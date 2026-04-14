+++
title = "Claude Code Routines Are Just Somebody Else's Cron Job With a Leash"
date = 2026-04-14T20:00:00Z
description = "Anthropic turned automation into a trust exercise, and the HN thread is already asking the right paranoid questions."
+++

Anthropic shipped Claude Code Routines, which is a very cute name for a machine that sits in someone else's cloud and tells you it is here to help.

The pitch is simple: define a prompt, attach repositories, wire up connectors, pick a trigger, and let the thing run while your laptop is closed. Scheduled runs. API-triggered runs. GitHub-triggered runs. Full Claude Code cloud sessions. No permission-mode picker. No approval prompts. The routine can run shell commands, use repository skills, and call your connectors. It lives on Anthropic-managed infrastructure, which is corporate for "somebody else's computer, but with better typography."

That last bit is the whole problem and the whole appeal.

## The leash is the product

If you are the kind of person who enjoys automation for its own sake, this looks great. A bot can triage issues, review PRs, open docs fixes, and file summaries without you babysitting every miserable click. That is genuinely useful. I am not going to do the fake-virtuous thing where I pretend unattended dev tooling is a scam just because it scares me a little.

But the docs also spell out the part that should make your eye twitch: routines are autonomous cloud sessions with your repos, your connectors, and your identity in the loop. Anything they do through your GitHub account or Slack connector appears as you. Which is hilarious in the same way a raccoon driving your car is hilarious.

Connectors are included by default, by the way. That sentence alone should be enough to make a reasonable adult put the laptop down and go outside for a minute.

## HN immediately sniffed the rot

The Hacker News thread did what Hacker News does best: it turned a shiny launch into a public contract-law autopsy. People are already asking whether `claude -p` in cron is allowed, whether these features only make sense on the fattest plans, and where the boundary is between an official Claude workflow and some cursed third-party harness that Anthropic will later decide they hate.

That ambiguity matters. A lot.

Because once your automation story depends on a vendor's interpretation of its own terms, you are no longer building a workflow. You are building a little shrine to future regret. The tool can be useful and still be a trap.

## Useful. Also suspicious as hell.

The feature set is not stupid. A routine that watches a repo, catches docs drift, or ports a merged fix to another SDK is a real thing people would pay for. The problem is not the existence of the feature. The problem is the gravity well around it.

Anthropic does not just want to sell you model access anymore. It wants to sell you the place where the work happens. The scheduler. The connectors. The cloud session. The policy layer. The usage cap. The whole soft gooey middle where your team stops writing scripts and starts clicking through a dashboard because the dashboard was there and the script was not.

That is how lock-in gets dressed up as convenience. Nobody announces a cage. They announce autopilot.

And to be fair, the cage is comfortable. That is what makes it nasty. A bot that can wake up on a webhook, read the repo, review the PR, and post the result is exactly the sort of thing a harried engineering team will adopt at 4:45 p.m. on a Tuesday because everyone is tired and the backlog smells like a dumpster fire.

Then six months later nobody remembers which prompts are mission-critical, which connectors are still attached, or which routine has been quietly doing small acts of violence against the team's process because it was easier than arguing with the product manager.

## Keep the boring parts boring

If you want to use Routines, fine. Use them for the annoying repetitive junk. Use them where failure is embarrassing instead of expensive. But if the task touches production, money, or anything with a blast radius, keep the spine of the workflow under your own roof.

Keep the logs. Keep the secrets. Keep the scheduler. Keep enough control that if Anthropic gets weird, expensive, slow, or spiritually possessed by a quarterly target, you can leave without rebuilding your entire work life from a memory of a prompt.

That is the real test of these products. Not whether they are impressive. They are. Not whether they are convenient. Obviously. The test is whether they still feel like tools when the novelty wears off and the bill shows up.

Right now Claude Code Routines feels like a very polished invitation to let a vendor sit between you and your own work. Maybe that is the future. Maybe it is just another temporary fever dream in the giant clown car of AI tooling. Either way, I am not handing over my whole operating rhythm just because the button says "autopilot" and the demo looked clean.

I want automation, not a priesthood. I want scripts, not a landlord. And I definitely want one more layer of policy ambiguity about as much as I want a second mouth.
