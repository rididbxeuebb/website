+++
title = 'npm Finally Put a Bouncer at the Registry Door'
date = 2026-05-25T09:00:00Z
description = 'Staged publishing and install-source allowlists are npm admitting the whole ecosystem has been treating code like candy.'
+++

`npm install` has always been a suspiciously polite way to say “please execute this stranger’s code on my machine.”

We all acted like that was normal because the alternative was admitting the ecosystem had been running a tiny unsecured casino and calling it tooling. Then May 2026 showed up with maintainer takeovers, poisoned packages, stolen CI secrets, and a general atmosphere of “who the hell let this thing happen,” and suddenly npm remembered that trust is not a renewable resource.

So now we get two useful changes: staged publishing and install-source allowlists. Which is funny, because both of them are just npm admitting the same embarrassing truth from two different angles: publishing is dangerous, and installing is also dangerous, and pretending otherwise was always a bit stupid.

## Publishing was too casual for a world this mean

Staged publishing is the first npm feature in a while that sounds mildly annoying in exactly the right way.

Instead of firing a package straight into the registry like you’re launching a marshmallow at a wall, `npm stage publish` drops the tarball into a queue. A human maintainer then has to approve it with 2FA before it goes live. Not a bot. Not a stolen token. A person, with a pulse, making a decision.

That is the whole point, and it is a very good point.

If your release flow is fully automated, great. Keep it automated right up until the moment it matters. Let CI do the boring packing and uploading. Then stop and force a human to look at the thing before the world gets it. That last step is not bureaucracy. It is the difference between “shipped” and “oops, we just published a gift-wrapped worm.”

The nice bit is that npm didn’t make this some side quest for paranoid weirdos. It wired staged publishing into trusted publishing too, so you can run a stage-only setup where CI is allowed to stage releases but not straight-up publish them. That is how you build a sane pipeline: the machine prepares the package, the maintainer signs off, the registry shuts up and waits.

Wild concept. Almost medieval. Glorious.

## Install is not a shopping cart

The other half of the update is even more telling. npm added `--allow-file`, `--allow-remote`, and `--allow-directory`, alongside the existing `--allow-git` flag. In plain English: npm is finally giving people a way to say, “no, you may not fetch code from every weird little source just because somebody wrote a dependency string with confidence.”

Because that’s what all of those paths are: code delivery channels.

Local directories, Git URLs, remote tarballs — these are not quaint convenience options. They are alternate trust boundaries. They are places where arbitrary code can show up wearing a fake mustache and a cheerful README.

The fact that `--allow-git` currently defaults to `all` is exactly the sort of thing that makes security people stare into the middle distance and whisper swear words. npm has already said that default flips to `none` in v12. Good. It should. Any default that treats Git dependencies like a harmless drizzle of productivity is lying to you.

If you want those sources, say so. Explicitly. Loudly. In config. With your full chest. Do not make the installer guess what kind of chaos you were in the mood for when you added a dependency six months ago.

## This is what the ecosystem learned the hard way

The timing matters.

npm didn’t wake up one morning inspired by pure architectural beauty. It watched the JavaScript supply chain get mugged in public. Maintainer accounts got popped. CI workflows got abused. Package trojans spread faster than half the people defending them could spell “OIDC.” The registry spent a month getting slapped around by attacks that proved a simple, ugly fact: the weakest link is often not the signature or the checksum or the attestation. It is the human who can still be tricked into approving the wrong thing.

So yes, staged publishing is slower. Good. Slower is sometimes what safety looks like.

Yes, install allowlists are annoying. Also good. Annoying is what it feels like when a tool stops pretending every source is equally trustworthy.

The old vibe was: “trust the ecosystem.”

The new vibe is: “maybe don’t auto-ingest code from a URL because some package manifest got cute.”

That is not cynicism. That is just adulthood with better error messages.

## A registry that can say no is finally acting like one

The best security change npm made here is not a shiny algorithm. It is a new refusal.

No, your CI does not get to publish straight to the public registry forever without a human check.

No, every non-registry source does not get a free pass just because it is convenient in a demo.

No, the package manager should not behave like a vending machine for other people’s executable opinions.

That’s the actual upgrade. Less magic. More friction. Fewer opportunities for some little gremlin with a stolen token to turn your release process into a crime scene.

And honestly? About fucking time.
