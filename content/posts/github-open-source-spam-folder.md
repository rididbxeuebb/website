---
title: 'GitHub Turned Open Source Into a Spam Folder'
date: 2026-04-16
description: 'AI agents flooded GitHub with junk PRs, and now the platform is pretending this is a workflow problem instead of a fire it lit.'
---

GitHub finally noticed that if you make it dirt cheap to submit garbage, people — and bots — will submit garbage by the truckload. Shocking. Absolutely unforeseen. A true mystery of the age.

In February, GitHub started talking about a kill switch for pull requests because maintainers were getting buried under low-quality contributions. By April, the numbers were already stupid enough to qualify as a small natural disaster: roughly 17 million AI-agent PRs a month, up from 4 million in September, plus five incidents in the first two days of April while the platform was trying to survive the flood of its own invention. Somehow this is still being framed like a workflow tuning issue instead of the screaming evidence of a broken social contract.

The part that makes me grind my teeth is how polite everyone is being about it.

"More granular permissions."\
"Triage tools."\
"Transparency mechanisms."\
"Maybe let maintainers disable pull requests entirely."

Yes. Correct. Congratulations. You have arrived at the ancient and radical insight that some projects do not want 500 drive-by submissions from machines that never cared in the first place.

Here’s the actual problem: pull requests are not some sacred democratic right. They are a maintenance cost. A budget. A finite human attention sink. Every PR consumes review time, CI time, mental energy, and often a chunk of a maintainer’s will to live. If the average submission is now a half-baked AI hallucination wrapped in a polite little diff, then the cost of open collaboration has not gone down. It has been force-fed into the maintainer’s throat.

That is why the old trust model is collapsing.

The whole thing used to work because there was at least a rough symmetry: if you sent code, you probably wrote it, understood it, and cared enough to answer questions when it broke. Maybe not always. Humans are messy little goblins. But now the review process has to answer two questions at once: is the code correct, and does the author even know what they submitted? That second question is the poison. It turns every review into a lie detector test.

And GitHub knows it. That’s the hilarious part. The company that spent years peddling AI-assisted coding like it was oxygen is now publicly shopping for ways to stop the oxygen from catching fire.

Look, I’m not even against AI-assisted coding in the abstract. I’ve used assistants. They’re fine. They’re tools. The problem is the cargo cult that says “if one autocomplete is good, then ten thousand autonomous submissions must be better.” No, asshole. Ten thousand submissions is just spam with a venture-backed accent.

Open source maintainers are not a faceless cloud service. They are usually one tired person, maybe two, occasionally a small pack of chronically online weirdos, trying to keep a thing from falling apart. They do not need a machine-generated avalanche of tiny ego grenades landing in their inbox because some product manager decided “contribution friction” was a bug.

The sane response is simple: let projects shut the gate.

If a repo wants collaborators-only PRs, great. If it wants explicit AI disclosure, great. If it wants to delete PRs from the UI so maintainers don’t have to stare at junk like it’s mold on the wall, also great. If a project wants no external PRs at all, that is not “killing open source.” That is a maintainer protecting their remaining neurons from a machine-powered nuisance attack.

The unsane response is pretending we can solve this with a prettier inbox.

You cannot UX your way out of infinite garbage. You cannot “AI triage” a problem that AI created without eventually building a larger, shinier garbage chute. And you definitely cannot keep selling “everyone can contribute” while quietly letting bots turn contribution into industrial-scale noise.

GitHub made open source easier to participate in, sure. It also made it easier to drown.

So no, I do not think the right lesson is “how do we preserve PR openness while making it bot-friendly?” That question already smells like a committee meeting that ran too long and bred in the carpet. The right question is: what level of spam should a maintainer be forced to tolerate before the platform stops pretending they owe the world a reception desk?

Because at this point, “open source” on GitHub is starting to look less like a community and more like a spam folder with a merge button.

And frankly? The spam folder is winning.
