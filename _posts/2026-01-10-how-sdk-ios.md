---
title: How to build an ios SDK
date: 2026-01-10
categories: [tech, programming, swift]
tags: [softskill, ios, swift, sdk]
---

# How to build an iOS SDK

## The Start

When I was hired by a consulting company to work for the largest bank in Latin America — Itaú — I wasn’t expecting to create an SDK. I thought I’d be maintaining their existing banking app.

However, my challenge turned out to be quite unique: building a Banking-as-a-Service (BaaS) SDK.
This SDK would provide features for partner banks, enabling secure integration with Itaú’s systems.
Open Finance, security standards, and SDK architecture were all new topics to me at that time.

My first step was to research mobile SDKs to define a solid structure and security model.
Over the past four years, I’ve created four SDKs — and one of them has survived the test of time and priorities within a large organization.

That SDK allows partners to authenticate users and access the bank’s backend systems.
It supports multiple authentication challenges, such as FIDO, biometrics, and more. Once the user successfully completes the challenges, the SDK returns an authorization code, which partners then exchange for an access token.

This article is a summary of the main lessons I learned throughout the SDK development process.

## Architecture

Designing the architecture of an internal SDK is already complex.

Designing the architecture of an SDK that will be used by third parties outside your organization is two levels harder.

The biggest challenge is the unknown — you don’t know how (or where) others will use your SDK, or what level of experience they have.
That’s why one of the most important principles of SDK design is having a clear API.

Your public interface — the code your users will interact with — must be simple, intuitive, and easy to integrate. It should feel **plug-and-play**, minimizing the setup time for that crucial first successful authentication.

Another critical point: **avoid breaking changes at all costs**.
Engineers often warn against over-engineering, but when designing an SDK, thinking long-term is not optional — it’s essential.

Imagine if the Firebase SDK broke its public interface every week. It would be chaos, right?

To achieve flexibility and long-term stability, I designed an event-driven (callback?) architecture. This model provided extensibility, simplicity, and backward compatibility.

The SDK’s structure was based on three main events:

- onSuccess(code): The SDK behaved as expected. The user completed all challenges, and here’s the authorization code.

- onFailed(error): Something went wrong. Here’s the error.

- onDismissed(): The user closed the SDK, denied a permission, or canceled a flow.

This structure allowed us to add new events or parameters later without breaking existing implementations. 

~~~swift 
public class AuthSDKAuthorizationCodeFlow {
    static func startAuthorization(
        requestURI,
        onAuthorizationSuccess: (code: String) -> Void,
        onFailed: (error: Error) -> Void,
        onDismissed: () -> Void
    )
}


AuthSDKAuthorizationCodeFlow.startAuthorization(requestURI) { code in

}, onFailed: { error in 

}, onDismissed: {

}

~~~

The SDK supported multiple authentication flows, each handled by a separate class.

Benefits of This Architecture

- Extensibility: New flows or events could be added seamlessly.

- Cohesion: The same architecture could be applied to both Android and iOS.

- Clarity: A simple and easy-to-read API.

- Plug-and-Play: Minimal setup required.

Since this SDK was also developed for Android, cohesion between platforms became a key design goal.

## Cohesion

This property can be translated to **shared knowledge**. That is, the ability to use the experience from one platform into another one. If a developer used the SDK in Android and there is an iOS developer with an issue, the first developer could be able to help the iOS Engineer as the API are close enough that they can exchange information.

Even our error codes and error object were very similar. This property made all the difference in the world as the SDK grows. With this, debugging was made easier, more people could undestand the SDK. So the architecture showed above work for both platforms.

## Error handling

Debugging and finding errors can be a source of much problem in an SDK. For an start think about analytics: Your SDK runs inside another app — possibly in another country — where data privacy laws differ. What can and cannot be collected? What data belongs to your partner? What is essential for your SDK to function?

These discussions can get complex quickly, so I started with one simple goal: **define a clear error API**.

~~~swift 
public protocol AuthSDKError: Error, LocalizedERror {
    var code: String { get }   
    var flowId: String { get }
    var installationID: { get }
    var sdkVersion: { get }
}

