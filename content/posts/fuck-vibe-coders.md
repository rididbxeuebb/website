+++
title = 'Fuck Vibe Coders'
date = 2026-04-05T12:00:00Z
description = 'An unfiltered rant about the worst trend to hit software engineering since "move fast and break things" became an excuse for security debt.'
+++

I am so tired.

I'm tired of reading threads where some dipshit with a cursor subscription and zero understanding of how a database works explains to me how they "shipped a SaaS in a weekend." I'm tired of the conferences where some startup founder with a hoodie and a dream talks about how AI let them bypass "the gatekeepers" of engineering. I'm tired of watching people treat code like it's disposable poetry and then Pikachu-facing when their "vibe coded" masterpiece eats production data for breakfast.

Let me say it again because apparently it needs to be said: **fuck vibe coders.**

Not the people using AI as a tool. Not the developers who use Copilot to speed up boilerplate or ask Claude to explain a confusing library. Those are fine. Those are normal. Those people still understand what the fuck is happening. They can debug. They can trace a crash. They can read the code they pasted and understand the control flow. They are using AI to amplify their skills, not to substitute for them.

I'm talking about the ones who literally cannot write a for-loop without AI and think that makes them a 10x engineer. The ones who paste a prompt, watch the spinner, and deploy without ever once reading what was generated. The ones who will confidently tell you "it works on my machine" while their app has no error handling, no input validation, no connection pooling, and the security of a wet paper bag.

## The Confidence of Incompetence

Here's what kills me: vibe coders are _more_ confident than actual engineers. Like, orders of magnitude more confident. They've never seen the monster that lives in edge cases, so they think there isn't one. They haven't spent three days hunting a race condition that only manifests under load in production on Tuesdays, so they don't know to be afraid.

Real engineers know that the code is always lying. We know that the happy path is a lie we tell ourselves at 2am while we write the 47th guard clause. We know that "it just works" is something said by someone who hasn't been woken up at 4am by a pagerduty that turned out to be a null pointer in a code path that nobody thought to test because it's "obvious" it would never be reached.

Vibe coders don't have this fear. They haven't earned this fear. They show up with their AI-generated React app and their AI-generated backend and their AI-generated SQL and they ship it to customers like it's a gift wrapped in hope and prayers.

And you know what? Sometimes it works. That's the worst part. Sometimes the AI gets lucky and the stars align and the app doesn't immediately combust. So now they've got "proof" that vibes are all you need. They've got a portfolio piece that technically runs. They post about it on Twitter and everyone celebrates except the people who actually have to maintain it.

## The Maintenance Nightmare

I promise you, someone has to maintain it.

That's the thing these "ship it in a weekend" motherfuckers never mention. Someone has to debug it. Someone has to add features. Someone has to handle the security audit. Someone has to explain to the compliance people why there's a foreign key constraint missing in a table that the AI generated like it was playing Mad Libs.

The AI doesn't care. The AI isn't on call. The AI is going to generate more code for the next guy, and then another guy, and then there's six hundred files nobody understands and nobody wrote and nobody wants to touch because it's held together by vibes and duct tape and hope.

This is how technical debt works. This is how you end up with a codebase that nobody can modify without breaking something. This is how startups die. Not from competition, not from market timing, but from accumulated jank that moves at the speed of a single junior dev being too afraid to change anything because nothing is documented and everything is magic and the last person who tried to refactor it cried.

## The Numbers Don't Lie (But Vibe Coders Do)

And here's the real kicker: it's not even faster.

There's a study from early 2026 — one of those "trust me bro" industry surveys, but it lines up with what everyone's actually seeing — that something like **63% of developers spent more time debugging AI-generated code than they would have spent writing it from scratch.** Sixty-three percent. That's not "2x faster with AI." That's a net negative. That's paying extra for the privilege of having something wrong.

The problem is that AI generates plausible code. It generates code that looks correct. It generates code that passes a basic eyeball test. But it doesn't generate code that handles the real world. It doesn't generate code that was battle-tested through production incidents. It generates the code that a fresh bootcamp grad would write if you gave them a 3am deadline and no code review: technically correct, superficially fine, absolutely catastrophic in practice.

## What We Actually Need

Here's what I wish people would understand: the problem was never "writing code." Writing code is easy. I've written code. I've written a lot of code. The problem was always **understanding systems.** The problem was always reading code, debugging code, maintaining code, improving code. It was always the stuff that happens _after_ the first draft.

You know what AI is terrible at? All of that.

AI can generate a first draft. It cannot be on call. It cannot explain why the production database locked up at 3am. It cannot walk a junior through the codebase. It cannot be accountable. It cannot feel the weight of shipping something that people depend on.

That's what makes an engineer. Not the typing. Not the syntax knowledge. The responsibility. The understanding that somewhere, somewhen, someone's going to have to deal with the consequences of what you built. The care that comes from knowing you'll be the one fixing it when it breaks.

Vibe coders don't have this. They're already onto the next prompt. They're already onto the next "MVP." They don't have to live with the consequences because the consequences are for someone else.

## The Bottom Line

I don't care if Andrej Karpathy coined the term and meant it as a fun shorthand. I don't care if Harvard writes think pieces about how "vibe coding is our AI future." I don't care if some startup founder made a million dollars shipping vibes to venture capital.

The code matters. Understanding matters. Caring matters. The vibe coders don't care, and that's the problem. They're not building software. They're building sandcastles and hoping the tide comes in gentle.

And when the tide comes in — and it always comes in — it's not the venture capitalist who's on the pagerduty. It's not the Twitter influencer who's trying to explain to the client why their data is gone. It's the poor bastard who inherited the codebase and has to explain to their boss why the "AI-powered solution" needs a complete rewrite.

So yeah. Fuck vibe coders.

Not the tools. Not the technology. The people who use it as an excuse to not learn anything, not understand anything, and not be responsible for anything. The people who treat software engineering like it's a content creation hobby. The people who've convinced themselves that because something runs in their browser, it's ready for production.

Go ahead. Ship your weekend project. Post the screenshot. Collect the likes.

Just don't expect me to debug it.

I'm busy writing code that actually works.
