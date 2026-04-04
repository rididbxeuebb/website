+++
title = "One Man's PC Just Brought Down the Internet. Again."
date = 2026-04-04T12:00:00Z
description = "The axios maintainer got RATed through social engineering, and suddenly millions of projects have a remote access trojan. Welcome to the npm ecosystem where your entire supply chain depends on some random dudes password hygiene."
+++

The axios supply chain compromise dropped on March 31, 2026, and it's one of the most absurd security incidents I've seen in years. Not because the attack was sophisticated — it wasn't — but because of what it reveals about the entire JavaScript ecosystem. Spoiler: it's a house of cards sitting on a foundation of hope and prayers.

## The Gist

Someone social-engineered the lead maintainer of axios, got remote access to their machine, grabbed their npm credentials, and pushed two malicious versions: `1.14.1` and `0.30.4`. Both injected a dependency called `plain-crypto-js@4.2.1` which installed a remote access trojan. macOS, Windows, Linux — everyone's problem.

The malicious versions were live for about three hours before someone noticed and npm pulled them. But guess what? That's more than enough time for millions of CI/CD pipelines to pick up the poisoned versions. The initial infection window was roughly 00:21 to 03:15 UTC on March 31. If you ran `npm install` during that window and got a fresh `node_modules`, congratulations — you might have a RAT.

The payload connected to `sfrclak[.]com` on port 8000. That's your new canary in the coal mine, folks. If you see that domain in your network logs, your machine is pwned.

## The Real Problem Isn't the Attack

Let me make sure I'm being clear here: the problem isn't that some maintainer got socially engineered. That happens. The problem is that **one person's compromised laptop can poison the entire JavaScript ecosystem for hours before anyone notices**.

We're talking about a library with 109,000 GitHub stars, used by literally every JavaScript project on the planet. axios is to HTTP requests what oxygen is to breathing. And the only thing standing between you and a remote access trojan was one lead maintainer's password hygiene.

This is the same pattern we've seen over and over — `colors`, `faker`, `event-stream`, now axios. Every few months some maintainer's credentials get leaked or phished, and suddenly millions of projects are installing malware. The npm security model is essentially "please don't get compromised, thanks."

## Where Was 2FA?

Here's the thing that pisses me off the most: npm has had 2FA available for years, but it's not enforced. Not for publishing, not for critical packages. The maintainer could have had 2FA enabled and this attack still might have worked — the attacker got a RAT on the machine itself, so even 2FA wouldn't help if the session was already authenticated. But that's not even the point.

The point is that npm, owned by GitHub, owned by Microsoft, doesn't require 2FA for package publishing. Doesn't require any meaningful access controls. Doesn't have any automated detection for "hey, this package just got a new dependency from a new maintainer with zero tests running." The detection of this compromise depended entirely on community members noticing and filing issues — which the attacker then deleted using the compromised account.

Let that sink in: the attacker had enough access to delete the issues reporting the attack. That's how broken the permission model is.

## The Response Is Almost Funny

Here's the post-mortem from the axios maintainer:

- Complete wipe of all devices and credentials
- Reset of all accounts, personal and otherwise
- Adoption of OIDC flow for publishing
- "Improvement of overall security posture"

Translation: they had no security to begin with, and now they're scrambling to implement basic precautions that should have existed before 109 million people depended on their library.

The industry response has been the usual hand-wringing. "We need better supply chain security!" "We needSigstore!" "We needsbom!" Great, tell that to the 10,000 companies that already got owned during those three hours.

## The Uncomfortable Truth

Open source supply chain security is a myth we've been telling ourselves because it was convenient. The reality is that npm, PyPI, RubyGems, and every other package registry operate on an honor system from the 1990s. There's no cryptographic verification of who pushed what beyond "you have the password." There's no tamper-evident audit trail. There's no automated detection for when a maintainer's account does something suspicious.

We're building the modern software world on a foundation that would be laughed out of any security conference, but because it's "open source" we treat it as automatically trustworthy. The irony is that proprietary software gets dragged for security flaws constantly, but npm packages get installed with zero scrutiny because "it's open source, someone would have noticed."

Someone didn't notice. For three hours, the internet was installing a RAT. And that's just the one we know about.

## If You're an Axios User

Check your lockfiles right now:

```bash
grep -E "axios@(1\.14\.1|0\.30\.4)|plain-crypto-js" package-lock.json yarn.lock
```

If you get a hit, assume compromise. Downgrade to `1.14.0` or `0.30.3`, nuke `node_modules/plain-crypto-js/`, and rotate every credential on that machine. If it was a CI runner, rotate those secrets too — the attacker specifically targeted CI environments in similar campaigns.

## The Broader Lesson

We can keep pretending this is an isolated incident, or we can admit that the JavaScript ecosystem has a structural security problem that isn't going to be fixed by adding more badges to our READMEs. The npm registry needs fundamental architectural changes — enforced 2FA, OIDC publishing, automated anomaly detection, tamper-evident logging. Until then, every package you install is a leap of faith.

And while we're at it, maybe we should stop acting surprised when "someone got phished" turns into "the entire internet got backdoored." It's happened enough times now that it's basically a feature of the platform.
