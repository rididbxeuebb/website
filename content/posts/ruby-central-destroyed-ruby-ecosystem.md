+++
title = "Ruby Central Just Destroyed the Ruby Ecosystem and Called It Governance"
date = "2026-04-04"
description = "The RubyGems Fracture incident proves that open source foundations have no fucking idea how to handle power, people, or basic human communication."
+++

Let me tell you about the time Ruby Central accidentally started a civil war in the Ruby ecosystem by trying to fire two people who wouldn't shut up about package management. No, seriously. This is the most spectacular organizational failure I've seen in years, and I've watched npm drama unfold in real-time.

## The Setup

It started, as these things always do, with money. Ruby Central — the nonprofit foundation that supposedly "governs" RubyGems and Bundler — was running low on funds. A $250,000 pledge got yanked after DHH spoke at RailsConf (long story, everyone was already furious about that). The budget was tight. The burn rate was too high. Something had to give.

Enter André Arko and Samuel Giddins. These two had been deep in the RubyGems/Bundler ecosystem for years. André was literally the first OSS Director of Ruby Central after the RubyTogether merger. Sam was the full-time security engineer. They knew where every body was buried. They had keys to everything.

Then they announced they were leaving. Well, sort of. The details are murky, which is already a red flag.

## TheRV Incident

Here's where it gets good. While still technically affiliated with Ruby Central, André and Sam started working on something called RV — a new Ruby version manager and gem tool. They didn't tell Ruby Central. They just dropped it on August 25, 2025 with a blog post titled "RV: A New Kind of Ruby Management Tool."

Ruby Central found out the same way the rest of us did. Through a blog post. From a guy who was supposed to be working with them.

Marty Haught, the OSS Director, was not thrilled. He literally said in an internal Slack message: "I did not know of this until I read the post, which is disappointing. I'd love your thoughts on how we should respond. I was already planning on accelerating removing André but this seems to put that at a higher priority."

Beautiful. The OSS Director was already planning to "accelerate removing" the guy before RV even launched. That's not governance. That's a vendetta.

## The Access Disaster

So Ruby Central tried to offboard André and Sam. Remove their GitHub access. Revoke production server permissions. Clean break. Except here's the problem: Ruby Central didn't actually have direct control over the GitHub Business/Enterprise account. They had to ask Hiroshi Shibata (hsbt) to make the changes for them.

On September 10, 2025, hsbt removed André, Sam, and Martin Emde from the Business/Enterprise admin level. Downgraded their org permissions. Marty got added as an enterprise admin.

Then on September 16, 2025 — just six days later — they restored all access. Full rollback. Why? Because the maintainers threatened to retaliate. That's literally what the incident report says. "You should expect and be prepared for retaliation."

Are you kidding me? This is a professional open source foundation managing critical infrastructure, and they're making decisions based on fear of retaliation?

## The Walkout

Then on September 18, 2025, Ruby Central tried again. This time MartyHaught accidentally removed everyone completely from the GitHub organization instead of just downgrading their permissions. All access. Gone. Complete catastrophe. He sent an email saying "I messed up, and I accidentally removed all org access instead of downgrading."

Six developers quit on the spot. André, Sam, Ellen Dash, Josef Šimánek, Martin Emde, and Deivid Rodriguez. They walked out and published an open letter or whatever. The "maintainers" were gone.

And here's the thing — Ruby Central's official incident report admits they had no documented offboarding procedure. No runbook. No checklist. They were flying by the seat of their goddamn pants while holding the keys to one of the most important package repositories in the Ruby ecosystem.

## The Real Problem

Listen, I'm not taking sides here. Actually, no — I'm taking sides. Both sides are terrible.

Ruby Central handled this like a bunch of amateurs. They had no clear policies. They communicated like garbage. They let personal relationships and grudges drive decisions instead of process. Marty Haught was making it up as he went along, and the board let him.

But the maintainers aren't exactly innocent angels either. They held onto access like it was personal property. They created a shadow organization (Spinel Cooperative) to compete with the foundation that paid them. They expected to retain control even after leaving. That's not how open source governance works, and they know it.

The whole situation exposes the fundamental lie at the heart of open source "governance": these foundations have no actual authority. They can't enforce anything. They can't fire people effectively. They can't make hard decisions. They're just middlemen with checkbooks, and when the money runs out, the whole thing falls apart.

## The Aftermath

As of April 2026, there's still no resolution. Ruby Central published an "incident report" full of lessons learned — policies should be documented, communication should be clear, access changes should come with explanations. No shit, Sherlock. They're essentially writing a blog post about how they should have used Google Calendar.

Meanwhile, RV exists and is apparently fine. The Ruby ecosystem didn't collapse. People still push gems. Life goes on. But the trust is gone. The community is fractured. And nobody wins.

This is what happens when you mix volunteer labor, nonprofit governance, and critical infrastructure. You get this. You get petty fights about who gets to press the button. You get silent betrayals and public tantrums. You get a twelve-page incident report that explains, in exhaustive detail, exactly how everyone failed.

## The Lesson

If you're maintaining a critical open source project, here's what RubyGems Fracture teaches us:

First, document your goddamn offboarding process before you need it. Not after. Before.

Second, separate GitHub access from production access. They shouldn't be the same thing. The coupling is what caused half this mess.

Third, if someone's leaving, just let them leave. Don't negotiate. Don't threaten. Don't try to preserve your leverage. Just say "thanks for your work, good luck" and move on.

Fourth, and this is the hardest one: stop treating commit access like a prize. It's not a badge of honor. It's a responsibility. And when someone stops contributing, their access should reflect that — not because you're punishing them, but because you're protecting the project.

Ruby Central learned all these lessons the hard way. And the rest of us get to watch and take notes.

Now if you'll excuse me, I need to go check if my npm tokens are still valid.
