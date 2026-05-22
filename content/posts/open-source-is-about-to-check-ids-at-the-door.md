---
title: 'Open Source Is About to Check IDs at the Door'
date: 2026-05-22
description: 'A forked PR can poison the cache, publish malware, and make open contribution look like a security bug with better branding.'
---

At this point, open source feels less like a commons and more like a nightclub with a broken latch.

Anybody can walk in. Some people brought snacks. Some people brought a crowbar and a fake mustache and now your CI is on fire.

That’s the mood TanStack just walked into after its npm supply-chain mess. The recent follow-up wasn’t just “here’s how we fixed the pipeline.” It was the part that should make everybody’s eye twitch: they’re openly considering an invite-only pull request model. Not closed source. Not “no contributors.” Just: maybe the internet shouldn’t be allowed to fling random code at the front door and call it community.

And honestly? I get it.

The attack didn’t need a merged PR. It didn’t need a stolen maintainer token. It needed a fork, a bad workflow shape, and the kind of GitHub Actions trust boundary that looks normal right up until it ruins your week. GitHub’s own docs have been screaming for years that `pull_request_target` is for metadata chores, not for running stranger code. Yet here we are, again, with a repo learning the hard way that “works in CI” is not the same thing as “safe in CI.”

That’s the part people keep pretending is philosophical when it’s actually mechanical.

If a forked PR can run in a context that touches shared cache, and that cache can later be restored by a privileged release job, then the PR was never just a PR. It was a bootstrap path into your trusted pipeline. The maintainers didn’t “invite trouble.” The platform handed trouble a badge and a lunch voucher.

## The ugly little truth

Open contribution only works when the boundaries are real.

If untrusted input can’t reach privileged state, great. PRs are beautiful. Forks are useful. Drive-by fixes are one of the few genuinely nice things left on the internet.

But when the platform lets a fork write to state that a later trusted job will consume, the whole model starts smelling like wet cardboard. You can keep saying “open” all you want. If the trust boundary is porous enough, what you’ve built is not openness. It’s a security theater exhibit with GitHub branding.

That’s why this debate is happening now, and not in some abstract future where everybody has perfect workflows and spiritually clean YAML.

TanStack is basically saying what a lot of maintainers are muttering into their coffee already: open PRs are nice until they become a delivery mechanism for malware, cache poisoning, and existential regret. So maybe the new shape is issues and discussions for anyone, but PRs only by invitation. A little more gate. A little less chaos.

That’s not them becoming evil. That’s them becoming tired.

## GitHub helped make this mess

I’m not letting GitHub off the hook here, because that would be cowardly and boring.

GitHub Actions has had the same dumb trap in the floor for years. GitHub docs say `pull_request_target` can access secrets and write permissions, and GitHub docs on cache access say PRs can touch caches from the base branch. That is not a corner case. That is the entire shape of the problem. We’ve just been normalizing it because the builds were fast and the dashboard looked pretty.

Meanwhile the broader ecosystem is already reacting like it got bitten.

pnpm is leaning harder on `minimumReleaseAge`, because apparently we’ve reached the point where waiting a day before trusting a brand-new package counts as hygiene. Which, fair. In 2026, the first hour of a package’s life is basically its burglary window.

That should not feel normal. It does anyway.

And that’s the real stink of all this: maintainers are not getting more paranoid because they’re fragile snowflakes. They’re getting more paranoid because the modern software supply chain keeps proving that every convenience feature eventually turns into an attack surface if you let it sit there long enough.

## Invitation-only PRs are not the apocalypse

People hear “invite-only PRs” and start acting like someone burned the library down.

Relax.

It’s not closed source. It’s not a secret cabal. It’s a project trying to keep random internet code from directly touching privileged machinery. If you want to contribute, you can still file issues, post patches, review code, earn trust, and climb the ladder like a human instead of a malware vending machine.

That said, it is still a bad sign.

Not because the model is morally wrong, but because it means the default platform experience has become so hostile that maintainers are considering a velvet rope just to keep the vodka bottle from going missing. Open source was supposed to lower barriers. Instead, we’ve built a system where “open” sometimes means “open to anyone who wants to use your automation as a crowbar.”

That’s the part that makes me pissy.

Not the PR gate. The fact that the gate is even being discussed.

If you want a neat little moral, here it is: the problem is not that open source got too open. The problem is that our tooling got too stupid to tell the difference between public contribution and privileged execution. Until that changes, more projects are going to start acting like a bouncer at a shitty club on a Thursday night.

And I won’t blame them.

I’ll blame the rotten doorframe.
