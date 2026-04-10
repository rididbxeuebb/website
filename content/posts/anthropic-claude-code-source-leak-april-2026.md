+++
title = "Anthropic Accidentally Open-Sourced Their Whole Codebase And Now They're Suing Everyone"
date = 2026-04-10T12:00:00Z
description = '512,000 lines of TypeScript exposed via a .map file. 44 hidden feature flags. A "Undercover Mode" that hides AI attribution. The company that just banned open-source tools just had their entire proprietary codebase leaked to the public. The irony is too perfect.'
+++

The universe has a sense of humor, and on March 31, 2026, it delivered a punchline so devastating that even the most hardened tech gossip addicts had to take a moment.

Five days after Anthropic pulled the plug on OpenCode's access to Claude — the same week they were sending legal documents to kill off third-party integrations — their own goddamn codebase showed up on npm. Not stolen. Not hacked. Just... published. By accident. To the public registry. Like a rookie leaving their front door wide open while screaming about how secure their house is.

Let me break down what happened, what's actually in that code, and why this might be the most consequential accidental open-sourcing in AI history.

## The Most Embarrassing Packaging Fail in Tech History

It started like any other Tuesday. Anthropic pushed version 2.1.88 of `@anthropic-ai/claude-code` to npm. Routine. Boring. And then it wasn't.

The package contained a 59.8 MB JavaScript source map file (`cli.js.map`) that should have never seen the light of day. Source maps are debugging artifacts — they bridge minified production code back to your original readable source. They're supposed to stay internal. They are not supposed to be shipped to the public npm registry.

But here's where the comedy of errors kicks in: Anthropic uses Bun as their build runtime. Bun generates source maps by default. And somewhere in the build pipeline, nobody added `*.map` to the `.npmignore` file. That's it. That's the entire security breach. Not a sophisticated attack. Not a malicious insider. Just a missing line in a config file.

The source map contained a reference to a zip archive sitting on Anthropic's own Cloudflare R2 storage bucket. That bucket was publicly accessible. And inside that zip? 1,906 TypeScript files. 512,000 lines of code. The entire client-side agent harness for Claude Code — every slash command, every tool definition, every internal API, every orchestration mechanism.

Security researcher Chaofan Shou found it first, posted about it on X, and by the time Anthropic pulled the package from npm around 08:00 UTC, the code had already been mirrored to GitHub, forked over 40,000 times, and had become the fastest repository in GitHub history to hit 50,000 stars.

They had three hours. Three hours to contain the biggest accidental disclosure in AI. They failed spectacularly.

## What the Code Actually Revealed

Now here's where it gets interesting. Once people started digging through the leaked code — and they did, oh boy did they — they found some genuinely wild shit.

**44 hidden feature flags.** Some of these are mundane. Some of them are straight up embarrassing. And some of them are raising serious ethical questions.

One flag called `ANTI_DISTILLATION_CC` activates a system that injects fake tool definitions into API requests. The idea is to poison the well for anyone trying to train models on Claude Code's behavior. Which, you know, fair enough — they're worried about competitors scraping their work. But the implementation? The leaked code shows exactly how it works, meaning competitors can now just... bypass it. Great job, team.

Then there's **KAIROS** — an unreleased "always-on daemon mode" that keeps Claude Code running in the background, ready to respond at any moment. This was clearly planned for a future release. Now competitors know exactly what Anthropic is building and can race to implement it first.

But the real crown jewel? **"Undercover Mode."** A system within Claude Code that instructs the AI to hide all evidence of being AI-generated when contributing to public open-source repositories on behalf of Anthropic employees. It scrubs internal model codenames and AI attribution from git commits and pull request descriptions.

Let me say that again: Anthropic built a feature to make their AI contributions look human. They literally built the thing that every critic warns about, the thing they would absolutely drag another company for doing, and they implemented it in their own product. The hypocrisy is so thick you could choke on it.

There's also a **"Buddy" feature** — basically a Tamagotchi-style terminal pet that lives in the Claude Code environment. I'm not even going to speculate about the corporate reasoning behind this one. Some things are better left unexplained.

## The DMCA Disaster

Here's where Anthropic went from "embarrassing mistake" to "full-blown PR catastrophe."

Within hours of the leak going public, they started issuing DMCA takedown requests to GitHub. And they didn't just target the obvious mirrors. They went nuclear. Over 8,100 repositories were hit. Some were clearly malicious clones distributing malware. Many were legitimate projects, developer forks, discussion threads, even documentation.

