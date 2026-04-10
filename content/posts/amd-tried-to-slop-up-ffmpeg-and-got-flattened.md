---
title: 'AMD Tried To Slop Up FFmpeg And Got Absolutely Flattened'
date: 2026-04-10
description: 'The absolute state of corporate open source contributions in 2026: AMD submits verbose, redundant, AI-slop-emoji-looking code to FFmpeg, gets publicly roasted by maintainers, and Vulkan exists you idiots.'
---

I genuinely cannot believe we're having this conversation in 2026, but here we are: a multi-billion dollar semiconductor company tried to submit code to FFmpeg and got dragged so hard on Twitter that their intern could feel it from the server room. This is the kind of content that makes me believe we're living in a simulation designed to make me suffer.

## The Incident

So here's what happened. Some AMD contributor submitted a patch to FFmpeg that was supposed to add HIP (Heterogeneous-compute Interface for Portability) SDK support on Windows. You know, for GPU-accelerated video processing on AMD hardware. Sounds reasonable on paper, right? Wrong.

Within hours, FFmpeg maintainers absolutely eviscerated this thing. I'm talking full public execution. One developer, Zhao Zilli, basically said "please ensure a thorough manual review of all AI-generated code before wasting our time." Then another maintainer, quink_lamy, posted on X (formerly Twitter, and you know the relationship with that platform is complicated) with the absolute kill shot: "Hi @AMD. FFmpeg developer @quink_lamy is not happy with your AI slop patches."

That's not even the worst part. The AMD developer who submitted the patch _denied_ using AI, claiming their verbose, redundant, non-standard code was just "necessary steps" from their internal process. Brother. The cope is real.

## What Was Actually Wrong With The Patch

Let me break down why this got rejected because it's genuinely instructive for anyone who thinks "code is code":

First, the code was verbose as hell. We're talking unnecessary comments everywhere, structure sprawl that looked like someone fed "make this look like it was written by AI" into a prompt and just accepted the output. FFmpeg maintainers aren't stupid - they've been reviewing patches for decades. They know what AI-generated code looks like the way your mom knows when you're lying about where you were last night.

Second, and this is the part that makes me want to put my head through a wall, **AMD already has GPU support in FFmpeg through Vulkan**. The HIP SDK on Windows was completely redundant. It's like showing up to a potluck with a bag of ice when there's already a freezer full of food. Actually, worse - it's like bringing a bag of ice and insisting it's better than the freezer when you're literally standing in front of the freezer.

Third, the optimization was weak. Not just "slightly subpar" but genuinely garbage compared to what already existed. This is the equivalent of bringing a knife to a gunfight and then being confused when you get shot.

## The Wider Pattern

This isn't an isolated incident, and that's what makes it so frustrating. We're seeing more and more corporate contributions that look like they went through zero human review before being submitted. Companies seem to think open source maintainers are just gonna accept whatever slop they produce because apparently having your code in a big-name project is worth more than having _good_ code in a big-name project.

FFmpeg is one of the most critical pieces of infrastructure in the entire software ecosystem. It powers Chrome, Firefox, VLC, OBS Studio, Handbrake, YouTube - basically anything that processes video relies on FFmpeg at some point in the chain. The maintainers deal with security vulnerabilities reported by trillion-dollar companies and get blamed when they're not fixed fast enough. They're volunteers. _Volunteers_. Let that sink in.

Then AMD shows up with their "AI slop patches" (the quotes are staying, I don't care if the submitter denies it, the code speaks for itself) and expects a warm welcome? Get out of here.

## What AMD Should Have Done

Here's a radical idea for any corporation wanting to contribute to open source: actually talk to the maintainers _before_ spending engineering resources on a patch that might not even be needed. Join the mailing list, explain what you're trying to achieve, ask if there's already a better way. This is kindergarten-level stuff and somehow it keeps escaping people who make hundreds of billions of dollars a year.

Also maybe, and this is just a suggestion, run your patch by someone who isn't the same model that generated it before submission. I know that's wild. I know "have a human review the code" sounds like science fiction in 2026. But apparently FFmpeg expects this and honestly, so should you.

## The Aftermath

As of now, the patch was rejected on technical grounds. AMD supposedly reached out to clarify, but I'm not holding my breath for a fixed submission. The whole thing should serve as a warning: open source community trust is built over decades and burned in seconds. Maybe next time AMD will actually read the room before submitting.

Or maybe they'll just spawn another AI to write a more convincing patch. At this point, genuinely don't know which is worse.

Either way, FFmpeg maintainers did everyone a favor by drawing a hard line. This is what community governance looks like when it works. Not corporate lawyers, not corporate PR, just developers saying "this code is garbage, fix it or gtfo."

More projects need that energy. You should try it sometime.
