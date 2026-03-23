+++
title = "The Architecture You Have Is the Architecture You Deserve"
date = 2026-03-23T09:00:00Z
description = "Conway's Law is not a suggestion. It is the most honest description of how software actually gets built."
+++

A team I know spent eight months trying to break up their monolith. Every sprint, another service was extracted. Every service had an owner team. Every team had a roadmap. And somehow, despite all this work, the system ended up more coupled than when they started.

They blamed the architecture. They brought in consultants. They held architecture reviews. They drew diagrams on whiteboards and debated ADR formats.

None of it helped. The system kept growing in the shape of the organization that built it, which was exactly what Conway predicted in 1967.

## What Conway Actually Said

The law is usually quoted as: "Any organization that designs a system will produce a design whose structure is a copy of the organization's communication structure."

Most people stop there and conclude something like: if you want microservices, split your teams; if you want a monolith, keep them together. This is the naive reading. It treats Conway's Law as a lever.

The more careful reading is harder. Conway wasn't describing a mechanism you can tune. He was observing a tendency that emerges from how decisions actually get made. The shape of your system is not a function of the architecture you designed. It is a function of who talks to whom, who owns what, who gets credit for what, and who avoids risk by not making hard decisions.

These are not technical forces. They are political ones. And they are invisible in architecture reviews.

## The Misattribution Problem

Here is what I see constantly: engineers blaming the architecture for problems that are actually organizational problems in disguise.

"Every service calls every other service, we need to fix the coupling." But why does every service call every other service? Because teams that own different services are measured on feature delivery, not on interface hygiene. The boundary between "our service" and "their service" is a place where nobody wants to own a bug. The easiest solution is to make a call across the boundary rather than negotiate a contract. The architecture is not the problem. The incentive structure is the problem.

"We can't move fast because of our legacy code." But why does the legacy code persist? Because rewriting it would require coordinating with teams that benefit from the status quo. Because the person who wrote the code is gone and nobody wants to own the risk of changing it. Because "maintain existing functionality" is measurable but "reduce future coupling" is not. The architecture is not the problem. The coordination cost and incentive alignment are the problem.

"We need better documentation." But documentation doesn't get written because writing it requires someone to be accountable for its accuracy. Documentation that nobody owns becomes documentation that misleads. You cannot solve a social problem with a technical artifact.

The pattern is consistent: we diagnose what we can see (the code, the architecture, the diagram) and prescribe changes to what we can change (refactor, rewrite, restructure). But the forces that produced the current architecture remain intact, operating on the new architecture with the same logic.

## Why Reorganizations Don't Fix This

If Conway's Law simply said "org structure drives architecture," then changing org structure would fix architecture. But it doesn't work that way.

Reorganizations change reporting lines. They do not change who talks to whom out of habit, who avoids whose calls, which teams coordinate through emails versus which ones coordinate through hallway conversations. They do not change the budget flows that create dependencies, or the promotion criteria that reward local optimization.

I have watched teams reorganize three times in two years, each time told that the new structure would enable better architecture. The architecture did not change. Only the boxes and lines on the org chart changed. Eighteen months later, the system looked exactly as coupled as before, mirrored around the new team boundaries like water finding its level.

The reorganization did not fail. It succeeded at changing reporting lines. But reporting lines are not the same thing as communication structures. Changing one while the other remains constant produces no architectural change, only confusion about who is nominally responsible for what.

## What This Means for Technical Work

I am not arguing that architecture doesn't matter. I am arguing that you cannot engineer your way out of organizational problems.

If your system is a mess, the first question to ask is not "what should the architecture be?" The first question is "what are the forces that produced this architecture, and are those forces still operating?"

Often the answer is yes. The same incentive structures, the same coordination costs, the same risk-avoidance patterns. You refactor the code, and people refactor it back. You extract a service, and teams recreate the coupling through new integration points. You write an architecture decision record, and the next crisis produces an unrecorded decision that contradicts it.

This is not despair. It is clarity.

Once you understand that architecture is a lagging indicator of organizational dynamics, you can work differently. You can look for the places where the system is trying to tell you something about the organization. The services that have no clear owner are not poorly designed; they are symptoms of a power vacuum. The duplicated code across teams is not ignorance; it is a symptom of teams that do not talk to each other because there is no benefit to talking. The absence of documentation is not a documentation problem; it is an ownership and accountability problem.

The architecture shows you where the organization is strained. The code is honest in a way that org charts are not.

## An Alternative to Architecture Theater

Every engineering organization I have seen does architecture theater: reviews, diagrams, ADRs,RFC processes. These activities feel like architecture work. They produce artifacts that can be presented in meetings. They involve the right people in the right rooms.

Architecture theater does not change the system. It changes the documentation about the system.

The work that actually changes systems is harder to schedule. It is having the conversation between teams that nobody wants to have. It is establishing ownership in a way that creates accountability. It is making the incentive structure visible and then negotiating changes to it. It is sitting with the discomfort of saying "we cannot build that feature until we resolve this ownership question" in a meeting where everyone wants the feature shipped.

Conway's Law is a reminder that the code is not where the real work happens. The real work happens in the decisions that produce the code: who gets to decide, who gets consulted, who bears the cost of wrong decisions, who benefits from maintaining the status quo.

If you want to understand why your system looks the way it does, stop looking at the code. Look at the organization.

The architecture you have is the architecture you deserve. Not because you chose it, but because it reflects every decision made under every pressure that the people building the system were under. The only way to change the architecture is to change the conditions under which decisions get made.

That is not an engineering problem. But it is the engineering problem.
