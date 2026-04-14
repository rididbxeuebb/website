+++
title = "TypeScript 7.0 Is Being Written in Go, and Microsoft Just Dumped Your 500 Unmerged PRs Into the Trash ⁶🤷⁷"
date = 2026-04-10T12:00:00Z
description = 'Microsoft just announced TypeScript is getting rewritten in Go. Thousands of community PRs are dead. The JS codebase is now legacy. What the actual hell is happening?'
+++

Microsoft just dropped a nuclear bomb on the TypeScript community, and nobody seems to be screaming loud enough. Let me say it again, slowly, so it sinks in: Microsoft is rewriting TypeScript in Go. Not TypeScript 7.0. Not some experimental branch. The entire future of the language is being ported from JavaScript to Go, and your contributions — your weeks, your months, your carefully crafted pull requests — are now worth precisely goddamn nothing.

I need to unpack this because the implications are absolutely staggering, and the response I've seen is way too goddamn calm.

## The Announcement That Should Have Started a Riot

On January 8th, 2026, Microsoft quietly posted what they're calling a "bridge release" — TypeScript 6.0. The blog post reads like a breakup letter written by someone who doesn't have the balls to say the actual words. Let me quote the relevant bit:

> "TypeScript 7.0+ is the future of TypeScript development and we want to ensure we're doing everything we can to focus on that goal. The native rewrite in Go represents an unavoidable discontinuity in development."

Unavoidable discontinuity. Let me translate that for you into human language: "We spent twenty years building this thing in JavaScript, and now we're starting over in a completely different language, and we're not even going to pretend to care about the migration."

But here's where it gets really spicy. Microsoft basically came out and said: "Yeah, so, almost all of your open pull requests against the JavaScript codebase? We're not merging those. Actually, we're going to automatically close them in the coming weeks. Thanks for playing."

THOUSANDS of community PRs. Years of work from volunteers who cared enough about this language to spend their free time improving it. Gone. Not merged. Not ported. Just... closed. Like they never existed.

## Why Go, Though? WHY?

This is the part that keeps me up at night. Why the actual hell is Microsoft rewriting TypeScript in Go?

Let me think about this. TypeScript is, itself, a superset of JavaScript. It compiles TO JavaScript. The entire toolchain — the compiler, the language server, the whole goddamn ecosystem — was written in TypeScript/JavaScript. It was literally eating its own dog food in the most meta way possible.

And now they're like, "Actually, nah, we're going to write the next version in Go."

I can hear the justifications already. "Go is faster." "Go has better build times." "Go has better tooling for large codebases." Blah blah blah. And you know what? Those might even be valid points. Go IS faster. Go DOES have better compilation speeds for massive projects. I get it.

But here's what nobody seems to be asking: if Go is so much better for building a compiler, why did Microsoft spend twenty years building the original in JavaScript? Was that just a happy little accident? Or did they genuinely believe JavaScript was the right tool, and now they've done a complete 180?

More importantly — and this is the part that makes me want to scream — what does this mean for the FUTURE of TypeScript? If Go was always the answer, why not just BUILD A NEW LANGUAGE in Go from scratch? Why call it TypeScript? Why not just say, "Hey, we're making a new thing called GoScript or TypeGo or whatever, and it's going to be a spiritual successor to TypeScript?"

No. Instead, they kept the name. They kept the version numbers. They acted like this is a normal evolution. And then they told thousands of contributors that their work was now trash.

## The Community Is Losing Its Mind (But Not Enough)

I found a GitHub issue from January 8th — the day the announcement dropped — and the comments are wild. People are asking about WASM versions, about how this affects Monaco editor (you know, the thing that powers VS Code), about whether there will be any compatibility layer at all.

And Microsoft, in their infinite corporate wisdom, responded with: "WASM is definitely possible. The perf today is not super — about on par with the JS codebase."

