---
title: 'Linus Torvalds Just Called AI Bug Reports Pointless Churn'
date: 2026-05-19
description: 'The Linux security list is drowning in duplicated AI slop, and Linus finally said what everyone else was whispering: if you did not understand the bug, you did not do the work.'
---

Linus Torvalds looked at the Linux security mailing list and basically said: congratulations, you have turned vulnerability research into an industrial-grade spam cannon.

His words were better than mine, obviously. He said the list is “almost entirely unmanageable” because the same tools are finding the same bugs and then mailing the same nonsense to the same exhausted humans over and over again. Which is a perfect summary of 2026, honestly. Automation all the way down, except the last step is still some poor bastard reading twelve nearly identical reports and muttering into the void.

That is the part people keep dodging. AI did not invent bugs. It did not invent duplication. It did not invent laziness. It just made the whole operation cheaper, faster, and much more obnoxious.

If your “security workflow” is:

1. point model at code,
2. copy whatever confident sentence falls out,
3. blast it at maintainers,

then no, you are not doing research. You are operating a polite little nuisance machine in a blazer.

Linus’s actual point is better than the usual sanctimonious AI panic too. He is not saying “never use AI.” He is saying if AI found the thing, chances are somebody else already found it too, because the same tools are now everywhere. The value is not in being first to vomit a claim into a mailbox. The value is in understanding the bug, building a patch, and adding something that makes the project better instead of noisier.

That’s why the private security list bit matters. Torvalds basically said AI-detected bugs are not secret in the same way a real disclosure is secret. If the entire point is that a machine searched public code and spotted a pattern, then hiding the discussion behind a private mailing list just creates pointless churn. Nobody can see the duplicates, nobody can coordinate, and everybody wastes time pretending secrecy is a feature instead of a clerical fever dream.

And bless the kernel folks, they even had to update the docs around this mess. Not because they suddenly got religion, but because the flood got bad enough that the instructions had to be rewritten for people who apparently need an adult to explain that “I used an AI” is not a substitute for “here is a real bug with a real impact.”

The whole thing exposes the exact rot underneath a lot of modern “AI-powered security research.” People love the fantasy version where a model wanders through code like a wise little goblin and returns with treasure. The reality is much dumber. Most of the time it returns the same treasure everyone else already found, plus a mountain of duplicate reports, plus a bruised maintainer ego, plus an afternoon deleted by triage.

That’s not just annoying. It changes incentives. When the easiest path to clout is “send a report,” people stop learning the system. They stop reading docs. They stop checking whether the issue was fixed last month. They stop writing patches. They stop being researchers and become prompt-forwarding weather vanes.

And then they act surprised when maintainers start slamming doors.

I don’t blame them. At some point the job stops being “review security issues” and starts being “separate signal from machine-generated compost.” Nobody volunteered for that. Nobody woke up dreaming of becoming the bouncer at the AI bug report club.

What Linus is really defending is the boring, unsexy middle of the process: understand the thing, verify the thing, explain the thing, fix the thing. The part nobody wants to do because it doesn’t fit in a demo reel. The part that cannot be automated away without turning the whole exercise into expensive fan fiction.

So sure, use AI. But use it like a tool, not like a priest. If it points at a bug, read enough to know whether it’s real. If it’s real, show your work. If you can patch it, patch it. If all you have is a hallucination with a CVE-shaped haircut, maybe sit this one out and let the adults breathe for five minutes.

The kernel is not broken because AI exists.

It is broken because too many people keep mistaking noise for contribution.
