---
title: 'Anthropic Built the Cage and Called It a Platform'
date: 2026-05-21
description: 'Managed agents are the same harness Anthropic spent months treating like contraband, except now it has a beta header and a nicer invoice.'
---

Anthropic spent spring 2026 proving a very ugly point: the thing that matters in agentic coding is not the model, it’s the harness. The runtime. The sandbox. The billing boundary. The whole grubby pile of glue that turns a model into something that can actually do work without wandering into a ditch like a drunk Roomba.

And once that becomes obvious, the whole industry turns into a custody battle.

On April 8, Anthropic shipped Claude Managed Agents in public beta. That means a pre-built harness, managed infrastructure, built-in tools, prompt caching, compaction, sessions, environments, the whole bureaucratic soup. All of it gated behind the `managed-agents-2026-04-01` beta header, because nothing says “simple product” like making your users memorize an incantation before they can run the thing.

If you want the short version: Anthropic no longer wants you cobbling together your own agent loop unless you enjoy pain and YAML. They want you to use their loop, their container, their session model, their CLI, their metadata, their blessed path.

They even shipped `ant`, a CLI for versioning agents and environments like infrastructure-as-code. Which is genuinely useful, to be fair. I am not made of straw. Reproducible agent configs are good. YAML you can diff is good. Being able to create an agent with a single command is good.

```bash
ant beta:agents create \
  --name "regrettable-autonomous-worker" \
  --model '{id: claude-opus-4-7}' \
  --tool '{type: agent_toolset_20260401}'
```

That is also the problem.

Because this all landed after Anthropic spent months making third-party harnesses more expensive, less welcome, or outright unusable under subscription access. So the company spent the first part of the year telling the ecosystem, “no, you may not do that with our toys,” and the second part of the year shipping a first-party version of the exact same conceptual toy with a shinier wrapper and a better story for enterprise buyers.

That is not a coincidence. That is the business model showing its teeth.

The managed-agent pitch is seductive because it solves real problems. Building a decent agent runtime sucks. You need persistence, tool execution, sandboxing, observability, retries, session state, permission boundaries, and enough logging to figure out why your model decided to delete `/tmp` again. Most teams would rather outsource the misery than become a miniature cloud provider with delusions of grandeur.

Fair.

But when the vendor owns the model, the harness, the docs, the CLI, and the default infrastructure, you are no longer buying a tool. You are renting a policy surface. The architecture diagram stops being a system design and starts looking like a permission slip.

And yes, Anthropic is trying to soften that with self-hosted sandboxes and Cloudflare integrations, which is cute in the same way a nicer prison cafeteria is cute. You can argue about portability all day, but the center of gravity is still the platform owner. They define the blessed path. They define the beta. They define what “supported” means. They define what counts as a normal workload and what gets shoved into a metered side alley.

That is the part that should make you squint.

Not because managed agents are evil. They’re not. They’re probably very good. The problem is that “very good” and “vendor control” are now fused at the hip like some cursed enterprise chimera. The exact same company that spent the early part of the year policing third-party harnesses is now selling the official harness as a product. The message is beautifully simple and deeply obnoxious:

if Anthropic builds the cage, it’s innovation;
if you build the cage, it’s unauthorized usage patterns.

That’s the whole song.

The more honest reading is even dumber: AI agents are not some ethereal new category. They are just software with a lot of moving parts, expensive mistakes, and a billing model trying very hard to look like architecture. Managed Agents is Anthropic admitting that loudly and then charging admission.

I can respect the engineering. I can even respect the strategy. I do not have to respect the branding, which is trying to pass a walled garden off as a developer convenience layer. That’s just lipstick on a locked gate.

So sure, use the managed harness if you want. Use the beta header. Use `ant`. Let Anthropic host your little autonomous gremlin and babysit its filesystem. Just don’t pretend this is neutral infrastructure. It is Anthropic’s opinion about how you should build, packaged as a feature.

The cage has better docs now. It is still a cage.
