+++
title = "Chrome's Prompt API Is a Vendor Lock-In Machine in a Trench Coat"
date = 2026-05-01T12:00:00Z
description = "Google says the browser can talk to a local model now. Sure. And the model just happens to be Google's, the policy is Google's, and the compatibility problem is everybody else's."
+++

Chrome wants web pages to talk to a browser-provided language model now, which is either the future or a more expensive way to recreate browser sniffing with a smiley face.

Google’s Prompt API pitch is adorable in the way a live wire is adorable. The browser downloads Gemini Nano separately, wants roughly 22 GB of free space, checks whether your hardware is beefy enough, and only then lets a page ask for a session through `LanguageModel.create()`. If the model isn’t there yet, Chrome can spend time fetching it, extracting it, and stuffing it into memory like a raccoon hoarding shiny garbage.

Oh, and before you even get to play with the toy, you have to acknowledge Google’s generative AI policy. Because apparently “open web platform” now means “please agree to the house rules before the browser thinks for you.” Nothing screams neutrality like a terms-of-service checkpoint bolted onto an API that claims to be general-purpose.

Mozilla saw this and did the only sane thing: it complained about interoperability, updatability, and neutrality. Correct. Once developers start tuning prompts to Gemini Nano’s quirks, the standard stops being a standard and becomes a Chrome compatibility target. Then the rest of the web gets dragged into the usual mess: special cases, fallback paths, model-specific hacks, and the whole ugly zoo we spent decades pretending to outgrow.

This is the real problem, and it’s not subtle. A web API that depends on a particular vendor’s model is not just “client-side AI.” It is a distribution channel for vendor behavior. If Chrome ships one model, Edge ships another, and Firefox ships something else or nothing at all, then developers will optimize for whichever one is easiest to sell to management. That’s how de facto standards happen. Not through elegance. Through laziness and market gravity.

And yes, Google is wrapping the thing in nice technical clothing: structured output, session management, `promptStreaming()`, permission policy, all the little bureaucratic handles that make the feature sound civilized. Fine. Great. None of that changes the core issue. You can put a JSON Schema on the response and still end up with a platform that behaves differently depending on whose model happened to be bundled this quarter.

That’s not a web primitive. That’s a compatibility debt generator.

The browser used to be the place where you rendered HTML and got on with your miserable day. Now it’s expected to cache an LLM, police its allowed use, manage downloads, enforce policy, and decide which sites get to pretend the machine is thinking locally. That’s not a small extension of the browser’s job. That’s the browser quietly becoming a model runtime with a tab bar attached.

I can already see the future support thread in my head:

> “Why does this feature work in Chrome but fail in Firefox?”

Because Chrome happened to ship the model your prompt was tuned against, you beautiful idiot. Because the page now depends on a probabilistic assistant with a policy file, not a deterministic platform primitive. Because the new version of “works everywhere” is “works on the browser that also owns the model.”

And before somebody runs in waving the “local inference” flag like it’s a magic purity talisman: local is not the same as open. Local is not the same as neutral. Local is not the same as portable. If the browser vendor controls the model, the update cadence, the policy, the memory budget, and the default behavior, then the thing is still a product surface, just one with less obvious bandwidth bills.

This is how platform capture gets dressed up as convenience. First the feature is optional. Then it is “helpful.” Then the demos get better. Then the sites that matter start depending on it. Then every browser that doesn’t play along gets accused of being behind the curve, because apparently the curve is always wherever the biggest vendor feels like standing that morning.

So no, I am not dazzled.

I think the web should stay suspicious of APIs that require you to accept a vendor’s model, a vendor’s policy, and a vendor’s interpretation of “helpful” before the page can ask a question. If you want AI in your app, ship AI in your app. Don’t smuggle a corporate oracle into the browser and call it a standard.

The browser is already full of enough weirdness. It does not need a new priesthood.
