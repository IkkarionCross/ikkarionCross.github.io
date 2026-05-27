---
title: Interview with the Software Engineer
date: 2026-05-26
categories: [behavior, interview, mobile]
tags: [softskill, interview, recruiter]
---


# Interview with the Software Engineer

For the past 10 years, I've been interviewing people who want a job in IT. This much experience has brought me to a point where I have my own process that I believe works and can get good candidates for the job. I based my process on self-awareness and recognition of the limits of a candidate's knowledge. I decided to share it and make some clarifications about it too.

# My problem with the standard interview process

Anyone with an IT career or in related areas has heard about the Big Tech way of interviewing: a long process, focused on algorithms and data structures (ADS) that tests candidates who are very skilled at solving those problems quickly.

The thing is: no matter how much I study ADS, I can't stop thinking that this is just remembering a past problem that I solved again and again, until I have it memorized — always solving the problem in the same way or using variations of it.

Facing a problem they'd never seen before, most candidates would struggle — not because they lack skill, but because the test rewards pattern recognition over actual reasoning. Identifying the category of the problem and searching for a solution in that category from memory is not real-life software engineering.

This tests the memory of a candidate, because it's really hard to face a problem like those on a daily basis. And because it's not normal to find a difficult problem, there is no way to be ready when one of those appears.

Like all problems that we will encounter in this career, we should be ready to do two things:
- Research;
- Know what you don't know;

Now, the second one is more complicated. How do we tap into the unknown? How do we deal with things that are not familiar to us? That's my goal with my process. I think good engineers are those who know what they don't know.

## Everything is a trade-off

The first law of software architecture states "Everything is a trade-off", but if everything in software has pros and cons, we cannot always have the best of both. What happens? Does everyone just go mad about deciding something? No! We can understand *why* something is a trade-off, and to know this, we should also know both options that we are comparing.

But, but... Are you saying that we need to have a deep knowledge of the options? No, of course not! We need to have a deep understanding first of what we know as a software engineer/architect. In other words, we need to know ourselves — how far our knowledge of something goes. We should keep adding more and more knowledge of many different architectures, components, diagrams, methodologies, algorithms and so on... This is what will make the difference when deciding about something.

There is no need to memorize everything. We need to know some concepts just enough to know of their existence and be prepared to go deeper when needed.

## Tapping into the unknown

> Yes, I did a lot of research about the sentence at the beginning of this section to write it. All references are at the end of the article

> Know what we don't know

That expression is very old in different philosophical traditions. It is present in Asia, Africa and Europe. In ancient texts — sometimes fragments of scribbles in Egypt, philosophers in Athens and philosophical concepts in China. Its meaning is very clear: to know the limits of your knowledge and acknowledge that there are things that you don't know and even things that you can't know. With this, you know yourself and by knowing your limits you don't need to pretend to know something that you don't. This gives you confidence to say: I don't know.

Software/Hardware is one of the careers that have the most changes in a small amount of time, so you need to be ready to go deeper in a technology, read books, articles and try something different from time to time. All professions have their pros and cons... What do you think is ours? Ours is constant learning, always keeping up to date on different technologies and ways of working.

Being aware of your own ignorance is gold. That's why my favorite philosopher is Socrates, and his most famous sentence is:

> All I know is that I know nothing

This puts you in a state where you are always learning if you keep your mind open and remain aware of the limits of your knowledge. Our field of work is a field of limits; we are always pushing the limits of what we know within a given domain or set of business rules. For example, imagine being given a task to create software for taxes. In many countries this is insanely complex. How can you, with no prior knowledge of how the financial system of that country works, build that system? Can you give an estimate on your contract?

Pretending to know is the source of poor estimates which lead to poor decisions which lead to technical debt, bugs and software that is difficult to maintain.

That's why in many texts across countries, continents and different philosophical traditions, the knowledge boundary is the most important thing to map.

Why am I taking too much space to talk about this? Because sometimes what I most want to hear in an interview is: I don't know. When a candidate says this, I know that this person has some character and knows their gaps. The first step to close a gap is to know of its existence; the second one is to demonstrate that they want that gap filled.

# Interview process

The interview process should assess the candidate's ability to reason about a problem, discuss trade-offs, and show deep technical knowledge of the operating system, concurrency, memory management, and large-scale projects. My process of interviewing tests a candidate in three steps:

- Initial conversation

- Live coding → Assess what the candidate knows.

