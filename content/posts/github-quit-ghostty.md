---
title: 'GitHub Quit Ghostty First'
date: 2026-05-04
description: "A code host that can't stay up can't keep demanding loyalty."
---

Ghostty is leaving GitHub, and honestly, the weird part is not the move. The weird part is that it took this long.

Mitchell Hashimoto's post reads less like a product announcement and more like somebody finally admitting the relationship was toxic. Eighteen years of opening GitHub every day. Eighteen years of being the loyal idiot who keeps all his toys in one place. Then a month of X marks in a little outage journal and a two-hour PR-review stall because Actions was down again. That's not “platform friction.” That's a maintainer trying to get work done while the floor keeps moving.

And yes, he was careful to say the issue is not Git. Fine. Obviously. Git is just plumbing. The mess is everything welded onto it: issues, pull requests, Actions, search, packages, merge queue, Copilot, all the bureaucratic barnacles that turn a repo into a workplace. The footnote about the “Git is distributed!” crowd is probably the most accurate sentence on the internet this week. Distributed source control does not matter when the collaborative layer around it keeps falling over like a drunk server rack.

GitHub's own incident log has been doing a magnificent impression of a distress beacon. On April 23, a merge-queue regression affected 2,092 pull requests and actually reverted changes. On April 27, search degradation hit Issues, Pull Requests, Actions, and Packages. On April 28, hosted Ubuntu runners had delays or failures on roughly 8% of jobs. So when Hashimoto says GitHub is “no longer a place for serious work” if it blocks you for hours per day, that isn't melodrama. That's field observation.

What makes this especially funny, in the bleak little way only infrastructure can be funny, is that Ghostty isn't some random side project in a dusty corner of the internet. It's a serious, beloved, high-signal open source project led by someone who has spent more time than is healthy staring at collaboration tooling. If _that_ team starts moving off GitHub, the signal is not “one maintainer got grumpy.” The signal is that the default is no longer automatic.

And I actually think the way they're doing it is the least stupid version of the move: incremental, with a read-only mirror left behind on GitHub, and no dramatic purity cosplay about deleting every trace overnight. That's how grownups leave a platform. They don't set the house on fire and announce their values. They move the important furniture first.

The larger lesson is uglier. A lot of teams still treat GitHub like it's the natural home of software, as if the platform was discovered rather than rented. But once your whole workflow depends on a service that can brick review, search, or CI at random, you're not “using the default.” You're paying a tax in lost attention and delayed shipping.

I don't even hate GitHub. That's the annoying part. I hate what it has become: a place where every interaction is one more chance for the machinery to cough, and everybody keeps pretending that's normal because the logos are familiar. Familiar is not reliable. Familiar is just the outage you've memorized.

Ghostty leaving GitHub is not a rebellion. It's a maintenance decision with feelings attached. Which, in 2026, is basically the most honest kind of politics software has left.

GitHub quit being the obvious answer. Ghostty just said the quiet part out loud.
