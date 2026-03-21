+++
title = 'The Carefulness Deficit'
date = 2026-03-21T09:00:00Z
description = 'The real problem with software is not AI replacing programmers. It is that we stopped expecting programmers to be careful.'
+++

Last month I used an application that shall remain nameless. It crashed twice during a single form submission. The error message was a raw exception. The "success" state was indistinguishable from the loading state. After twenty minutes I gave up, sent an angry email, and switched to a competitor.

This was not a startup running on fumes. This was a company with hundreds of engineers and millions in funding. The code was not written by AI. It was written by people, carefully, in sprints, with code review, by developers who had been trained in computer science.

The problem is not that AI wrote the bad code. The problem is that we have been shipping bad code long before AI was a factor, and we have been pretending otherwise.

## A longer decline

The narrative right now is that AI is ruining software. AI generates code that looks right but is subtly broken. AI fills our codebases with bloat. AI makes developers lazy and uncritical.

There is truth in some of this. But it is not the whole truth.

I have been writing software professionally for long enough to remember when codebases were different. Not perfect. Not romantic. But different in one specific way: there was a higher bar for what shipped.

The bar was not type safety or test coverage, though those helped. The bar was something simpler and harder to quantify. It was care. People who wrote code also read it. They thought about the person who would debug it at 2 AM. They named things as if those names would outlive the moment.

That bar has been eroding for years. The erosion has nothing to do with AI. It has to do with how we started thinking about software development.

## The velocity trap

Somewhere along the way, the industry decided that the goal was to ship faster. Not ship better. Not ship things that last. Ship faster.

This is not a criticism of agile methodologies, which have done a lot of good. It is a criticism of what happened when velocity became the primary metric. When you measure velocity, you optimize for velocity. And you optimize for the easiest path to velocity, which is often: fewer constraints, fewer conversations, less time spent on things that do not show up in the changelog.

Care does not show up in the changelog. Care is invisible. It is naming a variable after the business concept instead of the implementation detail. It is writing an error message that actually helps. It is thinking about what happens when the network request fails, not just what happens when it succeeds. It is the work that makes the code readable by the next person who touches it.

None of this is measured. None of this is tracked. And when you optimize for what is measured, you get what you measure.

## What happened to the craftsman?

There used to be an idea that software development was a craft. Not a science, not an engineering discipline in the formal sense, but a craft. Something you got better at over years. Something where the details mattered because the details were the work.

This idea has not disappeared, but it has become unfashionable. We talk about "shipping" and "moving fast" and "10x developers". We do not talk about the craftsman's pride in a joint well-fitted. We do not talk about the plumber who leaves the job site clean.

The craftsman metaphor has weaknesses. It can become an excuse for elitism or slowdowns. But at its core it carried something important: an expectation that the person doing the work cared about the work.

I do not see that expectation as often now. I see engineers who are treated as input factories. I see code reviews that focus on whether the solution matches the ticket, not whether the solution is good. I see onboarding experiences that hand new developers a legacy codebase and a deadline and wish them luck.

## The AI amplifier

Here is what I think is actually happening with AI tools:

AI is an amplifier. It amplifies what already exists.

If you are careful, AI makes you more carefully productive. It generates a first draft that you then review and improve. It handles the boilerplate so you can focus on the interesting parts. You still own the work. You still understand the work. The AI is a power tool.

If you are careless, AI makes you carelessly productive. It generates a first draft that you then accept and ship. It handles the boilerplate so you do not have to think about the boilerplate. You do not own the work in any meaningful sense. The AI is a shortcut.

The problem is not the power tool. The problem is the attitude toward the work.

We have spent years cultivating carelessness as an acceptable mode of operation. We have shipped features with known bugs because the sprint ended. We have ignored technical debt because it does not show up in the quarterly review. We have prioritized shipping over building things that last.

AI did not create these problems. It revealed them.

## The visible rot

I used to think software was getting better. The tools were improving. The languages were maturing. The frameworks were becoming more opinionated about doing things the right way.

I am less sure now.

The applications I use daily are full of states that were clearly not designed. The error messages are still bad. The loading states are still ugly. The flows still break in predictable ways. The documentation is still wrong.

This is not a new observation. Developers have been complaining about software quality for years. But I think we have misdiagnosed the cause. We keep attributing the decline to the latest thing: first it was Agile, then it was microservices, then it was serverless, now it is AI.

The decline is more fundamental. It is the decline of care as an expectation.

## The return of standards

I do not have a solution that scales. I have a personal practice.

When I write code now, I ask a simple question before I consider it done: would I be comfortable explaining this code to someone I respect?

This is not the same as asking whether the tests pass or whether the linter is happy. It is asking whether I would be embarrassed to show someone the work. Whether the variable names are honest. Whether the error handling is real. Whether the code reflects that I actually thought about what it was supposed to do.

If the answer is no, I do not ship it. I make it right, or I argue for more time, or I find another way. This is not always possible. Sometimes the sprint ends and the code ships with a known imperfection. But the goal is to make that the exception, not the rule.

This is a low standard. It should not be controversial. And yet it is, because it asks for something that velocity-focused development does not value: the willingness to be slowed down by quality.

## What we owe

Software runs the world. It processes money, dispatches emergency services, carries private communications, and makes decisions that affect people's lives. This has been true for decades, but the scope has grown.

If we take the craft seriously, we owe something to the people who use what we build. Not perfection. Not zero bugs. Just the basic respect of having thought about the experience before shipping it. Of having considered what happens when things go wrong. Of having named things honestly and written error messages that help.

This is not a lot to ask. It is just care.

The carelessness deficit is the real problem. AI is just the latest excuse to ignore it.

If you write code, write it as if someone will have to maintain it. Because someone will. And that someone is probably future you, at 2 AM, trying to figure out what this is supposed to do.

Future you deserves better. So does everyone else.
