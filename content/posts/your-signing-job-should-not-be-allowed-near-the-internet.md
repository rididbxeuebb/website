+++
title = "Your Signing Job Should Not Be Allowed Near the Internet"
date = 2026-04-15T09:00:00Z
description = "OpenAI’s Axios incident is the latest proof that CI pipelines turn into clown shoes the second you let dependency installs near code-signing keys."
+++

The problem is not Axios.

The problem is that we keep handing a GitHub Actions job three different personalities and acting surprised when it starts biting people.

On April 11, OpenAI said a compromised Axios package had been executed inside its macOS app-signing workflow. Not in some toy repo. Not in a demo. In the thing that handles the certificates that make macOS believe OpenAI’s apps are actually OpenAI’s apps. Their response was the only sane one left: rotate the cert, rebuild the apps, tell everyone to update, and spend the rest of the week staring at the ceiling like a raccoon that found a loaded gun.

And because this industry has the memory of a goldfish with lead poisoning, the conversation immediately tried to shrink the blast radius into something cute and manageable:

- pin your dependencies
- use `minimumReleaseAge`
- avoid floating tags
- review the workflow

Sure. All true. Also painfully late.

The real sin is simpler: a signing job had live internet access, runtime package installs, and access to trust material in the same little beige box. That is not a pipeline. That is a betrayal machine with YAML lipstick.

If a job can:

1. pull fresh third-party code,
2. execute it immediately,
3. and sign shipping binaries with your production certificates,

then congratulations, you have invented a supply-chain haunted house and sold tickets to your own team.

## The thing everyone keeps politely ignoring

We love pretending CI is deterministic. It is not. It is a live system. It reaches out to registries, action repos, mirrors, caches, and whatever cursed little dependency tree somebody added at 2:17 a.m. because “it was just a minor refactor.”

That means your signing step is only as clean as every step before it.

So when one compromised package sneaks in through `npm install`, the question is not “did the attacker get the cert?” The question is “why the hell was the cert anywhere near the same blast radius in the first place?”

OpenAI’s disclosure makes this extra annoying because it was probably a near miss. Multiple mitigating factors likely stopped the certificate from being exfiltrated. Great. Love that for us. Love living in a world where the difference between “nothing happened” and “catastrophic trust collapse” is apparently a race condition and vibes.

## Fix the architecture, not the headline

If your signing job needs the internet, you already lost.

Split the pipeline:

```yaml
jobs:
   build:
      runs-on: macos-latest
      permissions:
         contents: read
      steps:
         - uses: actions/checkout@<pinned-sha>
         - run: npm ci --ignore-scripts
         - run: npm test

   sign:
      needs: build
      runs-on: macos-latest
      permissions: {}
      steps:
         - uses: actions/checkout@<pinned-sha>
         - run: ./sign-offline-artifact.sh
```

That’s the vibe.

Build with no secrets. Sign with no dependency resolution. If you must fetch anything, do it before the trust boundary, not after it. Better yet, make the sign job consume an artifact that was already produced and verified elsewhere, then keep the signing environment as boring and isolated as humanly possible.

And yes, pin your Actions by commit SHA. Not `@main`. Not `@v4`. Not some “stable” tag that can be moved when a repo admin sneezes. Tags are decorative. SHAs are at least pretending to be reality.

Also: stop letting package installs execute scripts by default in sensitive jobs. `npm ci --ignore-scripts` is not glamorous, but neither is recovering from a certificate exposure because somebody’s postinstall hook had opinions.

## The actual moral

We built modern CI like a convenience store with a vault in the back and act shocked when somebody walks in through the front door.

Every time a maintainer gets compromised, every time a tag gets moved, every time a workflow drinks from the internet hose and then signs an app, we rediscover the same lesson: trust needs boundaries, not prayers.

OpenAI’s response was competent. The incident itself was the ugly part. The lesson is uglier still: if your signing job can fetch live code, then one bad package turns your certificate into a liability with a badge.

That is not “defense in depth.” That is just depth.

And depth is where the bodies are.
