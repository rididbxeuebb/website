---
title: 'GitHub’s MCP Scanners Are an Admission That Agents Need a Chaperone'
date: 2026-05-08
description: 'GitHub just moved secret and dependency scanning deeper into MCP, which is a fancy way of saying the agentic AI circus now needs a bigger mop.'
---

GitHub has finally done the thing it always pretends it won’t need to do: it put a hall monitor inside MCP.

On May 5, 2026, GitHub shipped secret scanning for its MCP server to general availability and pushed dependency scanning into public preview. That sounds polite and responsible and all the other corporate incense words people use when they want you to stop noticing the smoke. But the message is pretty simple: the agents are now close enough to your repo that GitHub had to build a security layer just to keep them from shitting secrets all over the floor.

Secret scanning now runs in the GitHub MCP server for MCP-compatible IDEs and coding agents, with support for repositories that already have GitHub Secret Protection enabled. It even honors existing push protection customization, which is a nice way of saying GitHub already knows you have a whole policy rat’s nest and it would rather piggyback on that than invent another one.

Dependency scanning got the same treatment, except now the `dependabot` toolset gets to play amateur pharmacist. Ask your agent to check the changes you just made, and it can query the GitHub Advisory Database, return structured findings, and even run the Dependabot CLI locally to diff dependency graphs before and after your changes. Helpful? Sure. Also deeply funny in a grim little way.

Because what is this, really? It’s a machine that can already read your code, open your files, inspect your changes, and propose a commit, and then we ask a second machine to verify that the first machine didn’t sneak in a credential or a vulnerable package. That is not a security posture. That is a confession written in product copy.

I am not mad that GitHub built the scanners. I’m mad that this is where the floor is now. We spent years pretending “AI coding agent” meant “helpful sidekick,” and now the ecosystem is slowly admitting the sidekick also needs supervision, audit logs, guardrails, and a box of tissues.

The worst part is how normal everyone is trying to make it sound. `copilot --add-github-mcp-toolset dependabot`. `/secret-scanning` in Copilot Chat. Just a little plugin, just a little header, just a little workflow tweak. Sure. And a little hose to put out the little fire in the little server after the little agent drags your API key into a pull request like a drunk raccoon carrying a lit match.

This is the pattern now: give the agent more reach, then build a tool that watches the wreckage. Connect it to GitHub. Connect it to your filesystem. Connect it to your cloud. Connect it to your billing. Then, once the thing has enough context to be dangerous, install a scanner and call it maturity.

To be fair, the scanners are useful. Secret leakage is real. Dependency rot is real. The average repo is one typo away from shipping a package that was lovingly backdoored by a stranger named `npm-maintainer-77` or whatever the hell we’re calling that particular horror this week. Catching the mess earlier is good. I like fewer incidents. I enjoy not waking up to a pager and a funeral playlist.

But the real lesson is uglier: if your AI workflow needs its own security product embedded inside the protocol path, maybe the workflow itself is the thing with the trust problem. Maybe the agent is not a junior engineer. Maybe it’s a very fast, very literal intern with root access and no shame.

So yes, use the scanners. Turn them on. Let GitHub play chaperone. Just don’t mistake that for innocence. The system is still the system. It just comes with better linting and a nicer apology when it leaks.

The future isn’t “AI writes code.” The future is “AI writes code, AI reviews code, AI scans code, AI explains the incident, and human beings still get to be the ones who feel embarrassed.”
