---
title: Surgical Change
date: 2026-01-20
lang: en
categories: [engineering, tech, process]
tags: [softskill, process]
---

# The small change

There are situations where a small, seemingly harmless change can have a disproportionate impact on many people’s lives.

When, as developers, we start building systems that help in the diagnosis of health problems, control the injection of medicine into the body of someone, or manage the flight of 300 people, the consequences of our changes matter. We do not see the impact of our changes... That tiny refactor you made can potentially introduce a bug that drastically affects someone’s life.

In our day to day work we can`t notice any problem beyond a file not following the naming conventions or classes being tightly coupled. The beauty--or uglyness--of the code becomes our highest priority. We spend so much time deciding names and structure, that we miss some very important thing: engineering proccess.

Who am I doing this for—myself or the company’s client? Or the company?

Most of us don’t work on life-critical systems. Still, it’s important to be clear about who will be affected by the code we write. What is the value of refactoring a legacy system if it breaks in the process?

# Refactoring

I`m not against refactoring, every developer should refactor regularly.Code that doesn’t evolve grows stale until someone wants to rewrite everything because nothing works. The real problem, however, is not the system’s condition, but the people responsible for it: developers, managers and stakeholders. They failed to keep the heartbeat of the system healty.

Refactoring is the hearthbeat of a system. If you refactor it every day or or only once a year, both extremes are wrong. Frequent, needed refactors signal a system having a heart attack; annual overhauls mean the system is effectively dead.

Let's be clear: improve the system a little every day.  Small changes—improving names, removing unnecessary code, refactoring a switch into a Factory or Strategy—can be done alongside feature work or bug fixes. There is no need to tell the PM or your manager. If a refactor takes days or weeks, it’s not a refactor—it’s a rewrite. Parts of the system may be so poorly built that they require an almost complete change to work or to become understandable.

Changes to a system should develiver value, even refactors. Be careful not to break something already works. In my opinion, refactors need more caution than adding features.

Value needs to be the motive behind a refactor. Improving readbility, documentation, separating concerns and etc. But none of them is ego or "fun".Programmers sometimes refactor “just for fun.” It’s satisfying to turn messy code into something beautiful, but enjoyment cannot be the sole motive. Changes need context and purpose.

# Engineering Proccess

When changing software, always reflect on the "why". Who benefits? How you will measure success? How will you know the system improved?

Start with a clear goal and a way to measure it. For subjective values like readability, get other developers’ opinions so the change can be evaluated.

Treat this as refinement: describe what to improve, how it will affect the system, and how tests should be written. Testing is critical because it reveals related systems and integration points.

Next, tell your manager or a stakeholder about the planned refactor. Explain details, pros, and cons. Think about what could go wrong. Seek critique from someone who will challenge your ideas and improve them. Reviews increase a change’s value and can reveal when a change has no value.

This process—documenting the change, planning, asking for review, and iterating—is a feedback loop used by many agile and design methodologies. Don’t skip writing the specification for the change: a use case, a user story, a task, a feature description, or a bug report. Writing what needs to change and why is a **necessary process**.

While documenting, you’ll uncover flaws in your thinking and in the code that you hadn’t expected. That helps estimate the size and impact of the change and provides evidence to convince your manager that the refactor is worthwhile.

# Surgical Change

During refinement I aim for a surgical change: the modification that delivers the most value with the smallest impact on system behavior. Easier said than done, but that`s the goal.

My proccess for identifying that change usually starts after I have get rid of all my doubts about the business. I first ask the product manager clarifying questions, then examine the code.

When inspecting the code I follow four steps:
1. **Identify the start point of the change:** where should the change begin; which source file is the implementation entry;

2. **Identify dependencies:** note related systems, facades, libraries and internal or external dependencies that will be affected;

3. **Make a draf:** Experiment to see what breaks. This isn't full implementation. it’s testing to discover problems. If something breaks, mock or stub it and proceed. Which systems fail? Which tests need updates?

4. **Write tests that validates the idea:** create tests that capture the bug, feature, or refactor goal. They will fail at first; that’s expected.

The last two steps can be merged into a Test‑Driven Development workflow. These steps are guidelines—don’t be a slave to any single methodology; apply what works best for your context.

Software engineering is not an easy task. Developers write code and documentation every day; both need attention to prevent mistakes that can cause serious bugs. A repeatable process—a reliable way of working—helps prevent oversights and builds productive habits.



References: 

uncle bob talk that he says the rules are given to programmers.

Expecting professionalism

https://www.youtube.com/watch?v=HD0L3lQ9cms&pp=ugMICgJwdBABGAHKBQ51bmNsZSBib2IgdGFsaw%3D%3D

Brooks, mythical man-month -> surgical team
    "
    That is, instead of each member cutting away on the problem, one does the cutting and the others give him every support that will enhance his effectiveness and productivity. "

    Brooks Jr., Frederick P.. The Mythical Man-Month: Essays on Software Engineering (p. 47). (Function). Kindle Edition. 

Wikipedia list of bugs that killed people

https://en.wikipedia.org/wiki/List_of_software_bugs