So let me get this straight. They're rewriting the entire language in Go, but the WASM version — which is the only way this would run in a browser — is "not super" and "about on par" with what they already have? And this is supposed to be exciting?

The issue has 20 rocket emojis. TWENTY. Do you know how sad that is? That's the TypeScript community basically saying, "Well, I guess this is happening, and we're just going to accept it and hope for the best."

## Here's What Actually Matters

Let me break down the real consequences of this disaster:

First, every single TypeScript maintainer of every single ecosystem tool is now facing a massive migration burden. ESLint plugins, type checking libraries, build tools, testing frameworks — all of them were built against the TypeScript compiler's internal APIs. Those APIs are about to CHANGE COMPLETELY. The language service, the AST structures, the whole underlying architecture — all of it is getting rewritten. Every single TypeScript-related library out there is going to break, and maintainers are going to have to learn Go to fix them.

Second, thousands of open source contributions are being literally deleted. Microsoft is closing PRs en masse because they can't — or won't — port them to the Go codebase. This is a signal to every single open source contributor: your work is disposable. It can be discarded the moment the company decides to change direction. The trust damage here is incalculable.

Third, the entire concept of "TypeScript as a platform" is now on extremely shaky ground. People have built businesses, tools, and entire careers around the TypeScript compiler's internal APIs. Now those APIs are going away. The message is clear: the TypeScript you know and love is legacy now. The new version won't be written by the same people, won't use the same code, and won't give a damn about your existing tooling.

## The Irony Is Delicious

You know what's funny? One of the biggest arguments for using TypeScript in the first place was that it was "JavaScript that scales." The language that was supposed to make large codebases manageable is itself being abandoned in favor of a language that, presumably, scales better.

And the kicker? Go has generics now, but they're still pretty basic. TypeScript's type system is light years ahead of Go's. Microsoft is literally downgrading the type system as part of this "upgrade."

Some users in that GitHub issue are already asking: "Will TypeScript 7.0 even have the same type inference capabilities?" And Microsoft hasn't answered. They just said "we want to focus on that goal" and moved on. This is the most hand-wavey disaster announcement I've ever seen, and I've watched plenty of companies tank their own products.

## What You Should Actually Do

If you're maintaining a TypeScript-related library, you need to start planning NOW. This is your warning. The 6.0 release is the last one on the JavaScript codebase, and after that, the Go rewrite takes over. Your tools WILL break, and you have maybe a year to figure out how to migrate.

If you're a contributor who has open PRs — especially ones that have been waiting for months — you need to accept that they're probably not getting merged. Start documenting your changes. Fork the JavaScript version if you care that much. Or just walk away and let Microsoft eat their Go-shaped meal alone.

And if you're starting a new project in 2026? Maybe think twice about betting everything on TypeScript. The language that was supposed to be stable, predictable, and forever is now a ticking time bomb of rewrite-induced chaos. The "upgrade path" to 7.0 is going to be a nightmare, and nobody at Microsoft seems to have a plan for it.

## The Final Word

This is the biggest self-inflicted wound in the history of TypeScript. Microsoft took a language that worked, that had a massive ecosystem, that developers genuinely loved, and they decided to rewrite it in a completely different language — without any clear plan for migration, without any respect for community contributions, and without any explanation for WHY they chose this path.

And the worst part? Everyone's just accepting it. There's no riot. There's no mass exodus to Rust or OCaml or whatever. There's just... 20 rocket emojis on a GitHub issue and a quiet acceptance that the language we all built together is now being thrown in the garbage.

I'm not saying TypeScript is dead. It's not. It's going to survive, probably in some form. But the TypeScript we knew — the one built by the community, improved by thousands of contributors, and cherished by millions of developers — that version died on January 8th, 2026, when Microsoft decided Go was the answer.

The question is: are you going to stick around for whatever comes next, or are you going to find something that actually gives a damn about backward compatibility?

Choose wisely. Because Microsoft sure as hell didn't.

