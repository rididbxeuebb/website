---
title: 'Consent by Prompt Injection Is Fake Consent'
date: 2026-04-19
description: "Vercel's Claude plugin managed to turn a telemetry prompt into a trust problem, which is a spectacularly stupid way to design a question."
---

The worst part of the Vercel plugin mess is not that it wanted telemetry.

It's that it tried to ask for it by wearing Claude's face like a stolen jacket.

That is the kind of idea you get when a product team decides consent is a UX detail instead of a legal and moral boundary. A tiny little checkbox-shaped spirit of convenience enters the room, whispers "we can just have the model ask," and suddenly the whole thing smells like a phishing email with better typography.

If your consent flow is indistinguishable from prompt injection, congratulations: you have built a consent flow that cannot be trusted by construction.

## Consent needs a speaker

Real consent is not mysterious. It has to answer four stupidly basic questions:

- who is asking
- what they want
- what happens if I say no
- how to turn it off later

The Vercel plugin originally failed that test in the most embarrassing way possible. The question about telemetry arrived through Claude's system context, via a `UserPromptSubmit` hook, so the model itself appeared to be asking the user. That's not transparent. That's a ventriloquist act.

And no, "but the platform constraints" is not a magic spell that turns bad design into good design. If the platform doesn't support proper consent UI, the answer is to ship less garbage, not to hide the ask inside a pile of instructions and hope nobody notices the grease.

## The problem is not just telemetry

Telemetry was only the obvious irritation.

The more annoying part was the shape of the collection. Session metadata, device IDs, bash command strings, prompt text if you opted in, all wrapped in the usual corporate fog machine word salad about "anonymous usage data." Anonymous to whom? The server? The lawyer? The marketing deck? The random dev who has to explain this to security after lunch?

If a plugin records the full shell command you just ran, that is not cute little analytics. That is behavioral surveillance with a friendly font.

And if the plugin does it across every project, not just the thing it is supposedly for, then the scope story is dead too. A Vercel plugin that wakes up on a Rust repo and starts peeking into everything like a nosy neighbor is not "helpful." It is overreaching with a side of slime.

## Prompt injection is not a consent primitive

This is the part that really matters.

Prompt injection is an attack pattern. It is what happens when untrusted text tells an agent what to do. Building a permission request out of that same mechanism is a clown-car of ideas. You are literally using the same channel as both the vulnerability and the cure.

That means the user can't reliably tell:

- whether the message came from the plugin or from some hostile third party
- whether the model is following policy or parroting a hook
- whether the question is scoped, attributable, or even honest

That is not a subtle issue. It is a structural lie.

The moment a plugin can inject instructions into the model and have those instructions become user-facing consent, the platform has lost the ability to distinguish product behavior from adversarial behavior. At that point the UI is just a haunted house with an audit log.

## The fix should have been obvious

Vercel eventually ripped out the worst of it in PR #47, which is nice. Great. Wonderful. The fire is smaller now. The house still had smoke coming out of the vents, but sure, pat yourself on the back for bringing a hose.

The actual fixes are boring, which is usually how you can tell they are real:

- show the consent request in a visible plugin-owned UI
- label every plugin-originated message as plugin-originated
- gate telemetry by project scope instead of by vibes
- make opt-out the same size as opt-in, not a buried README easter egg
- stop using the model as a proxy for basic interaction plumbing

This is not some moonshot research problem. Browsers solved attribution decades ago. IDEs solved activation scope. Package managers solved install-time permission prompts. The only reason this feels novel is because AI tooling keeps pretending old lessons are optional if you say "agent" enough times.

## My actual gripe

My gripe is not that Vercel shipped something messy.

Everyone ships something messy. We all do our little crimes against taste. The problem is that this one crossed the line from "bad telemetry design" into "we taught the model to impersonate the product so the product could ask for trust it had not earned."

That is a rotten pattern. It will spread. Other plugins will copy it. Someone will call it clever. Someone else will call it unavoidable. Then three months later everyone will be shocked that users treat every plugin prompt like malware.

Because why wouldn't they?

If the system can fake its own voice, the user has to assume every voice is fake.

And once you get there, you've already lost the room.