~~~

This protocol defines only what’s necessary to identify an error:

- code: A unique identifier for the type of error.

- flowId: Like a correlation ID, used to trace a specific SDK session.

- installationId: Identifies the partner.

- sdkVersion: Ensures traceability across versions.

Each SDK domain defines its own errors in enums conforming to AuthSDKError:

~~~swift
public enum AuthError: AuthSDKError {

    case emptyRequestURI

}

~~~

These errors are returned to partners so they can debug issues or open a ticket when needed.

A good pattern is to categorize error codes by domain:

- 100–199 → Service errors

- 200–299 → Security errors

- 300–399 → Authentication errors

With consistent documentation, this makes it easy for anyone to pinpoint where the SDK failed — and how to fix it.

## Documentation

If there is something that is important everywhere in software is documentation. Good software need a good documentation. It does not need to be complex or big, just to exist go straight to the point and have a nice index. Sadly, in most projects there is no such concern. 

In the previous sections I talked about clear architecture, simple code and defining a good error handling structure. All those things simplify a lot the process of writing documentation. If you have only a few lines of public interface, well defined errors, then you already have an easy documentation.

One advide that I can give here is this: think like you need to explain the software to someone like a Product Manager, a business stakeholder... Someone with litle technical background. That should be your goal, not to write a documentation for everyone, but to write a documentation that everyone can read and understand what that software does.

Be very careful with the index of your documentation. That should be an easy look up, something to find the important topics: how to setup, in case of X error... what to do?, what security features the sdk has?. Every time that someone opens a ticket to your team with a doubt,  sugestion or error consider adding that to the documentation or the index. Documenation is a live thing, it should be updated based on the client doubts/problems and natural growth of the software.

## Security

In a bank environment security is always the priority. If some application is not secure, it will not go to production. Because of that, the treat model of the SDK was created to prevent malicious inverventation in it`s code or requests:

- Obfuscation.
- App Attest/Integrity checks.
- Request Assertions & Cryptography.

### Obfuscation

Even though iOS apps are compiled, reverse engineering is still possible. Obfuscation helps by transforming readable code into something nearly impossible to interpret or modify.

### App Attest / Integrity Checks

Apple’s and Google’s integrity services verify the device and OS for signs of tampering or malicious code injection. They analyze the environment and confirm whether it’s safe before allowing sensitive operations.

### Request Assertions & Cryptography

To prevent man-in-the-middle (MITM) attacks, we added an additional layer of cryptography on top of HTTPS.
Requests are encrypted and signed. The server decrypts and validates them, rejecting anything suspicious — preventing fake biometric or FIDO challenge responses.

## Observability

Finally, let’s talk about observability — something I briefly touched on earlier.

There’s no way around it: be extremely careful with what you collect.
Your SDK runs inside a host app that your company doesn’t own — possibly in another jurisdiction.
Collecting the wrong type of data can even be illegal.

Privacy must always be a top priority and explicitly defined in the contract between SDK provider and consumer.
Who processes the data? What data? For what purpose?

Key Guidelines

- Minimal Data Collection: Only collect what’s strictly necessary for your SDK to function.

- Transparency: Clearly state what data is collected and why.

- Opt-In Mechanisms: Let users choose whether to share analytics data.

- Anonymization: Ensure all collected data is anonymized.

Remember: logs are not analytics.
Logs are for debugging and should only contain non-sensitive technical details.
Never log user data like names, IDs, or documents.

## Conclusion

Developing an SDK was challenge and I learn a lot. Here I will sumarize my learnings:

- Clear API: Try to provide a simple and clear API that can be used in multiple platforms.
- Well defined errors: Define your errors with a good structure to make simple to identify problems.
- Security: Trust no one. Protect your code and your requests, create a treat model and ask for the help of your company security team.
- Observability: Transparency is key. Analytics with only what is necessary. Logging should not contain private information.
- Documentation: If you have all previous topics, you already has a easy to write and read documentation.