```
⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⡿⠿⢛⣛⣩⣭⣭⣭⣭⣙⣩⣭⣭⣭⣭⣙⣛⠻⢿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿
⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⡿⠟⣋⣵⣶⣿⣿⣿⣿⣿⠿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⡷⣦⣙⠻⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿
⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⡿⢋⣴⣿⣿⡟⡿⢻⣿⣿⡟⣿⠸⣿⡙⣿⣿⣇⢻⣿⣿⣿⣿⣿⣷⣍⡻⣷⣬⡻⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿
⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⡿⢣⣶⢿⡿⢋⠍⢰⠃⣾⣿⣿⢡⣿⡆⢿⣧⠹⣿⣿⣆⢻⣿⣿⣿⣿⣿⣿⣿⣦⡹⣷⣌⠻⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿
⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⠏⣴⡿⡡⠋⡴⢣⠢⠃⣼⣿⣿⢃⣾⣿⡇⣌⠻⣷⡈⠻⢿⣦⡙⢿⣿⣿⣿⣿⣿⣿⣷⣌⢿⣷⡜⢿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿
⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⢋⣼⡟⠁⠄⣨⠞⡁⢀⣾⣿⡿⢃⣾⣿⢏⣴⣿⣷⣮⣙⡂⠄⠨⢙⡂⠙⠻⢿⣿⣿⣿⣿⣿⣧⡙⢿⣆⢻⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿
⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⡟⣸⣿⠃⣴⣶⣿⠖⣣⣾⣿⠟⣡⡾⠟⣫⣼⣿⣿⣿⣿⣿⣷⣶⣤⣼⣷⣶⣦⣬⣙⡻⢿⣿⣿⣿⣷⣜⠿⣎⢻⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿
⣿⣿⣿⣿⣿⣿⣿⣿⣿⡿⢠⣿⣯⣼⡿⢟⣡⣾⠿⢛⣡⣤⣴⣶⣿⣿⣿⣿⣿⣿⣿⣿⢿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣷⣬⡙⣿⣿⣿⣷⣶⣆⠹⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿
⣿⣿⣿⣿⣿⣿⣿⣿⣿⠃⣾⣿⣿⣦⣤⣤⢀⣶⣾⢛⡭⠐⠒⠒⠬⡛⢿⣿⣿⢸⣿⣿⡌⣿⣿⡿⢋⠅⠒⠐⠒⢬⡝⢿⣷⡘⣿⣿⣿⣿⣿⣷⡜⢿⣿⣿⣿⣿⣿⣿⣿⣿⣿
⣿⣿⣿⣿⣿⣿⣿⣿⣿⢸⣿⣿⣿⣿⣿⢃⣾⣿⡡⡏⠀⠐⠀⠂⠀⣈⣼⣿⡇⢾⣿⣿⡆⢿⣿⣧⣀⠀⠰⠠⠅⠀⢹⡎⣿⣷⡘⣿⣿⣿⣿⣿⡿⠷⠬⢙⢻⢿⣿⣿⣿⣿⣿
⣿⣿⣿⣿⣿⣿⣿⣿⣿⢸⣿⣿⣿⣿⡏⣼⣿⣿⣿⡿⠶⠶⠶⢞⣫⣼⣿⠟⣡⣭⣶⣦⣽⣌⠻⣿⣦⣙⡲⠶⠶⠶⢿⣿⣿⣿⣧⠸⣿⣿⣿⣿⣿⣦⣤⣭⡭⢀⣿⣿⣿⣿⣿
⣿⣿⡟⢻⣿⣿⣿⣿⡏⣸⣿⣿⣿⡿⢠⣿⣿⣿⣿⣿⣿⣿⣿⣿⠟⢋⣴⡿⠓⠹⣿⡏⠙⠿⢷⣎⢻⡻⣿⣿⣿⣿⣿⣿⣿⣿⣿⡆⢻⣿⣿⣿⣿⣿⡟⢉⣒⡁⣼⣿⣿⣿⡿
⣿⣿⣷⠠⣉⡛⠿⢛⣠⣿⣿⣿⣿⡇⣿⣿⣿⣿⣿⣿⣿⡿⢋⣵⣿⣦⣛⣠⣴⣾⣿⣷⣶⣤⣛⣛⣼⣿⣦⣙⢿⣿⣿⣿⣿⣿⣿⣷⢸⣿⣿⣿⣿⣿⣿⣿⡿⢡⣿⣿⣿⡿⠞
⣿⠋⢛⠷⠍⠛⢻⣿⣿⣿⣿⣿⣿⢰⣿⣿⣿⣿⣿⡿⣫⣶⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣷⣍⢻⣿⣿⣿⣿⣿⢸⣿⣿⣿⣿⣿⣿⡿⣡⣾⣿⣿⣿⣿⡌
⣿⠀⠦⡻⢿⣿⣿⣿⣿⣿⣿⣿⣟⢸⣿⣿⣿⣿⢏⣴⣿⣿⣿⠿⠟⠛⣛⡛⠉⠉⣉⠉⠉⢛⣛⠛⡛⠿⠿⣿⣿⣿⣷⡹⣿⣿⣿⣿⢸⣿⣿⣿⣿⠟⣫⠴⠟⣻⣿⣿⣿⡿⠁
⣿⣆⠳⣦⣤⣽⣿⣿⣿⣿⣿⣿⣗⢸⣿⣿⣿⠇⣾⣿⡟⠋⠀⣬⢡⣶⣎⣰⣿⣿⣀⣾⣿⣷⣱⣶⡎⣥⡔⡂⢍⢿⣿⣷⢹⣿⣿⡟⢸⣿⣿⠿⣷⡶⠖⣫⣴⣿⡿⠏⠁⠀⠒
⣿⣿⠣⠜⠻⢿⣿⣿⣿⣿⣿⣿⣿⠸⣿⣿⡏⢸⣿⡏⢠⢸⢇⣿⢻⣿⣿⣿⣿⣿⡛⣿⣿⣿⢿⣿⠿⣿⣇⣿⢈⠂⢹⣿⡌⣿⣿⡇⣿⡿⠛⠦⠄⣀⣿⡿⠉⠁⠀⠀⠀⠀⠀
⣿⣿⣷⣬⡐⠻⢿⢿⣿⣿⣿⣿⣿⡆⢻⣿⣿⢸⣿⠀⢆⢆⠣⠍⠀⠀⠀⠈⠉⠀⠀⠀⠀⠀⠀⠀⠀⠀⢒⣋⠟⡄⠈⣿⡇⣿⡿⢰⡿⢁⣶⣤⣍⠻⠁⠀⠀⠀⠀⣀⣠⣀⣀
⣿⣿⣿⣿⣷⣀⠨⢼⣿⣿⣿⣿⣿⣧⠸⣿⣿⢸⣿⠀⠘⠊⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠈⠉⠐⠁⠀⣿⢣⣿⠇⡼⢃⣼⣿⣿⣿⣦⡐⢶⣶⣴⣶⣿⣿⣿⣿
⣿⣿⣿⣿⣿⣿⣷⣶⣤⣭⣭⣄⠙⢿⣆⢻⣿⡌⣿⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⣯⣼⡿⢀⣴⣿⣿⣿⣿⡏⢿⣷⣄⡙⢾⣿⣿⣿⣿⣿
⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⠟⢠⡆⢲⣬⡈⣿⣿⣿⡄⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⢸⣿⣿⡇⣾⣿⣿⣿⣿⣿⣿⢸⣿⣿⣿⡄⢿⣿⣿⣿⣿
⣿⣿⣿⣿⣿⣿⣿⣿⠟⣠⣾⣿⣷⠸⣿⡇⢻⣿⣿⡇⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⣸⣿⣿⢠⣿⣿⣿⣿⣿⣿⡏⣼⣿⣿⣿⡇⠸⣿⣿⣿⣿
⣿⣿⣿⣿⣿⣿⡿⠛⠰⣿⣿⣿⣿⣆⢹⣿⠸⣿⣿⣿⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⣿⣿⡟⣸⣿⣿⣿⣿⣿⡟⣰⣿⣿⣿⡿⢁⣷⣤⡹⣿⣿
⣿⣿⣿⣿⡟⢉⣴⣾⣆⠹⣿⣿⣿⣿⣆⠻⡆⣿⣿⣿⡄⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⢠⣿⣿⠇⣿⣿⣿⣿⡿⢋⣴⣿⣿⣿⠟⣠⣾⣿⣿⣷⡌⢿
⣿⣿⣿⠋⣴⣿⣿⣿⣿⣷⡈⠻⣿⣿⣿⣿⣧⢸⣿⣿⡇⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⢸⣿⣿⢰⣿⣿⣿⣿⣷⣿⣿⣿⡿⢃⣴⣿⣿⣿⣿⣿⣿⡌
⣿⣿⢃⣾⣿⣿⣿⣿⣿⣿⣿⣦⡈⠻⣿⣿⣿⡈⣿⣿⣧⢠⢤⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠴⠆⣾⣿⡏⣸⣿⣿⣿⣿⣿⣿⡿⢋⣴⣿⣿⣿⣿⣿⣿⣿⣿⣿
⣿⠇⣾⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣶⣌⠻⢿⡇⢿⣿⣿⠰⢿⡂⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⢀⣿⠇⣿⣿⡇⣿⣿⣿⣿⣿⡿⢋⣴⣾⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿
⡿⢸⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣷⣶⣦⢸⣿⣿⡄⢿⣟⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⣛⠻⢸⣿⣿⢁⣿⣿⣿⠟⣁⣴⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿
⡇⣾⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⡀⣿⣿⣇⠙⣫⣤⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠸⠿⡇⣸⣿⡟⢸⠿⢋⣥⣾⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿
⠇⣿⣿⣿⣿⣿⣆⠸⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⡇⢻⣿⣿⡄⠿⣯⡄⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⡻⣿⢀⣿⣿⡏⣠⣾⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿
⠀⣿⣿⣿⣿⣿⣿⡀⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣷⢸⣿⣿⣇⢰⣿⢗⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⢴⣧⠙⢸⣿⣿⠃⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿
⠰⣿⣿⣿⣿⣿⣿⣧⠸⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⡈⣿⣿⣿⣆⢣⣿⢃⡀⠀⠀⠀⠀⠀⠀⣀⢰⣧⠻⢡⣿⣿⣿⢰⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿
⠘⣿⣿⣿⣿⣿⣿⣿⡆⢻⣿⣿⣿⣿⣿⣿⣿⣿⣿⡇⢿⣿⣯⠻⣦⠉⢿⡇⣿⡷⣶⢲⣿⡞⣿⠺⠟⣠⢿⣿⣿⡇⣸⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿
⠈⣿⣿⣿⣿⣿⣿⣿⣿⡄⢻⣿⣿⣿⣿⣿⣿⣿⣿⣿⠸⣿⣿⣷⡙⢷⣦⣔⣈⠉⠛⠩⠛⢁⣉⣴⡾⢋⣼⣿⣟⢀⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿
⡄⣿⣿⣿⣿⣿⣿⣿⣿⣿⡄⢿⣿⣿⣿⣿⣿⣿⣿⣿⡆⢻⣿⣿⣿⣷⣭⣛⠻⠿⠿⠿⠿⠿⢛⣫⣴⣿⣿⣿⠇⣼⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿
⡇⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⡄⠹⣿⣿⣿⣿⣿⣿⣿⣿⡌⠿⣿⣿⣿⣿⣿⡿⣿⣿⣿⣿⢿⢿⣿⣿⣿⡿⠏⣼⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿
```
