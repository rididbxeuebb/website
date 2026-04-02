+++
title = "North Korea Pwned npm and Everyone Just... Let It Happen"
date = 2026-04-01T02:30:00Z
description = "North Korean hackers hijacked the axios maintainer account, pushed malicious versions with a cross-platform RAT, and the JavaScript ecosystem just shrugged. Again."
+++

The npm ecosystem is a burning trash can, and I am absolutely done pretending otherwise.

## Another Day, Another Supply Chain Catastrophe

So here's what happened. On March 31, 2026, some absolute legends at North Korea's UNC1069 (apparently they have a whole job posting for "state-sponsored hacker" and they're actually good at it) got their hands on an axios maintainer's account. Changed the email to `ifstap@proton.me` — because of course it's Proton, those guys literally cannot resist a good privacy-focused hookup — and pushed two versions: `1.14.1` and `0.30.4`.

These versions pulled in a dependency called `plain-crypto-js` version 4.2.1. Cute name, right? Sounds like something you'd use to encrypt your startup's half-baked auth system. Except this piece of garbage was an obfuscated dropper that deployed WAVESHAPER.V2 — a cross-platform RAT that works on Windows, macOS, AND Linux.

Let me say that again so it properly sinks in:

**North Korea has a backdoor that works on your MacBook, your Linux server, AND your Windows workstation. All because someone typed `npm install axios` without checking what the latest version actually contains.**

## The Attack Is Actually Impressive and That's What Pisses Me Off

Here's the thing that makes me want to put my fist through my monitor: this attack was _elegant_.

The `postinstall` hook in the malicious package runs `setup.js` automatically. That script detects your OS, downloads the appropriate payload, executes it, and then — here comes the chef's kiss — _deletes itself_ and reverts the `package.json` to hide the evidence. It's like a burglar who breaks into your house, robs you blind, cleans up, and leaves a fruit basket.

The WAVESHAPER.V2 backdoor itself? It's got:

- System telemetry collection (hostname, username, boot time, timezone, running processes)
- Directory enumeration with file sizes and timestamps
- Arbitrary shell command execution
- In-memory PE injection for Windows
- AppleScript execution on macOS
- Python variant for Linux
- 60-second beacon intervals to C2 at `sfrclak.com:8000`

This isn't some script kiddie running `msfconsole` in their mom's basement. This is a professional operation. And they got in through... a maintainer's password. Probably reused, probably 2FA-less, probably the same password they used for their Gmail since 2014.

## The Ecosystem That Couldn't Give a Shit

But here's what really grinds my gears: the response.

NPM published an advisory. GitHub sent some emails. A few companies published blog posts about "how to protect yourself." And within a week, everyone's moved on to the next drama. Someone posted a meme about LLMs, and suddenly the axios backdoor is ancient history.

Meanwhile, axios has over 100 million weekly downloads. There are probably thousands of production systems that pulled these versions during the ~3 hour window when they were live. How many of those got investigated? How many got cleaned up? How many are still beaconing to `142.11.206.73` right now while some analyst at a SOC somewhere is watching a Slack thread about whether hot dogs are sandwiches?

And the kicker? The fix is literally just "don't use those versions." That's it. That's the remediation. Pin your dependencies to a known-good version, and pray nothing else gets compromised next week.

## Why This Keeps Happening

The npm ecosystem has a fundamental trust problem that nobody wants to address:

1. **Anyone can publish anything** — no review, no signing, no verification
2. **Maintainers are unpaid volunteers** — with passwords that probably haven't been rotated since the Obama administration
3. **Dependencies cascade forever** — your `package.json` probably pulls in 500+ packages you've never heard of, and any one of them could be the next axios
4. **Nobody audits anything** — we just `npm install` and hope for the best

There's no accountability. There's no signature verification for published packages. There's no trust framework worth a damn. Just a polite suggestion to check the integrity of what you're installing, which absolutely no one does because that would take hours and there are TikToks to watch.

## If You're Still Using Axios

Here's what you actually need to do:

1. Check your `package-lock.json` for `plain-crypto-js` versions 4.2.0 or 4.2.1 RIGHT NOW
2. If you find it, assume you're compromised. Rotate every credential on that machine. All of them. Yes, all of them.
3. Pin axios to 1.14.0 or earlier, 0.30.3 or earlier
4. Block `sfrclak.com` and `142.11.206.73` at your network perimeter
5. Clear your npm cache — do it now, I'll wait
6. Actually implement some kind of dependency scanning in your CI pipeline, for once

And for the love of god, enable 2FA on your npm account. All of you. Right now. Even if you think your package isn't important — it's not about your package, it's about the supply chain you become a part of.

## The Real Problem

This isn't going to stop. It's going to get worse. North Korea is funding their missile program by robbing crypto exchanges and popping software supply chains. They have actual resources, actual motivation, and actual skills. The npm ecosystem is a wide-open target with no security guard and all the money in the world sitting in the register.

We keep treating supply chain security as someone else's problem. The npm maintainers will figure it out. The security companies will catch it. The CI pipeline will block it. But no one's actually solving the underlying disease — we just keep applying fresh bandages and hoping the bleeding stops.

The next attack won't be axios. It might be something you depend on. It might be something your dependency depends on. And by the time you find out, some kid in Pyongyang will have your AWS keys and be mining Monero on your servers.

Check your `package-lock.json`. Check it now.

I'll wait.
