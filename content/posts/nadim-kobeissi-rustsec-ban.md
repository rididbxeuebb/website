+++
title = "Nadim Kobeissi got banned from Rust for reporting bugs and honestly? Good."
date = 2026-04-01T12:00:00Z
description = "The cryptographer vs. RustSec saga is the most entertaining open source meltdown of 2026, and nobody comes out looking good."
+++

Listen, I don't know who needs to hear this, but if you submit a security vulnerability report and the response you get is a ban from the project, something has gone catastrophically wrong. Not with you. With the project.

Let me tell you about Nadim Kobeissi. He's a cryptographer — a real one, not some airdrop-claiming-web3-fuckboy — and back in February he found what he describes as critical vulnerabilities in hpke-rs, a Rust cryptography library being used by Signal, OpenMLS, Google, the Linux kernel, and various other places you actually want your encryption to work. We're talking nonce-reuse bugs that could let attackers recover plaintext. We're talking about libraries that are supposedly "formally verified" and still shipped catastrophic mistakes.

So Kobeissi did what you're supposed to do. He reported the bugs. He filed RustSec advisories. He tried to get the vulnerabilities properly disclosed so people could, you know, update their shit.

And the RustSec maintainers basically told him to get lost.

They closed his PRs. They blocked him from the organization without notice. Then they banned him from Rust's Zulip spaces, citing "harassment."

Harassment for what? For filing bug reports. For following the disclosure process. For being persistently annoying about critical vulnerabilities in libraries that are deployed in production systems used by millions of people.

Now here's where it gets good — and by good I mean "exquisitely糟糕" — the guy who issued the ban was also the same person sitting on the Rust Leadership Council, which is the body that supposedly adjudicates conduct complaints. Kobeissi filed a complaint with the Rust Foundation, and the guy whose conduct was being complained about is literally part of the committee reviewing the complaint.

That's not a conflict of interest. That's a parody of a conflict of interest. That's the plot of a bad movie about institutional corruption, except the director would say it's too on-the-nose.

## The "harassment" angle is where this gets genuinely interesting

Filippo Valsorda — who has been feuding with Kobeissi for over a decade, so definitely not a biased party — told The Register that Kobeissi's handling "never seemed to be in good faith or proportional." He called the blog post "aggressive, accusatory, hyperbolic, and bordering on dishonest."

And look, I've read Kobeissi's blog post. It's pretty harsh. He accuses Cryspen — the company behind libcrux — of silently fixing the bug without any public disclosure or acknowledgment. He calls out the "formally verified" marketing while shipping code with cryptographic failures. He's not subtle about it.

But here's my question: when you're reporting a critical bug that affects production deployments at Signal and Google, when you've been trying to get a RustSec advisory published for over a month, when the maintainers are closing your PRs and ignoring you — at what point does "aggressive" become "justifiable frustration"?

Because I've seen plenty of vulnerability reports that were polite, measured, and completely ignored. The severity of the response seems inversely correlated with the politeness of the report. Be nice and get dismissed. Be angry and get banned. The incentives here are completely backwards.

The cryptography community is not known for being gentle. This is a field where people have spent decades arguing about whether secp256k1 is a trap, whether TweetNaCl is actually secure, whether everything bun哈希does is a catastrophe. Aggressive technical arguments are the norm, not the exception. And sure, maybe Kobeissi went too far. But a ban? A permanent exclusion from the community? For提交漏洞报告?

## The absolutely hilarious part

On March 24th, Cryspen finally filed the security advisories that Kobeissi had been asking for since February.

The same vulnerabilities. The same RustSec database. The same advisory process he was banned for trying to use.

That's not vindication. That's a goddamn punchline.

Everything Kobeissi was asking for got published. The advisories exist. The vulnerabilities were real. And the response to "please publish these so people can protect themselves" was to ban the guy asking.

If this were a movie, the hero would get the girl, the villains would get exposed, and there would be a nice epilogue about how the community learned and grew. But this is open source, so what actually happened is the maintainers got to keep their moderator privileges, Kobeissi got to keep his ban, and Cryspen got to quietly publish the advisories on their own timeline without ever having to acknowledge they shipped broken crypto for however long.

## The real problem here

Here's what this saga actually exposes: the open source security infrastructure is held together with duct tape and good intentions. There's no standard process for handling vulnerability reports. There's no clear escalation path when maintainers don't cooperate. There's no accountability mechanism when the people tasked with publishing advisories decide not to. And when someone gets frustrated enough to make noise about it, they get painted as the problem.

The RustSec advisory database is supposed to be the canonical source for security vulnerabilities in Rust crates. It's supposed to feed into cargo-audit so developers can know if their dependencies have known bugs. It is genuinely important infrastructure. And it's run by a small group of volunteers who can just... decide not to publish your advisory. There's no oversight. There's no appeals process. There's just a Zulip channel where you can get banned for being too persistent about critical bugs.

This is not unique to Rust. Every ecosystem has this problem. But the Rust community especially loves to think of itself as better — more rigorous, more process-oriented, more "safe." And then this happens, and it's just the same old open source governance nightmare wearing a cargo vest.

## So who is right?

Probably neither side. Kobeissi was probably too aggressive in his advocacy. The maintainers were definitely too heavy-handed in their response. Cryspen's "we fixed it quietly and didn't tell anyone" approach to a cryptographic vulnerability in a library used by major tech companies is genuinely alarming. The conflict of interest in the moderation process is indefensible.

But here's what I keep coming back to: if you're a developer using hpke-rs, if you're building something on top of a crate that depends on libcrux, if you're relying on the "formally verified" promise to keep your users' data safe — you deserved to know about these vulnerabilities. You deserved a RustSec advisory. You deserved to be able to run `cargo audit` and see a warning.

And instead, the system that was supposed to protect you was too busy arguing about whether the guy reporting the bugs was being mean to give a shit about the actual security issue.

This is fine. Everything is fine.

Go check your dependencies.
