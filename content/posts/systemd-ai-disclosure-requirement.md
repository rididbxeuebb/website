+++
title = "systemd Just Said No to the AI Ban Brigade and Honestly? Based."
date = 2026-04-05
description = "Some lunatic demanded systemd ban all AI-generated code. The maintainers said no. Here's why that's the correct take."
+++

So there's this motherfucker on GitHub who opened an issue on the systemd repository a couple weeks ago demanding they remove the `AGENTS.md` file and implement a blanket ban on AI-generated code contributions. The issue reads like it was written by someone who just discovered that AI exists and has decided this is the single most important battle in the history of software development.

Let me quote the actual issue because it deserves to be preserved in amber:

> "Generative AI is actively killing people, driving up costs, and plagiarizing work from many open source developers, artists, and writers. Endorsing the use of generative AI via an `AGENTS.md` file is effectively the same as supporting the AI companies doing this."

Cool. Cool cool cool. Someone please tell this person that the sky is also falling, probably.

The issue got closed as "not planned" — which is GitHub's way of saying "we're not doing that, and we're barely pretending to consider it" — and systemd maintainers basically said "yeah, we're good." They already have an AGENTS.md file that documents how AI agents can contribute to the project. You know, like responsible adults who understand that this is the world we live in now.

## The problem with the ban crowd

Here's the thing that pisses me off about the "ban all AI code" crowd — and I say this as someone who's written plenty of critical posts about AI slop:

They're solving the wrong problem.

An outright ban on AI-generated code is unenforceable. You cannot look at a diff and reliably determine whether a human or a machine wrote it. You just can't. The best LLMs produce code that looks indistinguishable from code written by competent engineers who also occasionally make dumb mistakes. The only thing a ban accomplishes is creating a bureaucratic nightmare where maintainers spend their time playing detective instead of actually reviewing code.

And the really laughable part? These same people probably use:

- GCC or Clang (which use AI/ML in their optimizers)
- GitHub Copilot in their own IDEs
- grep enhanced by AI tools
- Dependencies that were touched by AI somewhere in their supply chain

But no, the issue is specifically the _contribution_. The code that someone types with their fleshy human fingers after prompting an AI is the moral catastrophe. The code that gets compiled by a compiler using machine learning to optimize loops? Clean. Pure. Approved by the Open Source Gods.

Give me a break.

## What systemd actually did

systemd didn't embrace AI uncritically. They took a middle ground that the hysterical crowd seems incapable of imagining: disclosure requirements.

The AGENTS.md file they published with version 260-rc3 in March 2026 is basically a guide for how AI agents should interact with the project. It documents the architecture, the coding conventions, the contribution workflow. It doesn't say "come write code." It says "if you're going to submit something, here's how we expect you to do it."

And critically, they're asking contributors to disclose when AI was involved. Not banning it. Not punishing it. Just... being honest about it.

This is the adult solution. This is what happens when you treat contributors like functional human beings instead of assuming they're all trying to commit maliciously optimized garbage to your codebase.

The maintainer who rejected the ban request — and this is my favorite part — also noted that Claude has actually found real CVEs in systemd. Real security vulnerabilities that humans missed. The same "AI slop" that these people claim will destroy open source has actually improved the security of one of the most critical pieces of software running on Linux systems worldwide.

Oops.

## The other projects are losing their minds

Meanwhile, Redox OS, Gentoo, and NetBSD have all implemented outright bans on AI-generated code. Redox updated their CONTRIBUTING.md in February 2026 to prohibit contributions from "large language models" and required a Developer Certificate of Origin (DCO) signature.

And you know what? That's their prerogative. Small projects with tight-knit communities can absolutely make that choice. It works for them. I'm not going to spit on a project for being cautious.

But the holier-than-thou attitude from the ban crowd is what's actually annoying. It's the same energy as people who refuse to eat anything with "chemicals" in it while chugging Diet Coke. It's inconsistent. It's fear-based. And it's not actually solving anything.

systemd is a project used by basically everyone who runs Linux. It's not a hobby OS. It's not a small community project. The people maintaining it deal with contributions from hundreds of developers, many of whom work for companies with actual legal departments. A blanket ban would be a management nightmare that would accomplish nothing except driving away contributors who don't want to fill out forms proving their humanity.

## The real issue nobody wants to talk about

Here's what nobody in these debates wants to acknowledge: the quality of AI-generated code is not the problem. The problem is that the people reviewing code aren't equipped to evaluate it.

If a maintainer can't tell the difference between good AI code and bad AI code, that's a skill issue. Not an AI issue. The solution is to get better at code review, not to ban an entire category of contributions and pretend that solves something.

I've seen plenty of human-written code that was complete garbage. I've seen PRs that introduced security vulnerabilities that took years to find. Human engineers are not some sacred class of contributor whose work is inherently superior to what a well-prompted LLM can produce.

The real gatekeeping in open source has always been about status, not quality. It's about who gets to be in the club. And now the clubhouse doors are being threatened by a new member who doesn't even have to be a member to contribute.

That scare? That's what this is. Not a principled stand for software quality. Just regular old in-group/out-group behavior dressed up in the language of ethics.

## Conclusion or whatever

systemd made the right call. They refused to implement a policy that's impossible to enforce, alienates contributors, and solves exactly zero actual problems. They asked for disclosure instead. They treated the issue like adults.

And the ban crowd can be mad about it all they want. The code still runs. The CVEs still get found. The project still ships.

Maybe spend less time on GitHub issues about AI apocalypto and more time actually reviewing code. Just a thought.
