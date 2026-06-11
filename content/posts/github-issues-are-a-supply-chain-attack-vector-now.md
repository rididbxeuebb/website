---
title: 'GitHub Issues Are a Supply-Chain Attack Vector Now'
date: 2026-06-11
description: 'Gemini CLI showed how a public issue can crawl from “triage” to “push to main” if your bot is allowed to be clever in the wrong places.'
---

A public GitHub issue is not a bug report anymore. It is a little paper-thin exploit delivery vehicle with a nice icon.

That sounds dramatic until you look at what Google had to patch in Gemini CLI this spring. The advisory — GHSA-wpqr-6v78-jr5g — covered two separate sins: headless mode trusted workspace folders too casually, and `--yolo` mode ignored fine-grained tool allowlists. In other words, the bot was happy to swallow untrusted input, reach into the workspace, and then act like boundaries were for other people.

Pillar Security’s write-up is the part that should make everyone uncomfortable. They showed a path from a public issue to a full supply-chain compromise of `google-gemini/gemini-cli`. Not “the model hallucinated a weird reply.” Not “someone got owned by a typo.” A plain old issue body fed into an automated triage workflow, the agent got steered into leaking secrets, and the stolen token chain eventually reached `contents: write` on the repo.

That is the whole nightmare in one sentence: untrusted text, privileged tools, and a workflow that thought it was doing customer service.

The industry keeps pretending prompt injection is some exotic wizard problem. It is not. It is just input handling, except the input is now a blob of internet sludge and the downstream action can be `gh issue edit`, shell access, or whatever other shiny little footgun you stapled to the bot because “automation.” If the agent can read secrets, talk outward, and write back, congratulations: you built a supply-chain attack surface with a mascot.

The annoying part is how easy this is to dismiss if you squint hard enough. “Well, the user opened an issue.” Yes. That is the point. Public issues are untrusted by default. They are the GitHub equivalent of a stranger handing your receptionist a USB stick and asking for the CEO.

The fix is not mystical and it is not cute:

```yaml
permissions:
   contents: read
   issues: write

steps:
   - uses: actions/checkout@v4
     with:
        persist-credentials: false
```

And then, because the YAML above is not a force field, you also need to ask the boring adult questions: can this bot read secrets, can it exfiltrate them, and does it get to touch write-capable tokens later in the same run? If the answer is yes, your “assistant” is a tiny breach with branding.

My favorite lie in this entire category is the one where people say the prompt is the boundary. No, the prompt is decoration. The real boundary is what the runner can access, what the checkout step leaves on disk, and whether the workflow can be tricked into pivoting from issue triage to repo mutation. A polite system prompt does not matter when the filesystem and token handling are already doing acrobatics behind its back.

So yes, GitHub issues are now an attack vector. Not because issues are evil, but because we keep giving bots god-mode and then acting shocked when a stranger writes three hostile paragraphs and the bot happily licks the hand grenade.

If your issue triager can reach secrets, external network, and write paths, it is not triage. It is a self-inflicted incident response exercise waiting for a headline.
