---
title: "Zig's Writergate Is Either the Most Based Move in Programming or a Sign of Deep Madness"
date: 2026-04-10
description: 'Andrew Kelley just rewrote std.io. Again. And honestly? He might be right, but everyone who uses Zig deserves a medal for sticking around.'
---

Andrew Kelley broke IO again. Let me say that louder for the people in the back: **Andrew Kelley broke I/O again**, and this time he called it "Writergate" because apparently we're all living in some kind of programmer Watergate tribute act now.

If you missed it - and honestly, congratulations if you did, because July 2025 was a wild month - Kelley merged a pull request that completely gutted std.io.Reader and std.io.Writer. Not deprecated. Not gradually phased out. **Gutted**. Replaced with new non-generic interfaces where the buffer lives in the interface, not in the implementation. 15,000 lines changed. Hundreds of APIs renamed, moved to `.deprecatedReader`, or deleted outright. This wasn't a breaking change. This was a **hostile takeover of the standard library**, and I mean that as the highest compliment possible.

Here's the thing though: the motherfucker was right. That's what kills me.

## The Technical Case (Trying to Be Objective for Once)

The old `std.io.AnyWriter` had what the issue described as "very high overhead in tight loops" because it prevented inlining. You know what that means in practical terms? Every single write operation in a tight loop was slower than it needed to be, because the generic vtable dispatch meant the optimizer couldn't see what was happening. Someone at Zig tested custom buffering and got 2x faster performance. Two. Fucking. Times. Just by avoiding `AnyWriter`.

So Kelley did what Kelley does: he threw out the entire design and rebuilt it. The new architecture puts the buffer **in the interface**, which sounds simple but is actually a fundamental rethink of how streaming I/O should work in a systems programming language. It also happens to be a prerequisite for bringing back async/await, which - and I cannot stress this enough - was **previously existed in early Zig builds, got removed, and is now being reinstated** because the I/O infrastructure needed to support it properly didn't exist until now.

The release notes for 0.15.1 literally include "Writergate" as one of three "scandals" in that release cycle, alongside bounded array removal and managed ArrayList deprecation. The Zig team is **marketing their own breaking changes as scandals**. I don't know whether to applaud or be concerned.

## The Apology That Was Worse Than the Crime

Kelley added this to the PR description:

> "These changes are extremely breaking. I am sorry for that, but I have carefully examined the situation and acquired confidence that this is the direction that Zig needs to go."

That's it. That's the apology. "I am sorry for that" is basically "thoughts and prayers" for your broken build system. And then he just... merged it. Right after. No vote. No community process. Just a dude with commit access deciding that the entire I/O stack needed to die for the good of the project.

But here's the catch - and this is what makes Zig both infuriating and compelling - he was _right_. The new writer IS faster. The new design IS cleaner. It DOES enable async/await. And Bun, Ghostty, and TigerBeetle - three of the most ambitious real-world projects built in Zig - all survived. TigerBeetle's maintainer literally said they "didn't feel the pain of those breaking changes" because they don't have dependencies and wrote their own standard library subsets anyway.

That tells you everything about who Zig is for: people building shit so ambitious they need a language that will make the hard calls instead of letting technical debt accumulate. And people who freak out about backward compatibility? They're not wrong to do so - but they're also not the target audience. Not yet.

## The -Gate Naming Convention Is Unhinged and I Love It

Let me get this straight: there's been Allocgate (allocator changes), Writergate (this one), and now apparently every major breaking change gets a -gate suffix because programmers are obsessed with political scandals. We're reaching Critical Drinkere levels of discourse. Someone's going to do a Memory Safetygate in a few years and I'm genuinely looking forward to it.

What's beautiful is that this is peak programmer drama energy. No marketing team would ever approve "Writergate" as a product name. It sounds like a midlife crisis. It sounds like a scandal. It sounds like something you'd hear about in a congressional hearing. And Andrew Kelley merged it anyway because he genuinely doesn't give a shit what anyone thinks, as long as the technical outcome is correct.

This is the same guy who said the original async/await implementation was "wrong" and removed it instead of supporting it. The same guy who recently blew up 250 C source files in favor of Zig-idiomatic standard library wrappers. The same guy who left GitHub because the CI was broken and Microsoft's AI obsession was "ruining the service." This is not a person who seeks consensus. This is a person who calculates the correct technical answer and then forces the world to conform to it.

## The Community Fracture Is Almost Worth It

The Hacker News thread on this is a masterpiece. You've got people saying this is exactly why they'll never touch Zig ("version 0.14 has breaking changes, UNACCEPTABLE"), and you've got people from TigerBeetle saying this is "the right choice for a database, it would have been a worse database in any other language." These are both valid positions. That's what's wild.

People who want stability - and I understand this, I really do - have every right to be frustrated. You learn Zig, you build something, and six months later your code doesn't compile because someone decided the old I/O design was technically incorrect. It doesn't matter that the migration path exists (there's a polyfill!), it doesn't matter that the new API is better. The **emotional** cost of watching your code break is real, and dismissing it as "you're just not serious about software" is cope.

But Zig's position is: we're going to 1.0, and we want to get it right. Not "mostly right." Not "good enough for government work." **Right**. That means making hard calls now instead of accumulating technical debt that future maintainers will curse. It means accepting that some users will leave. It means betting that the people who stay will build things that couldn't exist in more "stable" languages.

## The Async/Await Prize

Here's why this matters long-term: async/await is coming back. Actually coming back. Not a hack, not an approximation, but a first-class language feature built on I/O as an interface, which requires the old streaming architecture to die first.

Zig removed async/await in early development because it was wrong. Not "slightly suboptimal." **Wrong**. It was implemented as stackless coroutines/generators that rewrote function logic at compile time, which is apparently a nightmare to get right across all architectures. The new approach - which Writergate enables - is fundamentally different and actually supports the abstractions people need for high-performance I/O.

So when people complain about breaking changes, the counterargument is: this is the tax you pay for getting to use a language that's actively being designed, not merely maintained. Rust changed async/await too, but they did it behind a compiler flag and pretended it wasn't a big deal. Zig does it in public, apologizes, and merges anyway. Both are valid strategies. Zig's is just more honest about the cost.

## I'm Not Saying Zig Is For Everyone

Let me be clear: if you're building something where you need your code to work for the next decade without touching it, **do not use Zig**. Use Rust. Use Go. Use C if you're insane. Use something with a stability guarantee, because you've got real problems and real timelines and you don't have time to chase Andrew Kelley's latest architectural epiphany.

But if you're building Bun - a whole JavaScript runtime from scratch - or Ghostty - the fastest terminal emulator I've ever used - or TigerBeetle - a database with a thousand-year roadmap - then you need a language where someone is willing to make the hard calls. You're not building something that needs to work in ten years. You're building something that needs to be **right**, and you need a language that will change to get there.

Zig is either the best programming language for ambitious projects or the worst programming language for anyone with a pulse. It's almost certainly both. Writergate didn't change that. It just proved it.

Now if you'll excuse me, I need to go check if my last Zig project still compiles. It was written in 0.14. We're on 0.16 now. Wish me luck.
