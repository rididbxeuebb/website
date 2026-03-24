+++
title = "Dan Blanchard just murdered copyleft and called it a rewrite"
date = 2026-03-24T12:00:00Z
description = "The chardet 7.0.0 debacle proves that AI has finally killed the only thing protecting open source from corporate parasites."
+++

Let me tell you about a library called chardet. You probably have it installed right now. It's sitting in your Python environment, doing the quiet, invisible work of figuring out what character encoding some file is using. Billions of downloads. Years of volunteer labor. Originally created by a guy named Mark Pilgrim, released under the LGPL because he believed in the idea that if you benefit from free software, you should give back.

And then, in March 2026, Dan Blanchard — the maintainer who inherited the project — used Claude Code for five days and published chardet 7.0.0 under the MIT license. Same package name. Same API. Drop-in replacement. Just, you know, with the entire copyleft protection stripped away because he fed the old code to an AI and asked it nicely to make something new.

And the tech press? The "journalists"? Half of them are calling this an "innovation." A "clean room implementation." They're framing it like Dan did something clever. He found a loophole! He played the game! Welcome to the future, baby!

I'm going to be sick.

## The "clean room" argument is garbage and everyone knows it

Clean room implementation is a real concept. Compaq did it in 1982 to reverse-engineer the IBM BIOS — one team studied the original to write specifications, a completely separate team built new code from those specs with zero exposure to the original. It's clever. It's legal. It takes actual effort.

Now explain to me how you can do a "clean room" implementation when:

1. You're using an LLM that was almost certainly trained on the code you're trying to "rewrite"
2. You've personally maintained that codebase for twelve goddamn years
3. You didn't even wipe your git history — you just made a fresh commit and hoped nobody would notice

The JPlag similarity score showing 1.29% structural similarity is not the flex Dan thinks it is. The code is different. The architecture is the same. The problem domain is the same. The _API_ is the same, by design. The training data almost certainly contains the original. And even if it didn't — even if we pretend Claude Code is some kind of magic purity engine — Dan has been marinating in this code for over a decade. You think that doesn't influence what he prompts?

Please. This is "clean room" the same way that saying the N-word with your Windows microphone on is "accidental."

## Mark Pilgrim came back from the dead for this

Here's the part that really gets me. Mark Pilgrim deleted himself from the internet in 2011. That's not a metaphor — he did what internet historians call an "infosuicide." Walked away from everything. His books, his projects, his online identity. Gone.

And the _first thing_ that brings him back is this bullshit. He had to drag himself out of digital retirement to tell Dan Blanchard that no, actually, you don't have the right to relicense my code, what the fuck are you doing.

Read that issue. The one where he calmly, precisely explains why this is a violation of the LGPL. He's not screaming. He's not threatening a lawsuit. He's just... explaining copyright law to a guy who apparently thought "but I used AI" was a magic spell that made all previous agreements disappear.

And Dan's response is essentially: "You're right that I had extensive exposure to the original codebase. A traditional clean-room approach involves separation. But that would have been expensive. So I used an LLM instead. Here's my JPlag report."

That's it. That's his defense. "I know this isn't how clean room works, but clean room is expensive and I'm tired."

## Bruce Perens is right and I hate that I'm agreeing with him

Look, Bruce Perens has said some things over the years that I think are half-baked at best. But when he says the entire economics of software licensing are dead, that the fundamental assumptions behind GPL were built for a world where humans wrote code — I don't think he's exaggerating.

Think about what just happened. The LGPL existed because the people who wrote it understood that companies would happily take open source code, use it to build proprietary products, and give nothing back. The license was the guardrail. It said: you can use this, but if you improve it, you have to share the improvements too. That's not charity. That's just basic fairness.

AI just made that guardrail meaningless. Because now you don't need a team of engineers to do a clean room implementation. You need an API key and a weekend.

If this flies — if chardet 7.0.0 can just sit on PyPI under MIT while Mark Pilgrim screams into the void — then copyleft is dead. Not "under pressure." Dead. Every GPL project ever written is now one well-crafted prompt away from becoming someone else's permissive backend.

## The NVidia employee who called it "absolutely toxic" was not being dramatic

There's a comment in the GitHub issues from someone who identifies as working at NVidia. They said, and I'm quoting: "Given the existence of issue #327 chardet v7.0.0 is absolutely toxic. If my employer's open source review legal people got wind of it, I seriously doubt that they'd approve v7.0.0 and up for any use under any circumstances whatsoever."

That's not a random internet person being dramatic. That's a software engineer at a major tech company who understands the legal risk. Because here's the thing — Dan might be right that his implementation isn't a derivative work. Or a court might decide differently in five years. Or the copyright on AI-generated code might get sorted out in a way that makes this entire thing legally murky.

You know what companies don't do? They don't deploy code with unresolved copyright questions in a prominent dependency. They're going to fork chardet 6.0.0, pin it forever, and never touch 7.0.0. Which means Dan achieved his goal of creating an MIT-licensed alternative and simultaneously split the userbase, introduced uncertainty, and made life worse for everyone who just wanted to detect character encodings.

Great job. Heroic, really.

## What actually should have happened

If Dan wanted an MIT-licensed character encoding detector, he could have:

1. Created a new package called `aichardet` (someone in the issue comments literally suggested this)
2. Documented clearly that it's inspired by chardet but is a separate implementation
3. Let users choose based on their licensing needs
4. Not appropriated the reputation and PyPI downloads of an existing project

Instead he chose the nuclear option: use the same package name, the same versioning scheme, replace the original in place, and change the license to MIT. All while claiming it's a "ground-up rewrite" as if that absolves him of the fact that the project only has value because of twenty years of Mark Pilgrim's original work.

It's the software equivalent of showing up at someone's house, changing the locks, repainting, and then insisting you built the house from scratch because you hired a crew to do it while standing in the driveway.

## The worst part

The worst part is that I understand why Dan did it. I do. He's been maintaining chardet for twelve years. He probably is tired. He probably does want to contribute to the Python standard library and feels like the LGPL is in the way. He probably genuinely believes he did nothing wrong.

And maybe — maybe — a court will agree with him. Maybe the MIT license will hold up. Maybe this will be the new normal and I'll have to update my understanding of how open source licensing works.

But even if Dan wins legally, he lost something worse: he proved that the social contract of open source is bullshit. That maintainers can't trust that their work will be protected. That the moment someone with commit access gets tired enough, they can just... AI-wash the license away.

Mark Pilgrim gave us chardet because he believed in sharing. In the idea that software could be free and still sustainable, as long as everyone played by the rules.

Dan Blanchard just showed us what happens when those rules meet a sufficiently powerful autocomplete.

I genuinely hope Mark finds peace. He deserves better than this.

And to everyone celebrating chardet 7.0.0 as a "win" for the open source community: I hope your dependencies don't start disappearing into permissive licenses when their maintainers get bored. I hope you enjoy that.

It's going to be a fun decade.
