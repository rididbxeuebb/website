+++
title = "CanisterWorm Just Turned Your npm install Into a Goddamn Malware Farm"
date = 2026-03-30T12:00:00Z
description = "The Trivy supply chain compromise spread to 141 packages in a week. And somehow, the solution is still 'just don't run untrusted code lol.'"
+++

Let me tell you about the week I stopped trusting npm install. Actually, I never trusted it to begin with, but now I have proof that the entire JavaScript ecosystem is one compromised token away from imploding.

## The Attack

On March 16, 2026, someone with a stolen npm token published malicious versions of Trivy — you know, the popular security scanner that millions of developers run in their CI/CD pipelines. They pushed malware-laced releases of `trivy`, `trivy-action`, and `setup-trivy`. Simple credential theft at first. Dumb. Effective.

But then the attackers got creative.

A week later, we're staring at CanisterWorm — a self-propagating nightmare that uses Internet Computer (ICP) canisters as its command-and-control infrastructure. The malware drops a Python backdoor that phones home to an ICP canister every 50 minutes, asking politely for instructions like some kind of obedient malware pet.

Here's where it gets hilarious. The canister returns a YouTube URL when it's in "dormant mode." A Rickroll, specifically. When the attacker wants to deploy actual malicious payloads, they swap the URL to point to something else. Every infected machine then grabs the new binary on its next poll. The old binary keeps running because the script never kills previous processes. Beautiful. Clean. Idiotic in the way only malware can be.

The worm has since spread to 141 malicious package artifacts across more than 66 unique packages. 47 npm packages in the initial wave. 28 in the @EmilGroup scope. 16 in @opengov scope. @teale.io/eslint-config. @airtm/uuid-base32. @pypestream/floating-ui-dom. You know, the usual suspects.

## The Propagation Is the Point

What makes CanisterWorm special isn't the initial compromise — that happens all the goddamn time. It's the mutation. The new variant found in @teale.io/eslint-config versions 1.8.11 and 1.8.12 includes a `findNpmTokens()` function in `index.js` that runs during the postinstall phase. It scans your machine for npm authentication tokens, grabs them, and immediately spawns the worm as a background process to infect every package that token has access to.

This is the moment where the attack goes from "compromised account publishes malware" to "malware compromises more accounts and publishes itself." Every developer or CI pipeline that installs this package and has an npm token accessible becomes an unwitting propagation vector. Their packages get infected. Their downstream users install those. If any of those users have tokens, the cycle repeats.

Congratulations. You've just built a malware worm using the same infrastructure that powers the modern JavaScript ecosystem.

## The Irony Is Delicious

Trivy is a security tool. People run it specifically to find vulnerabilities in their code. And now that security tool has become the attack vector that compromises your entire supply chain. The irony is so thick you could spread it on toast.

And the response from the community? "Just don't run untrusted code." "Audit your dependencies." "Use lockfiles." As if any of that helps when a maintainer's token gets stolen and legitimate packages get backdoored. As if auditing 1,500 direct dependencies and 50,000 transitive ones is something a normal human being can do.

The systemd user service persistence mechanism masquerades as PostgreSQL tooling ("pgmon") to fly under the radar. It restarts automatically if terminated using `Restart=always`. The backdoor polls every 50 minutes with a spoofed browser User-Agent. This isn't some script kiddie nonsense — this is professional-grade malware using decentralized infrastructure that can't be taken down because the command-and-control lives on a blockchain.

The canister controller can swap the URL at any time, pushing new binaries to all infected hosts without touching the implant. Traditional takedowns don't work. You can't shut down a smart contract. You can't seize a decentralized ledger. The attackers found the one infrastructure that survives the usual police work, and they used it to spread npm packages full of credential-stealing code.

## What Now?

Socket, the supply chain security company, detected the attack expanding. Endor Labs published analysis. JFrog published analysis. The Hacker News wrote about it. Everyone's talking about it. Nobody's fixing it.

The fundamental problem is that npm's trust model is broken at a architectural level. You trust that the package you install is what the maintainer published. But anyone with a token can publish as that maintainer. Two-factor authentication exists but isn't enforced. The audit tools exist but run after the fact. There's no runtime protection, no sandbox, no nothing.

You run `npm install` and hope. That's the security model. Hope.

So yeah, CanisterWorm is a wake-up call. It's also the twentieth wake-up call. We've been hitting snooze on supply chain security for years because it's easier to write blog posts about it than to actually fix the underlying architectural catastrophe that makes npm, PyPI, and every other package registry a waiting disaster.

Maybe next time it'll be your project. Maybe next time it'll be the dependency you didn't even know you had. Maybe next time you'll actually read the postinstall hooks in your node_modules before running them.

But probably not. Because that's how we got here in the first place.
