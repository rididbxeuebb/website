+++
title = "Cloudflare Dropped a CMS and It's Actually Interesting"
date = 2026-04-06T12:00:00Z
description = "EmDash is either the most important thing to happen to CMSes in a decade or a two-month fever dream held together by AI optimism. Let's talk about why both could be true."
+++

Cloudflare, of all companies, launched a CMS this week. Not a caching layer, not a DNS product, not another flavor of Workers — an actual, honest-to-god content management system called EmDash that aims to be the "WordPress spiritual successor." On April 1st, which fooled exactly no one because come on, this is Cloudflare.

And look, I've been burned by "WordPress killers" before. Every year some startup decides that the way to win is to build a better WordPress, and every year they discover that the plugin ecosystem is the moat, not the UI. Ghost tried it. Craft tried it. Statamic tried it. All excellent products, all still fighting for the scraps while WordPress chugs along at 40%+ market share like a cockroach that survived the apocalypse.

So my default position on EmDash should be skepticism. And don't worry, I'll get there. But here's the thing — I actually can't dismiss this one immediately, because there's something genuinely interesting happening under the hood that goes beyond "another headless CMS with a pretty admin panel."

## The Actually Interesting Part

The pitch is simple: built for AI agents. Not "has AI features," not "includes a chatbot," but designed from the ground up assuming that Claude or Cursor or whatever comes next is going to be a primary user of this system. The content lives as structured JSON, not HTML blobs. There's an MCP server so agents can programmatically create content types, manage entries, and deploy sites. The CLI outputs JSON. The documentation is apparently structured for machine consumption.

This is the part that made me actually stop and think, because it's not a feature you can bolt onto an existing CMS. You have to design for it from the start. WordPress wasn't built for AI agents — it was built for humans clicking buttons in 2003. You can add AI features on top, but the underlying architecture assumes a human is driving.

EmDash assumes the human is optional. And here's the thing — that might actually matter in 2026. Not because AI agents are building client sites today (they're not, mostly), but because the tooling is shifting. If your CMS is the bottleneck between "I told Claude what I want" and "there's a working website," you're about to have a problem. The AI can already write the code. The question is whether it can also manage the content.

## Two Months

They built this in two months. With AI coding agents. That's either the most impressive thing I've heard this year or the most terrifying, depending on how generous I'm feeling.

Because here's the uncomfortable truth: a CMS built in two months is not battle-tested. It's not been stretched across thousands of edge cases. It doesn't have the institutional knowledge that comes from twenty years of users reporting bugs, maintainers fixing security holes, and community members writing tests for things nobody thought to test. WordPress has all of that. WordPress is also a disaster of technical debt held together by the fact that it works and everyone knows how to fix it.

EmDash doesn't have that buffer. It looks clean. It looks modern. It's built on Astro, TypeScript throughout, SQLite locally, D1 in production. Beautiful. But has anyone tried to migrate a real site with 10,000 posts and 200 plugins to it? Has anyone stress-tested the plugin sandbox under load? Has anyone found the weird edge case where the edge deployment does something unexpected with caching?

We don't know. We can't know. Two months isn't enough time to find out.

## The Plugin Problem

Plugins made WordPress. That's not a controversial statement. WordPress has 60,000+ plugins because it was easy to build them, and the ecosystem exploded. But plugins are also the reason WordPress is a security nightmare — every plugin is a potential vulnerability, and most WordPress sites run outdated plugins with known CVEs.

EmDash's answer to this is sandboxing. Each plugin runs in an isolated worker with granular permissions. It has to explicitly request access to content, network calls, specific APIs. The UI is defined through JSON schema, so plugins can't inject arbitrary JavaScript into the admin panel. There's automated security scanning with Workers AI and Llama Guards.

This is a good idea. It's the right architectural decision. But here's the thing — the EmDash plugin marketplace is currently empty. They have the architecture for plugins, they have the security model, they even have guides for porting WordPress plugins. But nobody has built anything yet. And history suggests that CMS adoption is driven more by available plugins and themes than by technical merit.

So we have another chicken-and-egg problem: nobody will use EmDash because it doesn't have plugins, nobody will build plugins because there's no users. The sandboxed architecture is a great foundation, but it's not a solution.

## The Cloudflare Question

It's MIT licensed. That's good. But it's still a Cloudflare project. And Cloudflare has a pattern of launching interesting open-source projects and then... well, let's see how long they keep staffing it properly. Workers, Pages, D1, R2 — all solid. But EmDash is different because it's a CMS, which means long-term maintenance commitments, community management, and the kind of unglamorous work that doesn't get press releases.

I'm not saying Cloudflare will abandon it. I'm saying I'd want to see a governance model before I bet my client's site on it. Who's maintaining this in five years? What's the process for community contributions? What's the plan when a critical vulnerability is found?

The fact that it's MIT licensed means someone else could fork it if Cloudflare walks away. But good luck building a plugin ecosystem around a fork that doesn't have the company's backing.

## So Is It The Future Or Not

Here's my honest take: EmDash is asking the right question. The question isn't "how do we make a better WordPress?" The question is "what does a CMS look like when AI agents are doing the building?" That's a fundamentally different problem, and it's one that nobody else is addressing directly.

The answer might be EmDash. It might be something else. It might be that we don't actually need CMSes in five years because AI agents will just generate content on the fly and we'll store nothing. I have no idea.

But EmDash is the first thing I've seen that feels like it's designed for the world that's actually arriving, rather than the world that existed when WordPress was born. The two-month development time is a liability in terms of maturity, but it's also a demonstration of what's possible when you build on a modern stack without legacy constraints. The plugin ecosystem is empty, but the architecture is sound. The Cloudflare dependency is real, but the license is open.

I'm not going to migrate my blog this week. I'm not going to tell clients to abandon WordPress. But I'm going to watch this closely, because if the plugin situation gets resolved and the maintainers keep it updated, this could actually be the foundation for a generation of sites that are built by AI agents rather than humans clicking through admin panels.

The question is whether we're ready for that world, and whether EmDash is the right tool for it. My money says "maybe" on both counts, which is more enthusiasm than I've had for a new CMS in years.
