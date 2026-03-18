+++
title = 'The Feature Flag Trap'
date = 2026-03-18T09:00:00Z
description = 'Feature flags were sold as safety nets. They have become the opposite.'
+++

Feature flags start as liberation and end as incarceration. I have watched this pattern repeat across enough teams to stop treating it as an edge case.

The promise is seductive: ship code whenever, release whenever, roll back instantly. No more coupling deploys to releases. No more terrifying Friday afternoon pushes. The flag becomes a kill switch, a safety valve, a way to be brave about shipping and cowardly about consequences.

That part is real. It works. The problem is everything that comes after.

## The false economy

A team I worked with three years ago had twelve feature flags in production. This was considered modest. Each flag was clean, well-documented, temporary. The engineers were proud of their discipline.

Eighteen months later, they had forty-seven. The original twelve had not been removed. Some had been around so long that the engineers who created them had left. Nobody could confidently answer what would break if any single flag was deleted. The tests had grown to cover both paths for every flag, multiplying suite runtime and coverage gaps simultaneously.

This is the invisible cost that feature flag advocacy rarely mentions. Each flag does not just add a conditional branch. It doubles the cognitive load for every engineer who touches the code. It doubles the testing surface. It doubles the number of execution paths that could behave differently in production. And these costs compound non-linearly, because flags rarely exist in isolation. They interact. The new checkout flow only applies to users in certain regions with certain account types behind a certain percentage rollout with a certain cookie set. The flag is not a switch. It is a state space.

## The deletion myth

Every talk about feature flags includes a slide about cleanup. "Remove flags after launch," they say. "Set expiration dates. Audit regularly." This is the software engineering equivalent of telling people to eat less and exercise more. It is correct advice that almost nobody follows in practice.

The reasons are structural, not disciplinary. After a launch, the team moves to the next priority. The flag worked. The feature shipped. Removing the flag is a task that can only introduce risk, not value. There is no product requirement for flag deletion. There is no customer asking for it. There is no sprint ticket. And so the flag remains, accumulating dust and conditional logic like a permanent exhibit in a museum of good intentions.

I have seen flags outlive the features they guarded. The feature was removed entirely, but the flag persisted because someone was afraid to touch the surrounding code. The flag controlled nothing. It just sat there, a monument to caution, making every future reader wonder.

## The testing trap

Feature flags create a hidden testing burden that teams discover too late.

Without flags, testing is straightforward: you verify the code path that runs in production. With flags, you must verify both paths, or accept that half your code is unexercised. As flags accumulate, the matrix of possible states grows exponentially. Twelve independent flags create 4096 possible configurations. No team tests all of them. Most teams test a few representative paths and hope.

This is where the false sense of safety becomes dangerous. The flags exist to reduce risk. But an untested flag path in production is risk you do not know you are taking. The system appears to work because the dominant path is tested. The alternate path, the rollback path, the path that runs for that one customer with the unusual configuration, has never been executed in a controlled environment. It will fail at 2 AM on a Tuesday, and the on-call engineer will spend hours tracing a code path that nobody expected to run.

## The rollback illusion

The flag-as-rollback argument is the one that sounds most reasonable. If something goes wrong, you flip the switch and restore the old behavior. No deployment. No rollback. Instant recovery.

This sounds good in a slide deck. In practice, it assumes the old code path still works. Often it does not. Dependencies have moved. Data formats have changed. Other code has assumed the new behavior was the baseline. Flipping the flag does not restore a known-good state. It restores a state that was last tested weeks or months ago, running against a system that has evolved in its absence.

I have seen incidents caused by flag flips more often than I have seen flag flips save the day. The flag provides the comfort of control without the substance of safety.

## What actually works

The alternative to feature flags is not the opposite: big-bang deployments and fear-based shipping. It is a less glamorous set of practices that do not require slide-worthy branding.

Strong review and testing practices reduce the need for runtime kill switches. Small, incremental changes are easier to reason about and easier to reverse. Good monitoring and error budgets tell you when things are going wrong before you need to manually intervene. The discipline to keep deployments small and reversible is harder to sell than a tool, but it scales better.

When flags are genuinely needed for A/B testing or gradual rollouts, the scope should be narrow and the expiration should be enforced. A flag that controls a single dimension of behavior for a bounded time is manageable. A flag that controls everything is not a flag. It is a configuration language for your application, and you have just become its maintainer.

## The exit strategy

If you have feature flags in your codebase today, the question is not whether they are useful. Some of them probably are. The question is whether you can delete them.

If you cannot, that is not a discipline problem. It is a design problem. Code that cannot be removed is code that was never designed to be removed. The flag is not the problem. The problem is the system that made the flag necessary in the first place.

The safest feature flag is the one you delete. Everything else is just debt with better marketing.
