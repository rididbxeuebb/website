---
title: 'Google Turned Gemini CLI Into an Enterprise Tax'
date: 2026-05-24
description: 'The repo stayed open, the useful bits got fenced off, and Google somehow managed to make Apache 2.0 feel like a hostage note.'
---

Google did the cleanest dirty trick in software: keep the repo public, kill the product, and call the remains a migration.

On May 19, Google said Gemini CLI is getting folded into Antigravity CLI, free users get shoved over by June 18, and enterprise customers get to keep the old thing like nothing happened. The announcement was dressed up as a noble consolidation for the glorious multi-agent future, which is exactly the sort of sentence you write when you know you’re about to annoy thousands of developers and want the word salad to cushion the impact.

Here’s the actual shape of it:

- Gemini CLI stays Apache 2.0.
- Gemini CLI keeps existing only for the people paying Google in the right way.
- Free users, Google AI Pro and Ultra users, and Gemini Code Assist for individuals are told to move.
- The shiny replacement is Antigravity CLI, which is not feature-parity, not open source, and apparently not interested in pretending otherwise.

That’s the scam-shaped part. The code being open does not matter if the service layer is the thing that makes the tool breathe. A CLI with dead auth, dead quotas, and dead backend access is just a nice-looking corpse. Very technically reusable. Very spiritually useless.

And yes, Google absolutely knows this. That’s why the blog post makes such a big deal about the repository still being there with “no changes.” Cool. Great. Marvelous. A public archive is not a continuity plan. It’s a museum plaque.

The more obnoxious part is the asymmetry. Enterprise customers keep Gemini CLI. Everyone else gets the fun-sized product transition and a deadline that feels like it was chosen by someone who thinks `git pull --rebase` is a migration strategy. If the new platform is obviously superior, why does it need a forced shove? If it’s not obviously superior, why are people being herded into it like cattle with laptops?

The GitHub discussion turned into the expected little riot: users complaining about quotas, missing features, privacy terms, and the charming corporate habit of calling a downgrade “focus.” My favorite genre of company behavior is when they say “we listened to feedback” and then proceed to use that feedback as kindling.

This is also why the “but the repo is still open source” defense is so tiresome. Open source is not a magic force field. It is not a spell that keeps a product alive after the business side decides the old audience is no longer profitable enough. If the model access, authentication, limits, and shipping cadence all live behind Google’s wall, then the repository is basically a souvenir shop. You can walk through it. You cannot eat there.

What makes this especially gross is the social contract. People contributed because the tool was open, useful, and alive. They wrote integrations. They filed bugs. They fixed docs. They made the thing better. Then Google looked at that ecosystem and decided the correct next move was to funnel the energy into a closed successor for the paying tiers while tossing everyone else a “smooth transition” page and a fucking deadline.

That’s not a transition. That’s a landlord telling you the apartment is still there while quietly removing the plumbing.

If you want the less dramatic but more accurate reading, it’s this: the industry has figured out that the repository is the marketing asset and the backend is the business. Once those two diverge, the license starts doing a lot of emotional heavy lifting it was never designed for. Apache 2.0 gives you rights. It does not give you leverage.

And because the internet is allergic to being trapped, alternatives immediately start crawling out of the floorboards. Qwen Code exists. Community forks exist. People will keep cloning, re-wiring, and duct-taping these tools to other models because developers are, by temperament, stubborn little goblins with `bash` histories full of bad decisions.

That’s the real lesson here: don’t confuse access with ownership. Don’t confuse a public repo with a stable product. And for the love of all that is sane, don’t build your workflow around a company’s free tier and then act surprised when the free tier gets fed into a shredder.

Google didn’t just “move Gemini CLI to Antigravity CLI.” It took a useful open tool, reserved the practical version for paying customers, and left everyone else holding a beautiful, documented, increasingly decorative shell.

Open source, apparently, is just what they call the parts they’re done monetizing.