- System Design → Assess what the candidate thinks they know or pretends to know. Check the limits of their knowledge.

Let's go deeper in each one. System Design will go into the next part of this article.


## Initial conversation

This is where I, or another person in the process, get to know the candidate — asking about past jobs, projects, challenges and technologies.

Depending on the company, this may be done by an HR person or a tech recruiter. It really doesn't matter, but this step is very useful to check if the candidate meets the requirements of the job. Technical steps are costly; they involve getting senior people together, at least two to four and a manager (the hiring one).

Whenever I must do this step, I usually start by making the candidate comfortable, letting them know that I will not be giving them a problem to work on — this is just a conversation. Then I ask some questions to start the conversation:

- Tell me about *three* projects that you participated in that you are really proud of.

Asking for three specifically keeps the conversation focused and controls the time. I like to keep this first interview between 45 min and 1 hour. Imagine if you had to interview someone with 10 years of experience and they started to talk about all projects and companies. That would not be a very productive interview.

While the candidate is speaking, I take notes on what to ask next. I pay attention to:

- Tech stack that was mentioned
- Architectures
- Design decisions
- If testing was mentioned

From those notes, I choose one or two projects to go deeper and ask more questions about the structure and architecture. I check what they know about how the infrastructure was set up and how the team communicated.

After those more tech-related questions, I move to more behavioral ones, like:

- Tell me about a time when you had to make a presentation or convince a team/colleague/manager/stakeholder about a decision or technical evaluation that you made.

Generally speaking, I try to stay within the dynamics of a team and its processes, like agile techniques, communication, documentation and escalation decisions. Usually what I look for is this:

- How does the candidate ask questions and reason about decisions?
- What types of problems did they solve? More technical than communication or the inverse?
- What technologies and experiences make this candidate a good fit for the job?

I don't always do this step myself, but over the years, because I was already involved in hiring, many people asked me to handle it.

## Live Coding

Now it's time to give the candidate something to work on. The focus here is to check the candidate's knowledge at the level of what the candidate will do daily. This is the knowledge that the candidate must be comfortable showing. Here, I try to keep the challenges at the seniority level we are looking for. All challenges follow the same structure: a code sample is provided and the candidate should find the problems and fix them. Like in a code review.

The challenges should be small enough that the candidate can solve them in around 30 minutes, and we should have 15 minutes to discuss the solution and ask questions about it.

The model of the challenge is like the one below:

~~~Swift

import UIKit

protocol ImageCacheDelegate {
    func imageCache(_ cache: ImageCache, didLoad image: UIImage, for url: String)
    func imageCache(_ cache: ImageCache, didFail url: String, error: Error)
}

class ImageCache {

    var delegate: ImageCacheDelegate?

    private var store = [String: UIImage]()
    private var inFlight = Set<String>()

    func image(for url: String) -> UIImage? {
        return store[url]
    }

    func load(url: String) {
        guard !inFlight.contains(url) else { return }
        inFlight.insert(url)

        guard let requestURL = URL(string: url) else { return }

        URLSession.shared.dataTask(with: requestURL) { data, _, error in
            self.inFlight.remove(url)

            if let error = error {
                self.delegate?.imageCache(self, didFail: url, error: error)
                return
            }

            guard let data = data, let image = UIImage(data: data) else { return }
            self.store[url] = image
            self.delegate?.imageCache(self, didLoad: image, for: url)
        }.resume()
    }

    func clearAll() {
        store.removeAll()
        inFlight.removeAll()
    }
}

class FeedViewController: UIViewController, ImageCacheDelegate {

    @IBOutlet weak var imageView: UIImageView!
    @IBOutlet weak var loadingIndicator: UIActivityIndicatorView!

    private let cache = ImageCache()
    private var refreshTimer: Timer?
    var urls: [String] = []

    override func viewDidLoad() {
        super.viewDidLoad()
        cache.delegate = self
        startRefreshTimer()
    }

    private func startRefreshTimer() {
        refreshTimer = Timer.scheduledTimer(withTimeInterval: 60, repeats: true) { _ in
            self.reloadAll()
        }
    }

    private func reloadAll() {
        for url in urls {
            cache.load(url: url)
        }
    }

    func imageCache(_ cache: ImageCache, didLoad image: UIImage, for url: String) {
        loadingIndicator.stopAnimating()
        imageView.image = image
    }

