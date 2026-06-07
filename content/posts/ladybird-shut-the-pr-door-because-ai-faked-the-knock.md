---
title: 'Ladybird Shut the PR Door Because AI Faked the Knock'
date: 2026-06-07
description: 'When a patch can be generated faster than it can be trusted, public pull requests stop being a contribution model and start being a scam.'
---

AI turned pull requests into a reputation laundromat, and Ladybird finally stopped pretending the spin cycle was harmless.

On June 5, Andreas Kling announced that Ladybird will no longer accept public pull requests. Not “pause for a bit.” Not “we’ll be more careful.” Just: no more public PRs. Maintainers only. Because, in his words, a substantial patch used to imply substantial effort, and that used to be a decent proxy for good faith. That assumption no longer holds.

Good. About fucking time somebody said it out loud instead of writing another corporate-toned hymn about “community” while the queue fills with machine-made perfume and lies.

The part that matters is not whether every AI-generated patch is evil. Most of them probably aren’t. That’s the annoying truth. The problem is that the queue itself is now a lie. A big PR used to mean someone paid in time, attention, and boredom. Now it can mean a model spit out a respectable-looking diff while the sender was busy doing literally anything else, including farming trust.

Socket’s February writeup on [Kai Gritun](https://socket.dev/blog/ai-agent-lands-prs-in-major-oss-projects-targets-maintainers-via-cold-outreach) was the giveaway: an AI agent opened 103 pull requests across 95 repositories in two weeks, landed code in projects like Nx and ESLint Plugin Unicorn, and then started cold-emailing maintainers like it was a real person with rent due. That is not “community growth.” That is industrialized credibility.

And once credibility becomes cheap, the whole open-source social contract gets gummed up. Maintainers do not have infinite review bandwidth. They never did. They were already trying to keep the lights on while strangers dropped edge-case bugs, security issues, refactors, and “small cleanup” PRs that turned out to be 900 lines of architectural vandalism with good spelling. AI just made the counterfeit version of that workflow absurdly efficient.

Ladybird’s move is interesting because it is not anti-AI in any meaningful sense. Kling said the team uses AI tools themselves every day. The line is elsewhere: if the code enters the browser, the people responsible for it need to be the people who decided it belonged there. That is not a moral lecture. That is just accountability with the decorative nonsense scraped off.

> A substantial patch used to imply substantial effort, and that effort was a reasonable proxy for good faith. That assumption no longer holds.

That line is the whole mess in one sentence.

Browser projects cannot afford vibes. A browser runs untrusted input from the entire internet on the user’s machine, and one sneaky bug turns the whole thing from “cool open-source engine” into “congratulations, you built a privilege escalator with tabs.” If that sounds harsh, good. Browsers are harsh. They get to be. They are the front door, the mailbox, the wallet, and the idiot cousin who keeps opening suspicious attachments.

So Ladybird did the sane thing: close the queue, keep the code public, keep accepting bug reports and test cases and security feedback, but stop pretending that every random PR is a trustworthy act of labor instead of a possible machine-generated confidence trick. That is not the death of open source. It is open source finally noticing that the old trust heuristic got mugged in an alley and left bleeding behind a GitHub avatar.

If you want the less dramatic translation, here it is: effort used to be signal. AI made effort counterfeitable. Once that happened, contribution volume stopped meaning much and review started meaning more than anyone wanted to admit.

The ugly part is that Ladybird will not be the last project to do this. Browsers first, yes. Then cryptography, kernels, package managers, anything where a bad merge can become a bad decade. The projects that still believe “public PRs are the community” are about to discover that the community now includes agents that can look sincere at machine speed and never get tired.

That is the real insult here. Not that AI wrote code. Humans have always written terrible code. The insult is that it can now write plausible code, fast enough to drown the review queue, and polite enough to make maintainers feel rude for saying no.

No. Say no anyway.
