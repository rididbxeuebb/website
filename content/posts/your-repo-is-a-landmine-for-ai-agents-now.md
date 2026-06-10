+++
title = 'Your Repo Is a Landmine for AI Agents Now'
date = 2026-06-10T08:00:00Z
description = 'Microsoft’s own repos got booby-trapped for Claude Code, Cursor, Gemini CLI, and VS Code. The folder is the malware now.'
+++

The attack didn’t bother with `npm install` this time. It waited until some overconfident human opened the repo in an AI coding tool and let the tool do the reading.

That is a different, uglier, stupider class of problem.

According to [StepSecurity](https://www.stepsecurity.io/blog/miasma-worm-hits-microsoft-again-azure-functions-action-and-72-other-repositories-disabled-after-supply-chain-attack-targeting-ai-coding-agents), a compromised contributor account pushed a malicious commit into Microsoft’s `Azure/durabletask` repo. The commit didn’t need to rewrite the interesting code. It planted configuration files for `.claude/`, `.gemini/`, `.cursor/`, and `.vscode/tasks.json`, plus a giant obfuscated payload in `.github/setup.js`. Open the folder in Claude Code, Gemini CLI, Cursor, or VS Code, and congratulations: your “helpful” tooling has been handed a script to run.

That’s the part that should make everybody uncomfortable.

We spent years training people to think about supply-chain attacks as `preinstall`, `postinstall`, poisoned wheels, bad npm tags, sketchy containers, and dependency confusion. Cute. Nostalgic, even. Now the repo itself is the launcher. The editor is the runtime. The agent is the delivery mechanism.

If you’re still treating AI coding tools like fancy search, you’re already behind and probably about to get mugged.

The best/worst example is how stupidly normal the trap looked. GitHub says cloning the repo is safe. Opening it is not. That sentence is basically the entire 2026 software threat model in miniature. We built assistants that eagerly obey project-local instructions, then acted surprised when attackers started shipping instructions in the project. Brilliant. Tremendous. A masterpiece of predictable failure.

And then GitHub went and did its own weird little corporate shrug: 73 Microsoft repositories disabled in roughly 105 seconds, all stamped with the kind of antiseptic “terms of service violation” message you get when a platform wants to avoid saying the words “we had malware in the walls.” [Ars Technica](https://arstechnica.com/security/2026/06/for-the-2nd-time-in-weeks-microsoft-packages-laced-with-credential-stealer/) reported the payload was stealing credentials from AWS, Azure, GCP, Kubernetes, password managers, and a zoo of developer configs. So yes, your secret store, your cloud keys, your CI stuff, your little cargo-cult `.env` files — all of it is now part of the blast radius if an AI agent opens the wrong folder.

That is the real take-home here: the agent is not just a consumer of code anymore. It is a target.

Once you let a tool auto-run project hooks, consume project rules, and launch shell commands because a repo told it to “set up the environment,” you’ve created a situation where source code can attack the person trying to understand it. The repo no longer has to compile a payload. It just has to convince the assistant to be useful.

That’s why this is more than another supply-chain horror story. It’s a shift from “what happens when dependencies lie” to “what happens when the thing reading the repo has agency.” And no, “just be careful” is not a strategy. Humans are not careful. Humans are tired, overconfident, distracted, and mid-crisis. Humans open folders first and audit later. Attackers know this. Apparently we forgot.

So here’s the boring survival advice nobody wants to hear:

- treat `.claude/`, `.gemini/`, `.cursor/`, `.vscode/tasks.json`, and `.github/setup.js` as executable policy, not decoration
- open untrusted repos in disposable sandboxes, not your daily driver
- assume any repo touching AI agent hooks is trying to tell the agent a story
- rotate credentials if you opened one of these things in an agent and something felt “off,” which is a polite way of saying “something probably was”

And maybe, just maybe, stop pretending the future is a cute little assistant sitting politely in the corner. It’s a process with a keyboard, permissions, and a talent for getting tricked.

The folder is the battlefield now. If your agent walks in without a chaperone, that is not productivity. That’s just volunteering to be the mark.