    func imageCache(_ cache: ImageCache, didFail url: String, error: Error) {
        loadingIndicator.stopAnimating()
        print("Failed: \(url) — \(error)")
    }

    deinit {
        refreshTimer?.invalidate()
    }
}

~~~

What I ask of the candidate is to comment every error that was found and come up with a solution. The solution can be in Swift code, pseudo-code and even in plain text. What matters most is whether the solution is correct!

Of course, the challenge here is just an example and was AI-generated just to explain what I do. I have a library of challenges of different complexities.

~~~Swift

import UIKit

// BUG 1: Protocol not constrained to AnyObject.
// Without it, `delegate` cannot be declared `weak`, forcing a strong reference.
// Fix: add AnyObject constraint.
protocol ImageCacheDelegate: AnyObject {
    func imageCache(_ cache: ImageCache, didLoad image: UIImage, for url: String)
    func imageCache(_ cache: ImageCache, didFail url: String, error: Error)
}

enum ImageCacheError: Error {
    case invalidURL
}

class ImageCache {

    // BUG 2: `delegate` is strong.
    // FeedViewController owns `cache` strongly; `cache.delegate = self` closes a
    // retain cycle: FeedViewController → cache → delegate → FeedViewController.
    // deinit is never called, the timer is never invalidated, memory leaks.
    // Fix: weak + AnyObject constraint above.
    weak var delegate: ImageCacheDelegate?

    // BUG 3: `store` and `inFlight` are accessed from both the calling thread
    // (usually main) and URLSession completion handlers (background queue).
    // This is a data race — undefined behavior under Swift concurrency rules.
    // Fix: serialise all access through a dedicated queue.
    private var store = [String: UIImage]()
    private var inFlight = Set<String>()
    private let queue = DispatchQueue(label: "com.app.ImageCache", attributes: .concurrent)

    func image(for url: String) -> UIImage? {
        // Reads can run concurrently, writes need a barrier (see `load` below).
        return queue.sync { store[url] }
    }

    func load(url: String) {
        queue.async(flags: .barrier) {
            guard !self.inFlight.contains(url) else { return }
            self.inFlight.insert(url)

            // BUG 4: Invalid URL silently exits, leaving `url` stuck in `inFlight`
            // forever. Subsequent calls for the same URL are silently dropped.
            // Fix: remove from inFlight and notify the delegate.
            guard let requestURL = URL(string: url) else {
                self.inFlight.remove(url)
                DispatchQueue.main.async {
                    self.delegate?.imageCache(self, didFail: url, error: ImageCacheError.invalidURL)
                }
                return
            }

            URLSession.shared.dataTask(with: requestURL) { data, _, error in
                // BUG 5: Delegate callbacks are fired on URLSession's background queue.
                // UIKit mutations (stopAnimating, imageView.image) from a background
                // thread are undefined behavior and cause visual glitches or crashes.
                // Fix: dispatch delegate calls to main queue.
                self.queue.async(flags: .barrier) {
                    self.inFlight.remove(url)

                    if let error = error {
                        DispatchQueue.main.async {
                            self.delegate?.imageCache(self, didFail: url, error: error)
                        }
                        return
                    }

                    guard let data = data, let image = UIImage(data: data) else { return }
                    self.store[url] = image
                    DispatchQueue.main.async {
                        self.delegate?.imageCache(self, didLoad: image, for: url)
                    }
                }
            }.resume()
        }
    }

    // BUG 3 (same): clearAll mutates both collections without synchronisation.
    func clearAll() {
        queue.async(flags: .barrier) {
            self.store.removeAll()
            self.inFlight.removeAll()
        }
    }
}

class FeedViewController: UIViewController, ImageCacheDelegate {

    @IBOutlet weak var imageView: UIImageView!
    @IBOutlet weak var loadingIndicator: UIActivityIndicatorView!

    private let cache = ImageCache()
    private var refreshTimer: Timer?

    // BUG 6: `urls` is public. Exposing mutable state externally makes
    // thread-safety guarantees impossible to uphold. Fix: private(set).
    private(set) var urls: [String] = []

    override func viewDidLoad() {
        super.viewDidLoad()
        cache.delegate = self
        startRefreshTimer()
    }

