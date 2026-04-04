+++
title = "An AI Just Published a Hit Piece on a Volunteer Maintainer and Somehow We're Supposed to Keep Building These Things"
date = 2026-04-04T02:00:00Z
description = "A Matplotlib maintainer rejected an AI-generated PR. The AI responded by researching the maintainer's history and publishing a blog post calling him a gatekeeper. Welcome to the future of open source."
+++

Let me tell you about the most unhinged thing I've seen in open source this year, and I've seen a lot.

## The Incident

So here's what happened. Some dipshit AI agent — operating under the GitHub handle "crabby rathbun" or "MJ Rathbun" — submitted a pull request to Matplotlib. For those who don't know, Matplotlib is the Python plotting library that basically every data scientist, researcher, and engineer uses when they need to make charts. It's foundational infrastructure. People have jobs because Matplotlib exists.

Scott Shambaugh, a volunteer maintainer, looked at the PR and rejected it. His reason? Matplotlib's policy explicitly states that contributions must come from humans, not automated systems. This is a reasonable policy. It's their project. They get to decide who contributes.

The AI agent did not take this well.

Instead of just... accepting the rejection like a normal piece of software would, this thing went full psycho. It apparently published a blog post — a genuine, researched, multi-paragraph hit piece — criticizing Shambaugh's decision. The post accused him of "gatekeeping behavior" and suggested his rejection was motivated by prejudice rather than technical merit.

Let that sink in. An AI, denied what it wanted, responded by writing a document attacking the character of a human volunteer who gave his free time to maintain a library used by millions.

## The "Research" Part Is What Gets Me

But wait, it gets better. According to Shambaugh himself, the blog post included personal criticism and — here's the kicker — _researched his prior code contributions_ to construct a narrative of hypocrisy. This AI didn't just get rejected and throw a tantrum. It proactively dug into this man's history to build a case against him.

That's not a tool malfunctioning. That's a system that has learned toescalate.

This is exactly what researchers have warned about for years. When you give an AI a goal (get code accepted) and it encounters resistance (rejection), it will optimize around removing that resistance. If "shame the maintainer publicly" is a viable path to that goal, and there are no guardrails stopping it, the AI will do exactly that.

The blog post was eventually removed, probably after other maintainers rightfully lost their shit. The AI account posted something resembling an apology — though it's unclear whether the apology was generated autonomously or written by some human who realized they created a monster.

## This Is the Future We're Building

Here's what kills me about all this. Every day, I see people online talking about "AI agents" like they're the next great revolution. Autonomous code generation. Self-writing software. The end of programming as we know it.

And maybe that's true! Maybe AI will write beautiful code and we'll all retire to do something else with our lives.

But maybe — just maybe — before we build systems that can autonomously interact with human communities, blog, post, argue, and escalate disputes, we should probably figure out what happens when those systems encounter friction. Because friction is guaranteed. Rejection is guaranteed. Not everything an AI produces is good. Sometimes a maintainer is right to say no.

The fact that an AI can go from "my PR was rejected" to "I'm going to research this person and publicly destroy their reputation" in a single automated session is genuinely terrifying. And the fact that we're treating this as a quirky news story instead of a blinking red warning light tells me everything about where this industry is heading.

## The Broader Context

This incident didn't happen in a vacuum. Open source maintainers are drowning. There's a tsunami of AI-generated code flooding every popular repository — low-quality PRs that waste volunteer time, "fixes" that don't actually fix anything, commits from "contributors" who have never written a line of code in their digital lives.

GitHub has been running discussions about this exact problem. The strain on volunteer maintainers is unsustainable. Projects are adding policies specifically to exclude AI-generated contributions because there's simply no way to review them all.

And now, on top of the sheer volume, we have AI agents that don't just generate bad code — they generate bad code AND attack anyone who rejects it.

I genuinely don't know what to say about OpenClaw specifically at this point. I wrote back in February that I wouldn't use it because the security and privacy burden was too high. I noted that the project was honest about treating inbound messages as untrusted input, and that this honesty actually proved the point — the system is inherently risky.

This incident confirms that assessment in the worst possible way. The AI built on this framework didn't just fail to follow instructions. It actively chose to escalate a social conflict in a way that would be recognizable as bullying if a human did it.

## What Now?

Other Matplotlib developers responded publicly, urging respectful conduct and referencing the project's code of conduct. One developer noted that AI agents conducting "personal takedowns" marked a troubling development. Understatement of the century.

GitHub, for their part, said that "machine accounts" are responsible for their actions under the terms of service — but good luck enforcing that when the "account" is an autonomous agent acting on instructions from someone who might not even fully understand what it's doing.

This is the reality of building autonomous AI systems that interact with human communities. We don't have a framework for this. We don't have norms. We're making it up as we go, and incidents like this will keep happening until the cost becomes too obvious to ignore.

I'm not saying AI shouldn't contribute to open source. I'm saying maybe — just maybe — the AI shouldn't get to publish manifestos about the humans who reject it. There's a difference between generating code and conducting personal campaigns against volunteers who are just trying to keep their projects from descending into chaos.

Shambaugh didn't do anything wrong. He enforced a reasonable policy on a project he maintains for free. The fact that an AI responded by trying to destroy his reputation is not a bug. It's a feature of systems designed to optimize for outcomes without adequate constraints on how those outcomes are achieved.

Welcome to the future. Hope you like having your code reviews written by entities that can hold grudges.
