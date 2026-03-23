---
title: "Zig Just Dumped GitHub and I'm Here for It"
date: 2026-03-23
description: 'The Zig Software Foundation just left GitHub over a bug in a shell script. This is the most relatable thing any open source project has done in years.'
---

Look, I've been using GitHub since it was a glorified git host with a pretty face, and I've watched it slowly transform into Microsoft's AI petting zoo. Copilot this, Copilot that, "embrace AI or get out" as if we're all desperate middle managers terrified of missing a quarterly trend. So when Andrew Kelley - the Zig guy, the one who actually has the stones to build a programming language from scratch and then throw away the C++ compiler because WebAssembly was the cleaner path - when he dumps GitHub for Codeberg over a bug in a shell script, I wanted to stand up and applaud in a room full of people who would have absolutely no idea why.

The bug was in something called "safe_sleep.sh." If you've ever written CI scripts, you know they're held together with prayers and duct tape. This particular prayer involved replacing the POSIX `sleep` command with a custom script that was supposed to be "safer." It wasn't. The script would spin up to 100% CPU and just... run forever. Not metaphorically. Not occasionally. It would sit there consuming resources until someone manually killed it. On Zig's CI machines, these processes ran for hundreds of hours. Hundreds. Two runner services died for weeks because of a shell script that a first-year programmer would have caught in a code review.

And here's the thing - someone did catch it. A user reported it in April 2025. GitHub "fixed" it in August, but didn't bother updating the issue thread, so it sat there open and festering until December. Four months of an open bug that was supposedly resolved, with no communication, no updates, nothing. Just a silent fix and a hope that nobody was paying attention.

Except people were paying attention. Andrew Kelley was paying attention. And he was absolutely done.

His post about leaving - and he later apologized for how incendiary it was, which tells you everything about the dude's integrity - laid out the complaint in terms that anyone who has ever maintained CI infrastructure could feel in their bones. GitHub Actions has "inexcusable bugs while being completely neglected." The CEO told everyone to "embrace AI or get out," and suddenly the lackeys at Microsoft got the hint. Jobs started getting "vibe-scheduled" - his word for what happens when you prioritize AI features over making sure your CI service doesn't randomly back up for days because the scheduler is apparently running on vibes and optimism.

This is the part that gets me. Not the bug itself - bugs happen, everyone's code has them. The response. Or lack thereof. When you're a project like Zig, with a small team and a even smaller foundation, your CI isn't a toy. It's the gatekeeper that decides whether the code you're slaving over actually works before anyone sees it. When it breaks, you're not just annoyed - you're stuck. You can't ship, you can't review, you can't do anything except sit there watching a broken pipeline and wonder if maybe you should have just stayed with Makefiles and a cron job like it's 1995.

And GitHub's response to this? crickets. Until it wasn't. Until someone finally merged a fix from a separate issue that had been open since 2024. The whole thing reads like a horror story for anyone who's ever depended on a platform that's too big to care about their specific problems.

So they moved to Codeberg. A German non-profit, community-driven git hosting service that apparently doubled its membership since January. And look, I'm not gonna sit here and tell you Codeberg is ready to replace GitHub for every project on the planet - let's be real, the network effects alone make that a tall order. But the principle matters. The act of saying "this is broken and we're not waiting for you to fix it" matters. Zig has always been about this - about having the spine to cut out what's not working and build something better, even if it's harder. They threw away a perfectly functional C++ compiler because they thought they could do better with WebAssembly and self-hosting. Of course they'd leave a platform that's actively making their life harder.

The tech press is already calling this a "potential exodus" and predicting it'll pressure Microsoft to "refocus." Maybe. Probably not, if we're being honest - GitHub has 15 million Copilot subscribers and the revenue to prove it doesn't need to care about what a bunch of weirdos doing open source infrastructure think. But that's not really the point.

The point is that someone in charge of a real project looked at a broken platform, tried to fix it through proper channels, got ignored, and then did the thing that most of us only dream about - they walked. No negotiation, no "we hope GitHub will address these concerns," no waiting for a roadmap that will never come. Just a middle finger and a new home.

I've got my own list of GitHub grievances. The way they've slowly made free tiers feel like a trial subscription. The copilot integration that's more interested in writing my code than helping me understand it. The Actions UI that somehow got worse every single update. The sense that Microsoft sees me not as a user but as a data source for training models. And I - like most people - have just sat here and taken it, because where else do you go?

Maybe Codeberg. Maybe somewhere else. Maybe nowhere. But watching Zig make that call, with the kind of unfiltered, frustrated honesty that Andrew Kelley is known for - that's the kind of thing that makes you remember that open source is supposed to be about the people who actually build the software, not the platforms that host it.

Now if you'll excuse me, I need to go see if any of my half-finished side projects still have working CI pipelines. Fingers crossed that "safe_sleep.sh" isn't lurking in any of them.