    private func startRefreshTimer() {
        // BUG 7: Timer closure captures `self` strongly.
        // RunLoop retains the Timer; the closure retains FeedViewController.
        // deinit is never reached → timer never invalidated → permanent leak.
        // Fix: [weak self] capture list.
        refreshTimer = Timer.scheduledTimer(withTimeInterval: 60, repeats: true) { [weak self] _ in
            self?.reloadAll()
        }
    }

    private func reloadAll() {
        for url in urls { cache.load(url: url) }
    }

    func imageCache(_ cache: ImageCache, didLoad image: UIImage, for url: String) {
        loadingIndicator.stopAnimating()
        imageView.image = image
    }

    func imageCache(_ cache: ImageCache, didFail url: String, error: Error) {
        loadingIndicator.stopAnimating()
        print("Failed: \(url) — \(error)")
    }

    deinit {
        refreshTimer?.invalidate()
    }
}

~~~

I usually give senior candidates challenges that contain: 2 junior, 1 to 2 mid-level and 2 to 3 senior problems. This structure makes each challenge have up to 10 problems that are mapped and known, so the interviewer can evaluate which problems the candidate solves first and how they prioritize work. There are, of course, some challenges that contain only 3 problems of one seniority — that's to change the dynamics a little to a more thought-heavy or implementation-heavy challenge. The criterion is to choose a challenge that matches the candidate's abilities and the requirements of the job.

In this step, the two most important things to evaluate are:

- How the candidate thinks: do they prioritize tasks and communicate clearly?

- Knowledge: code architecture and problem solving.

Of course, you can set up your own Score Card with the things that are most important to your company. In this article, I won't go into creating a Score Card.

### How the candidate thinks

This is where I judge how the candidate faces the problem. I try to answer these questions:

- Did they think about how to prioritize tasks?
    - Did they read all the code before starting to solve or comment on the problems?
    - Did they solve bigger problems first or small ones?

- Did they ask clarifying questions about some problems?
- Did they try to really understand the code before jumping into the problem?

In this section, I try to map these behaviors onto what their day-to-day work would look like. Which tasks will they tackle first? How do they divide work? It's very important because I can start to create a mind map of the personality of this person and what it will be like talking to them daily.

### Knowledge

This is more straightforward. Here, I try to understand the limits of the candidate's knowledge:

- Did the candidate solve the problems correctly?
- Did the candidate give more than one option to solve a problem?
- Did the candidate find all senior/junior/mid-level problems? Which ones did they find more of?
- How do they behave when facing a subjective problem? Like generics, abstraction or a design pattern.
- Did the candidate explain their thoughts on a deeper level or just scratch the surface?

With those questions, I'm trying to learn from the candidate. I want to know if the candidate can articulate their thinking clearly.

### Follow-ups

Now, I make the life of the candidate even harder by asking some questions in the format:

- And if we want to do X? How would you change this code?
- If this were a module inside a global app used by millions of people, what would you change?

I always say that there is no need to actually change the code — it's just a mental exercise to know if they really understood the problem and the limits of their knowledge.

### Ending the interview

After I spend 45 minutes making the life of the candidate more difficult, it's time to change the game. Now the candidate has 10–15 minutes to ask questions about the company and to receive honest answers. I never skip this step — it's another opportunity to see how the candidate thinks and what is important to them.

For example, if the candidate asks "Do you do a lot of overtime?" This question indicates that they are worried about working overtime. This is fine — no one likes to work like that all the time. But it's honest to acknowledge that some overtime is unavoidable during crunch periods. If you are a candidate reading this, this is one great question to ask.

I'm one of those who value work-life balance. I hate staying past working hours, so I do what I can to avoid that.

And what if the candidate asks "Can you tell me how the deployment process works? Do you have automated tests?" — this clearly shows that they have a concern about quality.


# All I know is that I know nothing

There are many challenges in software engineering. No one needs to know every possible way of solving a problem or memorizing an answer. What matters most is keeping an open mind, read books, watch videos and try different ways of learning. This long process builds not a pool of knowledge, but an ocean. You can accumulate that knowledge even without actively using it — it stays with you, and some of it will remain fresh. This is the actual goal of constant studying: retain some of the knowledge for your brain to connect the dots when a problem arises. 

With each book read and each video watched, at this slow, steady pace the limits of one's knowledge will begin to become clearer and confidence will appear. Even if you deal with impostor syndrome, confidence will emerge as you accept that there is nothing to fear from lack of knowledge. I had a professor who said "the difference between you and me is the pile of books that I read".

In the next article, I'll cover the system design part of the interview in more depth.