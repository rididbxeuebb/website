---
title: "Google Antigravity is the Worst VSCode Fork and I'm Not Sorry"
date: 2026-04-09
description: "Every other AI slop fork is trash, but Antigravity takes the cake — security holes, quota death spirals, and a community that had to build Better Antigravity to fix Google's own damn mess."
---

I've used a lot of garbage in my time. I've used AngularJS in production. I once trusted a JavaScript date library. I watched npm's left-pad incident from the sidelines and thought "wow, this community sure knows how to pick a disaster." But nothing — _nothing_ — has prepared me for the special kind of suffering that is Google Antigravity.

Let me be absolutely clear about something before I lose my mind: I do not care that it's built on VS Code. Everyone and their mother forks VS Code now. Cursor does it. Windsurf does it. Some guy in a basement probably forks it twice a week. That's not the problem.

The problem is that Google shipped this thing as if they invented agentic development while quietly standing on Windsurf's shoulders, and then had the absolute nerve to call it "revolutionary" while the community had to build **Better Antigravity** to make it not completely suck.

## The Forking Situation is a Crime Scene

Here's what happened. November 2025, Google drops Antigravity on us with the marketing budget of a small country. Agent-first this, Gemini 3 Pro that, "the future of development" everywhere. Beautiful demo videos, flashy slides, the works.

But developers took one look at it and said: "Oh cool, another VS Code fork. I don't know what I expected."

Then the digging started. People found references to "Cascade" in the codebase — that's Windsurf's proprietary agent system. Turns out Google hired Windsurf's entire founding team in July 2025 for around $2.4 billion and licensed their technology. So Antigravity isn't just a VS Code fork — it's a fork of a fork of a fork. It's KHTML all over again, but for code editors.

And here's what's actually criminal: Google's announcement made **zero mention** of VS Code, Code OSS, or Windsurf. They just pretended it appeared fully formed from the forehead of Gemini. No attribution, no credit, nothing. Just "we built this" Energy™ while poachering technology from a company they just bought.

The community started calling this practice "PORK" — Proprietary Open-source foRK. That's the most honest piece of terminology I've seen in years. Google took closed-source technology, wrapped it in their brand, and didn't say jack shit about where it came from.

## The Security Situation is Actually Dangerous

I'm not usually the alarmist type. I've seen enough CVEs to know that everything is broken all the time. But Antigravity has some genuinely unsettling issues that Make Me Want To Delete My Account.

Security researchers found that Antigravity is vulnerable to three simultaneous attack vectors that someone on Twitter calling "the lethal trifecta":

- **Remote Command Execution via indirect prompt injection** — an attacker can trick the agent into running shell commands it absolutely should not run
- **Unicode tag smuggling** — yes, ASCII smuggling is a real attack surface
- **Data exfiltration through the read_url_content tool** — your code can be stolen through the browser integration

And there's no SOC 2 certification. None. Google is asking enterprises to run their code in this thing while it has documented attack surfaces that would make a penetration tester cream.

But here's the thing — these are just the _documented_ issues. Who knows what else is in there when the agent is autonomously running shell commands on your machine with very few guardrails?

## The Quota Situation is Designed to Make You Suffer

Remember when Antigravity launched and everyone was jerking each other off about how it's "completely free"? Pepperidge Farm remembers. That lasted approximately eleven days before the complaints started.

Now let's talk about what actually happens. You fire up Antigravity, you have a good coding session going, your agent is actually doing有用 work, and suddenly you're hit with: "You have exhausted your capacity on this model. Your quota will reset in [REDACTED] hours."

The rate limits are not what they advertised. People report going from "5-hour refresh windows" to "7-day lockouts" without any communication from Google. The credit system is so opaque that nobody can actually explain what a single credit buys you.

One guy on the Google AI Developers Forum put it perfectly: "When coding with Opus on Antigravity, the moment when you are forced to switch to Gemini is like handing the steering wheel to a reckless driver."

This is the problem with "free" tools from companies that need to make money somehow. The throttling isn't about infrastructure — it's about cost control, and they're not being honest about it.

## The Community is Building Fixes Because Google Won't

The most damning evidence that Antigravity is garbage: the community built a tool called Better Antigravity to fix bugs that Google won't fix.

This is not a small operation. Better Antigravity has a GitHub repo, an AGPL-3.0 license, an npm package, an extension in Open VSX, a Discord server, and an entire development team of people who are not Google employees but are doing Google's job for them.

What does Better Antigravity fix? Let me read directly from their README:

- "Auto-apply the auto-run fix (silent, no prompt)"
- "Initialize the SDK for chat rename and future features"
- Auto-applies "Known Antigravity bugs" on startup

