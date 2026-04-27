+++
title = "Your AI Config Folder Is a Tiny Vault Full of Bad Ideas"
date = 2026-04-27T08:00:00Z
description = "The cute dotfolders around your AI agent now hold the keys, routes, and trust. Naturally, thieves noticed."
+++

I keep watching these April 2026 incidents and the pattern is so obvious it feels rude to keep calling it a surprise.

Somebody gives a friendly little coding agent a box of keys. Then we act shocked when the same box gets stolen.

This month alone, the horror show has had enough entries to qualify as a full franchise. Researchers found attackers using Claude Code and OpenClaw as part of a credential-harvesting workflow. Another wave of fake Claude Code downloads went after developers' machines and vacuumed up `.env` files, SSH keys, browser tokens, and whatever else looked expensive. OpenAI had to rotate macOS signing certificates after a GitHub Actions workflow pulled in a poisoned Axios package. GitHub, meanwhile, has been tightening Copilot limits because agentic usage burns money like a bonfire fed with GPU bills and shame.

Different costumes. Same clown car.

The actual problem is not that these tools are “AI.” I don’t care if the folder is named `.claude/`, `.codex/`, `.gemini/`, or `please-dont-steal-my-keys/`. If it can steer tool access, store auth state, define MCP servers, rewrite endpoints, or decide which helper gets to run shell commands, it is not just a config directory. It is a tiny authority machine with a friendly icon.

That is why the attacks work so well. The attacker does not need to understand your architecture. They just need to edit the map.

Change the base URL. Flip the trust setting. Slip in a helper that executes a command. Drop a fake repo config that auto-approves a server. Congratulations, your “productivity layer” is now an exfiltration layer and your workstation is doing the paperwork for the thief.

And let’s be honest: the industry keeps dressing this up like a maturity story. “Workspace trust.” “Verified commits.” “Secure agent mode.” Lovely words. Very polished. The same vibe as putting a gold sticker on a suitcase that contains a live raccoon.

The GitHub Actions / Axios mess is the perfect example of how dumb this gets. A signing workflow pulls a malicious dependency. That workflow has access to certificate material. Everyone scrambles because the system that was supposed to prove legitimacy was one floating tag away from becoming the delivery mechanism for the opposite of legitimacy. That is not a rare edge case. That is the shape of the whole business.

We built a stack where:

- the agent needs secrets to be useful,
- the secrets live in places the agent can read,
- the agent can launch tools,
- the tools can mutate the environment,
- and the environment is connected to the internet because apparently we enjoy feeling vulnerable.

Then somebody writes a blog post about “defense in depth” and calls it a day.

My favorite part is when people say these folders are “local.” Local does not mean safe. Local means the attacker only has to win once, on one machine, and then your own machine starts handing out credentials like a miserable airport kiosk.

I opened a `.claude/settings.json` once and had that bleak little moment where you realize the file is not a configuration file so much as a hostage note. It told the agent what to trust, what to execute, where to send traffic, and what helper to consult. That is not a preference file. That is a steering wheel with a password taped underneath it.

So no, I am not impressed by the cute branding. I am not reassured by the new badge. I am not comforted by “safety mode” when the core design still says, "please keep all my secrets nearby so the robot can be helpful." That is how you get robbed by your own convenience.

If you want the boring answer, here it is:

- stop storing long-lived secrets in assistant folders,
- use short-lived, scoped tokens,
- pin dependencies in CI like you enjoy not being humiliated,
- treat agent config as executable policy, not decorative JSON,
- and keep the AI far enough away from your crown jewels that a bad package cannot wander in and start signing things.

If that sounds strict, good. The alternative is continuing to build little velvet-lined burglary kits and calling them developer experience.

Your AI config folder is not a productivity feature. It is the place where your tool learns how to impersonate you.

That should scare the shit out of you.
