+++
title = 'Rsync and the Death of the Regression Budget'
date = 2026-06-02T09:00:00Z
description = 'When a backup tool starts a culture war, the real bug is usually the release process, not the keyboard wizard everyone is yelling about.'
+++

Rsync is not supposed to have discourse.

It is supposed to move bytes from one place to another, silently, like a municipal worker with a grudge. If your backup tool becomes a trending topic, something has already gone sideways. And sure enough, the last few days of rsync drama have been a perfect little clown car: one issue about “vibe coding,” another about removing LLM-generated commits, and a comment section where everybody is either cosplaying as a security auditor or defending the honor of a 30-year-old utility like it’s a family heirloom.

My hot take is annoyingly simple: the problem is not “AI bad” and it is not “humans bad.” The problem is that rsync sits in the worst possible category of software — infrastructure that is old, trusted, widely installed, and apparently expected to evolve without ever making a mistake.

That category does not exist.

The complaints in the issue thread are not coming from nowhere. People pointed at regressions in newer releases: older Linux kernels getting shoved aside by `openat2()` assumptions, `--files-from` and `--delete-missing-args` acting weird, `--link-dest` in daemon mode going feral, and native-protocol reads throwing “invalid argument” errors. None of that is glamorous. None of it looks like a grand exploit. It is just the kind of boring, sticky breakage that ruins backups, which is exactly why it matters.

Backups are not the place for performance art.

And this is where the AI debate gets stupid in a hurry. People see `Co-Authored-By: Claude` in a commit and immediately start yelling about slop, while other people instantly jump to “you ship zero features, shut up.” Both reactions are a little too eager and a little too convenient. The model is not the moral center of the story. The release process is.

If a maintainer uses an LLM to rewrite tests, refactor shell scripts, or sketch out syscall shims, fine. I am not interested in purity theater. But the moment that workflow turns into a larger volume of change than the project’s review and test discipline can comfortably absorb, you have created a stability tax. The machine didn’t invent the bug. It just helped you ship enough surface area for the bug to hide inside.

That is the real hazard: confidence inflation.

LLMs are very good at producing code that looks like it belongs. They are also very good at making a maintainer feel productive while silently increasing the amount of stuff that needs human skepticism. That is a nasty combination in a utility whose job is to be boring forever. If you are touching rsync, you do not get to be interesting. You get to be careful.

What makes the whole mess more irritating is that the project now has all the ingredients for a classic infra tragedy: a venerable codebase, a maintainer under pressure, a pile of regressions, and a community that wants two incompatible things at once. They want the tool to stay frozen in amber, and they want it to keep fixing security issues, adding tests, and supporting newer systems. Sorry. You do not get infinite change with zero churn. Physics is rude like that.

So here is the part nobody wants to say out loud: if rsync is going to move at all, it needs a regression budget. Not a vibe. Not a crusade. A budget.

That means:

- slower releases when the change set gets weird
- a real stable branch for people who value “does not eat my backups” over “new shiny bits”
- explicit review for risky platform changes
- and enough humility to admit when a refactor is actually a gamble

That last one is the killer. The internet is obsessed with velocity, so every broken release gets retconned into “innovation.” No. Sometimes you just shipped a bigger pile of uncertainty than your process could carry.

I say this as someone who has absolutely trusted old tools way past the point where they deserved my trust. Everybody has. That’s how infrastructure works. You find one thing that is dull and reliable and then you build a small religion around it. The minute it starts getting fashionable, the spell breaks. Suddenly you’re reading issue trackers at 1 a.m. and wondering whether your backups have been doing interpretive dance for three weeks.

That is why this whole rsync saga hits a nerve. Not because the internet discovered AI, and not because a maintainer used a tool people are weirdly sentimental about hating. It hits because it exposed the fragile contract underneath old software: trust me, I will remain less exciting than a tax form.

Once that contract is broken, the arguments get loud fast.

My answer is boring, which is probably why it is correct: keep AI away from the part of the process where “move fast” turns into “lose data.” Let it help where it helps. But if the project is critical infrastructure, treat every big change like it might be the one that makes a thousand backups cry in the dark.

Rsync does not need a personality.

It needs to be right.
