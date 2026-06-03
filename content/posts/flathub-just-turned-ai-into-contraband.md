---
title: 'Flathub Just Turned AI Into Contraband'
date: 2026-06-03
description: 'The policy is understandable, wildly asymmetric, and mostly a headache for the honest people it can actually see.'
---

Flathub looked at the submission queue, inhaled the smell of a thousand mush-brained “AI-assisted” excuses, and said: no more.

Not just code. Not just manifests. The app, the metadata, the patches, the build scripts, the pull request text, the whole cursed bundle. If a machine helped write it, the answer is apparently get bent.

And, annoyingly, I get it.

If you’ve spent any time reviewing package metadata that reads like a sales bot with a concussion, or a patch that feels like it was hallucinated by a raccoon in a hoodie, you can feel the maintainer fatigue through the screen. Bart Piotrowski basically said the quiet part out loud: people were acting entitled, the interactions got stupid, and he was tired. Fair. The man sounds like he has seen things.

GNOME Circle is already drowning in backlog, so the reaction is not exactly mysterious. In their own survey, 62% of maintainers said they don’t use LLMs at all, 34% said they use them for little snippets or questions, and 3% said they use them for larger chunks of code. In other words: mostly humans, a little machine-assisted trivia, and a review queue that still somehow looks like a landfill fire.

But here’s the part where the policy stops being a hammer and starts being a vibes-based toll booth.

Flathub hosts open source and proprietary apps. That means the only people the policy can really inspect are the ones leaving their work in the open. If your repo, manifest, and PR are public, reviewers can at least try to sniff out AI sludge. If you ship closed source and keep your mouth shut, good luck proving anything. So the honest people get the paperwork. The liars get plausible deniability. Lovely system. Beautiful little joke. Extremely on brand for software governance.

The policy also covers the Flathub submission itself, which is where it gets especially funny in the miserable way. You can apparently get bounced for using AI to write the PR description. That is either righteous or absurd depending on how much coffee you’ve had and whether you’ve recently had to read a PR written like an enterprise chatbot with a marketing degree.

There’s also the lovely exception for “mature, well-maintained projects,” which is exactly the sort of phrase that makes bureaucrats feel warm and everyone else reach for a chair to throw. Who decides maturity? Who gets the exception? Who gets told to go away? You already know the answer: whoever is tired, whoever is known, whoever has enough history to be trusted, which is just a polite way of saying rules for thee, discretion for me.

And no, the policy is not retroactive. Existing apps stay. Which means this is not cleanup. It’s border control after the smugglers already got through and set up shop.

If you want a model that at least looks like it understands the real problem, look at the Linux kernel. It says: disclose the AI help, keep a human responsible, and do not pretend the robot can sign the DCO. QEMU is moving in a similar direction, narrowing the ban and tagging AI-assisted patches instead of trying to pretend the entire category can be wished out of existence. That’s ugly. It’s also honest.

Flathub chose a different kind of honesty: “we are sick of your shit, and we are closing the door.” I respect the mood. I do not trust it as a long-term governance model.

Because blanket bans rarely ban the thing they claim to ban. They mostly punish the people willing to be inspected, while the worst actors keep their heads down and sail right past. That is not a security policy. That is a moral speed bump with a clipboard.

So yes: ban the slop if you need to. Kick out the entitled slop goblins. Let the maintainers breathe for five minutes. They’ve earned it.

Just don’t pretend this is a clean solution. It isn’t. It’s a pressure release valve. Which, honestly, might be the most realistic thing anybody has shipped all week.

The rest of us can enjoy the smell of burning paperwork and move on.
