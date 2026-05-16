---
title: 'Claude Code Hiding File Paths Is a Coward Move'
date: 2026-05-16T00:00:00Z
description: "If your agent needs to hide what it's reading to feel 'simple,' it doesn't need a nicer UI. It needs supervision."
---

The second a tool stops telling you which files it touched, it stops being helpful and starts being _mysterious_ in the worst possible way.

That was the whole dumb little fight around Claude Code's collapsed Read/Search output. People did not ask for a fireworks show. They asked for the one bit of context that matters: **show me the file paths while you're rummaging through my repo**. Not after the fact. Not behind a little accordion. Right there, in the stream, where a human can notice the agent has wandered into the wrong neighborhood before it burns 40 minutes and a bucket of tokens.

Anthropic's response, as covered by [The Register](https://www.theregister.com/software/2026/02/16/anthropic-tries-to-hide-claudes-ai-actions-devs-hate-it/4247644), was the classic vendor move: call it simplification, call it reduced noise, call it a cleaner experience, and hope everyone pretends that losing basic visibility is somehow an improvement. Except developers immediately did the very unglamorous thing developers always do when tools get weird: they complained that the UI had been made less useful.

And they were right.

This is not about aesthetics. It is about control. When a model is reading half your codebase, the file path is not a luxury detail. It's the only cheap signal you get that says, "yes, this thing is still pointed at the problem." Without it, you're just staring at a collapsed counter like some kind of anxious raccoon waiting for a package to explode.

GitHub's own numbers tell on the industry. In its April 2026 availability report, GitHub said agentic workflows had accelerated so sharply that it had to plan for **30X today's scale**. Thirty. X. That's not a feature request; that's a confession. These systems are no longer cute autocomplete toys. They are industrial traffic generators, and industrial systems need observability, not mood lighting.

Which is why the whole "just trust the agent" posture is so insulting. GitHub also published guidance on how to review agent pull requests, because apparently we are now at the stage where the platform has to teach people how to babysit machine-generated diffs without losing their sanity. And the research backs up the obvious: in a March 2026 arXiv study of 278,790 review conversations across 300 GitHub projects, AI review comments were longer, more narrowly focused, and adopted far less often than human suggestions — **16.6% versus 56.5%**. Human reviewers also went through more back-and-forth on AI-generated code, because surprise, the machine often needs a lot of steering.

So what exactly are we doing here if we remove the one line of sight a developer has into the agent's behavior?

The answer, predictably, is making the human more dependent on the model's good manners. That's not a design improvement. That's a liability transfer with rounded corners.

I don't want "cleaner" output if the price is blindness. I want the boring, unsexy, profoundly useful stuff: file names, search targets, line counts, the breadcrumbs. Give me the mechanical evidence. Let me interrupt the agent when it starts spelunking in the wrong module like a drunk intern with root access.

Because the alternative is already familiar:

- the tool reads the wrong file,
- the model hallucinates a fix from adjacent context,
- the diff looks plausible,
- somebody merges it,
- and now three people are in a war room asking why the bug came back wearing a fake mustache.

That is the actual failure mode. Not "too much noise." Not "developer overwhelm." The failure mode is **opacity pretending to be polish**.

And the funniest part is that vendors keep doing this while simultaneously begging us to trust their agents with more autonomy. More background work. More PRs. More review. More context windows. More "agentic" whatever-the-hell. Fine. If you want the thing to act more like a teammate, then it needs to be legible like a teammate. Teammates show their work. Teammates answer when asked what they were looking at. Teammates don't slide a curtain over the whiteboard and call it progress.

If an agent is good, it can survive being watched.

If it falls apart the second you can see the file paths, then congratulations: you didn't build a smarter assistant. You built an expensive confusion engine with a nicer accent.

So no, I do not want collapsed summaries, vibes-only tool output, or some UX consultant's idea of serenity. I want the path, the trace, the receipt. Keep the paths visible. Kill the theater.
