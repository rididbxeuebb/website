+++
title = "Anthropic Just Declared War on Open Source. Here's Why You Should Give a Shit."
date = 2026-03-27T12:00:00Z
description = 'The company that built its brand on ethics just pulled the nastiest move of 2026 — and somehow DHH is the voice of reason.'
+++

Anthropic — you know, the company that positioned itself as the "ethical AI" alternative to OpenAI, the one that talked so goddamn much about safety and responsibility — just locked out every open-source coding tool from accessing Claude models. And they did it in the sneakiest, most cowardly way possible.

Let me lay out what happened.

## The Setup

OpenCode is an open-source AI coding agent that supports 75+ model providers. It's MIT-licensed, it's growing like wildfire (hit 100K GitHub stars in like six months), and it's basically the anti-C Claude Code — you know, the tool where you're locked into whatever model Anthropic decides to give you.

The problem? OpenCode let users connect their Claude Max subscriptions ($200/month) through OAuth. Not API keys — subscriptions. And here's where it gets spicy: people figured out this adorable little technique called "Ralph Wiggum" — basically stuffing Claude into an infinite loop, letting it autonomously write and rewrite code until every test passed. One developer allegedly completed a $50,000 contract for under $300 in subscription costs.

Anthropic was NOT thrilled about this. Their servers were getting absolutely hammered by people essentially running unlimited agent workloads on fixed-price subscriptions. The economics were broken.

## The Lockout

On January 9, 2026, at 2:20 AM UTC — because nothing says "we care about transparency" like doing this at 2 AM — Anthropic flipped the switch. All unofficial OAuth access was blocked. No warning. No announcement. Just a quiet flip of the kill switch.

But here's the part that really pisses me off: they claimed this wasn't a new policy. They said they were just "enforcing existing terms." Section 3.7 of their Consumer ToS, they claimed, already prohibited this. Except the way OpenCode was accessing Claude wasn't exactly violating anything clear — they were spoofing Claude Code's HTTP headers to make their requests look like they came from the official CLI. That's the technically questionable part, sure.

But the response? The RESPONSE is what matters.

OpenCode removed every line of Claude-related code on February 19, 2026. Commit `973715f`. Gone. The Anthropic auth plugin? Deleted. The Claude-specific prompt file? Gone. All of it, ripped out because Anthropic sent them legal documents.

## The Irony Is almost Too Perfect

Let me get this straight: Anthropic trained Claude on open-source code from the internet — code that developers like you and me wrote, contributed to, maintained for free. We built the training data. And now they're blocking open-source tools from accessing the models that were trained on our work.

DHH (Ruby on Rails creator) posted about this and said it directly: "Terrible policy for a company built on training models on our code, our writing, our everything."

And he's right. This is the most hypocrisy-filled move in AI this year, and that's saying something because the AI space is basically a minefield of stupid decisions.

George Hotz — yeah, THE George Hotz — called them out. He predicted this wouldn't drive users back to Claude Code. Instead, it would "convert people to other model providers." And he was right. Within weeks, OpenAI made a big show of allowing their Codex subscriptions to work in OpenCode and other open-source tools. Google Gemini does the same.

So now we have a clear divide: OpenAI and Google are the "open" ones, and Anthropic is the walled garden. Sound familiar? It's iOS vs Android all over again, except instead of phones, it's about which AI model gets to control your development environment.

## The Numbers Don't Lie

Here's what really gets me: Claude's market share in consumer chatbots is less than 2%. TWO PERCENT. They have the best coding benchmarks (SWE-bench Verified at 80.9%), they're supposedly the "ethical" choice, and yet almost nobody uses them. And their response to this was to make their ecosystem EVEN MORE closed?

That's not a moat. That's a tomb.

The capability gap between models is shrinking fast. GPT-5.2 is at 80.0%, MiniMax M2.5 at 80.2%. Claude still leads, but the gap is closing. When the performance moat narrows, ecosystem openness becomes the deciding factor. And Anthropic is actively choosing to lose on that dimension.

## What This Means For You

If you're a developer paying $200/month for Claude Max, you now have exactly one choice: use Claude Code, or nothing else. You can't use it in OpenCode. You can't use it in Cursor. You can't use it in your own tools. You're locked into their interface, their workflow, their every decision.

If you want flexibility, you need to pay for API access separately. That's pay-per-use, which can add up fast if you're running those "Ralph Wiggum" agent loops.

Or you can switch to OpenCode, use your own API keys, and have actual freedom. Yeah, you might pay more per token. But you're not a prisoner.

## The Bigger Picture

This isn't about one company blocking one tool. This is about who controls your development environment. Anthropic is making a bet: they think their model quality is so far ahead that you'll tolerate their walled garden. They might be right — for now.

But here's what's going to happen: as the model quality gap closes, developers are going to choose the tools that let them work the way they want. They'll choose flexibility over lock-in. They'll choose open over closed. History has shown us how this plays out.

Anthropic just showed their hand. They don't trust developers. They don't trust open source. They want control.

And maybe — just maybe — the rest of us should think twice before building our workflows around a company that treats us like criminals for wanting to use their product the way we want.

The open alliance is forming. You can join it, or you can stay in the garden. But at least now you know what you're choosing.
