+++
title = 'The Art of Deletion'
date = 2026-03-17T09:00:00Z
description = 'Why removing code is a skill worth developing, and how designing for deletion changes the way you write it.'
+++

The most useful line of code I wrote last year was one I deleted.

It was a service I had built two years earlier - a background worker that handled a workflow we no longer supported. The code was clean, well-tested, and professionally maintained. It was also completely dead. No one triggered it anymore. The data it processed had nowhere to go. But it still ran in production, still pulled dependencies, still needed to be updated when its libraries had security patches.

Deleting it felt like putting down a weight I had forgotten I was carrying.

Most developers I know are comfortable writing code. We practice it constantly. We study new patterns, learn frameworks, optimize our typing. But deletion - actually removing code from a living system - is a skill we rarely discuss, even though it may be more important.

## Code is a liability

The intuition that more code is better runs deep in our profession. Contribution graphs measure lines added. Job descriptions ask about code you have shipped. We celebrate features, not the absence of features.

But every line of code carries ongoing cost. It must be read and understood by the next person who touches the system. It must be updated when dependencies change. It must be secured, tested, and maintained. A line of code that does nothing useful still costs something every time the codebase is touched.

I first felt this clearly on a project where the test suite took forty minutes to run. We had tests for features that had been removed, assertions for behavior that no longer existed, and setup code for scenarios that could never occur. When we finally trimmed it down, the suite ran in twelve minutes. The coverage percentage went down, but the confidence went up. We were testing what mattered, not what once mattered.

That project taught me something I have carried forward: the goal is not to maximize code. The goal is to solve the problem with the smallest commitment possible.

## Delete-driven design

A useful frame I have come back to repeatedly is this: design your code as if deletion is a normal operation.

This changes how you structure things. When removal is hard - when deleting a feature requires touching fifteen files across four layers - that is a design problem wearing the clothes of architecture. If I cannot remove a piece of code without hunting through the codebase to find what else depends on it, I have built something that resists change in both directions. Adding is easy. Subtracting is painful.

The healthy version of this is different. Healthy code has clear boundaries. Removing a feature means removing its files and nothing else. The connections are explicit and localized. Dependencies point in one direction, and the cost of tracing them is low.

When I write code now, I ask myself: if this turns out to be a mistake, how hard is it to undo? If the feature gets cut next quarter, what does the deletion look like? The answer to that question tells me whether the boundaries are right.

This is not the same as writing throwaway code. It is about treating deletion as a first-class concern rather than an afterthought. The code does not need to be perfect. It needs to be removable.

## The hoarder mindset

It is easy to mock the idea of building features just in case, but most of us do it. We add abstraction layers because requirements might change. We add configuration options because a user might want them. We add entire services because the architecture diagram looks incomplete without them.

I have done this. I have built generic handlers for request types that never arrived. I have created utility libraries for imagined future needs. I have left dead code in place because removing it felt like admitting a mistake.

The real cost is not the lines themselves. It is the cognitive load. A codebase with dormant features is a codebase where every developer must wonder whether something is still used. It is a codebase where new engineers spend their first week asking about code paths that lead nowhere. It is a codebase where security updates must be applied to dependencies that serve no purpose.

That cost is invisible until you start subtracting. Then it becomes obvious how much noise was hiding the signal.

## Practical deletion

There are concrete ways to make deletion easier, and they are mostly boring:

Keep features in their own files. When everything lives in a shared module, nothing can be removed cleanly. When a feature has a home, it can leave one.

Avoid deep coupling. If module A imports B imports C imports D, and you want to remove D, you have a chain of cleanup ahead. Shallow, explicit dependencies make subtraction tractable.

Use feature flags as escape hatches, not permanent additions. A flag that is never turned off is just another piece of dead code waiting to be found.

Run dead code detection regularly. Most languages have tools that find unused exports. Use them. Review the results. Delete what is found.

None of this is glamorous. It does not show up on a contribution graph. But it keeps a codebase livable over time.

## What remains

I do not think every project should be ruthlessly trimmed. Some software genuinely needs the complexity it carries. Some domains require careful abstractions and forward thinking.

But I do think we undervalue subtraction. We celebrate shipping features but rarely celebrate removing them. We optimize for creation but not for the cleanup that makes creation sustainable.

The projects I enjoy working on most are the ones where deletion is easy. Where code has clear boundaries. Where removing a piece does not threaten the integrity of the whole. Those projects feel light not because they are simple, but because they do not carry unnecessary weight.

The most valuable skill in software is not writing code. It is knowing what the code is for, and having the discipline to keep only that.

When in doubt, delete. You can always add it back when you understand the problem better.
