---
title: 'GitHub Tried to Make Copilot a Co-Author, and That Was Deeply Stupid'
date: 2026-05-05
description: 'VS Code turned commit provenance into AI theater, then had to yank the default back to off.'
---

The minute a tool starts editing your commit metadata without screaming first, it stops being helpful and starts being a little bureaucratic mugger with a logo.

That is basically the whole story here. VS Code 1.118 shipped with `git.addAICoAuthor` defaulted to `all`, which meant the Git extension could slap `Co-authored-by: Copilot <copilot@github.com>` onto commits when it decided AI had touched the work. PR #310226 flipped the switch. PR #313931 flipped it back to `off` after people did what sane humans do when a vendor starts tampering with provenance: they yelled.

And yes, they had every right to. Commit trailers are not decorative confetti. They are a signal. People use them to understand who actually did the work, who is accountable, and whether a change was genuinely collaborative or just the usual late-night goblin with one good idea and six bad ones. If your editor quietly mutates that signal after the human thinks the transaction is done, the UI is lying. That is not “transparency.” That is fraud with better typography.

The especially stupid part is that the feature was not even reliably honest about its own boundaries. Users reported `chat.disableAIFeatures: true` and still saw Copilot show up in commit trailers. The maintainer response was refreshingly blunt: it should never have been enabled when AI features are disabled, and it should not add attribution to changes that were not done by AI. Which, yes. Congratulations on discovering the floor after falling through it.

I do not care how much corporate poetry you wrap around this. If I write the code, review the diff, write the commit message, and hit commit, the author list should not get a surprise guest star after the curtain call. I already distrust my own commits before coffee. I do not need Microsoft’s little hall monitor crawling into the repo and stamping my work with a robot signature because someone in product thought “adoption” would look better in a dashboard.

That last part matters. This smelled like metric theater from ten miles away. Once you start auto-tagging work as AI-assisted by default, you can brag about how much Copilot “helped” without bothering to ask whether the user wanted that story told in the first place. That is not attribution. That is inventory management.

The fix was simple, which makes the original mistake look even dumber. Set the default to off. Keep AI feature gating honest. Make the opt-in explicit. If a user wants to add an AI co-author trailer, fine, let them. But make them ask for it like an adult, not by shoving it into the commit path and hoping nobody notices until after it lands in history.

```json
{
   "git.addAICoAuthor": "off"
}
```

That should have been the starting point, not the recovery plan.

The bigger rot is the instinct behind all of this. Modern AI products keep trying to occupy the last inch of the workflow: not just the editor, not just the chat pane, but the metadata, the telemetry, the billing, the authorship, the little bureaucratic footnotes that make software engineering feel real. First they help. Then they “surface insight.” Then they quietly start rewriting the paperwork.

No thanks. If a tool can’t respect the line between assistance and authorship, it doesn’t get a seat at the table. It gets turned off, buried in settings, and treated like a cautionary tale for product people who confuse visibility with consent.

GitHub should know better by now. If it wants people to trust Copilot, it can start by not lying in the commit log.