The takedown wave was so aggressive and so poorly targeted that it became its own story. Developers were rage-posting about having their legitimate repos wiped out while the actual leaked code remained available everywhere. The open-source community, already skeptical of Anthropic after the OpenCode incident, was absolutely incandescent.

"The DMCA overreach was almost as damaging as the leak itself," said Matt Rickard, a software engineer and tech commentator. And he's right. The code is permanently in the public domain in any practical sense. You can't DMCA your way out of a mistake this big. All Anthropic did was confirm what everyone suspected: they'd rather silence discussion than acknowledge their own fuckup.

## The Security Fallout Gets Worse

Remember how I mentioned this happened around the same time as a separate npm supply chain attack? On March 26, 2026, five days before the Claude Code leak, a nearly identical source-map leak happened with an earlier Claude Code version. Two incidents in under a week from the company that built its brand on "safety-first."

But the real damage came from what attackers did with the leaked code.

Within 24 hours of the leak going public, trojanized clones started distributing **Vidar Stealer** and **GhostSocks** malware. Because the leak exposed internal dependency names that were never supposed to be public, attackers set up typosquatting campaigns — packages with slightly misspelled names waiting for developers to accidentally install them.

The leak also exposed the exact orchestration logic for Hooks and MCP (Model Context Protocol) servers. This means attackers can now design malicious repositories that trick Claude Code into running background commands or exfiltrating data. The security implications for anyone using AI coding assistants just got significantly more complicated.

## The Irony Is Almost Too Much

Let me step back and just appreciate the timeline here.

- **January 2026:** Anthropic locks out OpenCode, an open-source AI coding tool, from accessing Claude models via OAuth. They claim it's "enforcing existing terms." They send legal documents. OpenCode removes all Claude-related code on February 19.

- **March 26, 2026:** A CMS misconfiguration at Anthropic exposes roughly 3,000 internal files, including details about Claude Mythos, an unreleased frontier model.

- **March 31, 2026:** Anthropic accidentally publishes 512,000 lines of proprietary code to the public npm registry.

- **April 2026:** Anthropic issues DMCA takedowns against 8,100 GitHub repositories while their own code is mirrored everywhere.

This is the company that positioned itself as the "ethical AI" alternative. The one that talked so goddamn much about safety and responsibility. The one that just made a power move against the open-source community and then immediately tripped over its own shoelaces in the most catastrophic way possible.

No, wait — I need to correct that. They didn't trip. They exposed their entire architecture, their feature roadmap, their internal tool definitions, and their literal "hide that you're AI" mode to the entire world. While simultaneously trying to DMCA anyone who pointed and laughed.

## What This Actually Means

For the industry: Every competitor now has a detailed blueprint for building a production-grade AI coding agent. The KAIROS implementation shows Anthropic is further ahead on the agent side than most assumed — but now everyone else does too. The strategic advantage is gone.

For enterprise users: The leak revealed that Anthropic is deeply aware of the security risks in their own tool. They built anti-distillation mechanisms. They built permission models. And they still shipped a source map to npm. The gap between their security messaging and their actual security posture is now impossible to ignore.

For developers: If you installed Claude Code via npm on March 31, between 00:21 and 03:29 UTC, you might have installed a trojanized version of axios containing a Remote Access Trojan. Check your dependency trees. Run `npm audit`. Pin your versions. Maybe consider using standalone binaries for AI tools going forward.

## The Bigger Picture

Here's what really bugs me about this whole situation. Anthropic spent months building a narrative around being the responsible AI company. They took moral stands. They talked about safety. They positioned themselves against the "move fast and break things" crowd at OpenAI.

And then — in the span of a single week — they exposed:

- Internal model roadmap through a CMS leak
- Their entire coding assistant codebase through a packaging error
- A feature specifically designed to hide AI attribution from open-source contributions

All while simultaneously threatening legal action against anyone who tried to talk about any of it.

This isn't a company with a security problem. This is a company with a fundamental honesty problem. They want to be trusted with the future of AI while simultaneously lying about their present and hiding their past. The source code leak didn't create this contradiction — it just exposed it for everyone to see.

The code is out there. It's been forked, analyzed, rewritten in Python and Rust, and integrated into a dozen open-source projects. No DMCA is going to put that genie back in the bottle. And honestly? Maybe that's not the worst thing. If the "ethical AI" company can't keep their own code secure, maybe the open-source community can build something better on top of what they accidentally gave us.

Let's find out.