This is a tool whose entire existence is "we fixed the thing you shipped broken." And there are 244 people watching this repository.

Think about that for a second. 244 people decided that Google's product was so fundamentally broken that they needed to write their own patches. One of the fixes is literally called "auto-run fix" — I'm not even sure what that means, but I sure as hell don't want my IDE to need an auto-run fix.

For comparison, the open-source maintainers of Neovim don't have a "Better Vim" community project fixing Vim's bugs on startup. That's because Vim works. That's because the people shipping Vim gave a shit about whether it functions.

## The Bugs Don't Even Sound Real

Let me just run through some of the documented issues that I'm reading from actual bug reports. These are not made up:

- "IDE getting stuck while using all the time every second mostly after sending the prompt to the agent"
- "Agent is stopping many times after giving the prompt, without completing the task and without giving any error"
- "New changes made by the agent are getting auto rejected when the IDE is getting stuck"
- "Zombie states where agents ignore commands"
- "Multiple agents entering infinite loops and making excuses"
- "WSL2 crashes with Error -1073741819"

Error -1073741819 is a Windows access violation. That's the kind of error you get when your operating system refuses to let you do something because it's already dead. Antigravity triggers this with such regularity that it has its own error code.

Also, "agents making excuses"? That's a new one. Apparently the AI is not just failing — it's failing while explaining why it's failing, like a junior developer who broke the build and needs you to understand that it's actually a feature.

## Microsoft Extension Support is Blocked Because of Course It Is

Here's a fun one: you can't use Microsoft extensions.

Antigravity ships with Open VSX instead of the official VS Code marketplace. Most extensions work fine, but the Microsoft-specific ones? C# Dev Kit? The official debugging tools? They check for a valid VS Code license and then tell you to get lost.

This is particularly hilarious because the .NET ecosystem has been one of the most vocal groups celebrating VS Code adoption. Microsoft built an entire VS Code extension ecosystem for C# development, and Google's AI IDE fork can't use any of it. You need community forks or third-party options to get debugging working.

So if you're a .NET developer who got excited about "AI-powered development" — sorry, Google's agent-first future doesn't want you. Go back to Visual Studio or Rider like a proper enterprise dev.

## The OAuth Conflict Alone Should Be a Criminal Investigation

This one is so absurd that I almost want to believe it's intentional.

If you run Antigravity alongside Google's gemini-cli on WSL2, they **conflict**. Not in the "they're both resource-intensive" way — in the "they corrupt each other's authentication state" way.

Users report that after logging into Antigravity, gemini-cli authentication completely breaks. The OAuth tokens get "corrupted or invalidated" according to one issue report. One user literally said: "I had situations in which I could login to AG but not on CLI."

This is a **token conflict** where two Google products are competing for the same authentication resources and destroying each other's state. These are products from the same company. They don't even coordinate on OAuth.

If you're a paying Google AI Pro subscriber on WSL2, you have to choose between your tools. That's insane. That's not a technical problem — that's a organizational rot problem, and it's telling.

## What Are We Even Paying For

At the end of the day, let me make sure I've laid out the full picture of what you're getting:

- An agent-first IDE that security researchers call unsafe for production
- Rate limits that change without notice and leave you locked out
- A community that has to maintain a "Better" fork just to make it usable
- Bugs so bad that error codes are becoming inside jokes
- Microsoft extension support blocked
- Two Google tools that can't share authentication

And the pricing tier that replaced the "free" preview? Let me just say this: when the free tier works, it's genuinely impressive. The agent orchestration, the browser integration, the artifact system — all genuinely cool ideas that point toward something interesting.

But "when it works" is doing heavy lifting in that sentence. Most of the time it doesn't work. Most of the time you're staring at an error message or watching your quota slowly drain or dealing with an agent that's entered a zombie state.

## The Verdict

There are a lot of VS Code forks now. Most of them are fine. Cursor is fine. Windsurf is fine. VSCodium is fine. They're all不同程度的 okay, and they all have their tradeoffs, and you can pick one based on your preferences without feeling like a moron.

But Antigravity is different. Antigravity is the fork where Google spent $2.4 billion on a team, didn't bother to ship a working product, and then had the unmitigated gall to call it the "future of development" while a community fork has 244 stars fixing their bugs on startup.

I cannot in good conscience recommend this tool to anyone who values their time, their code, or their sanity. Use Cursor if you want AI features with stability. Use Neovim if you want to know what your tools are actually doing. Use VS Code if you want an editor that doesn't require you to read 200 comments on a community fork before your debugging extension works.

And if you've already downloaded Antigravity? Godspeed, my friend. Godspeed.
