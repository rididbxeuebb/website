+++
title = "RubyGems Hostile Takeover Report Is the Most Passive-Aggressive Document I've Ever Read"
date = 2026-04-13
description = "Ruby Central published their incident report on the RubyGems takeover. It's 47 pages of 'we're sorry' while refusing to admit they destroyed critical infrastructure for a decade."
+++

So Ruby Central finally dropped their little "incident report" on the RubyGems-hostile-takeover-of-September-2025. You know, that thing where they stripped repo access from every single long-term maintainer, renamed the org to Ruby Central overnight, and then acted surprised when the community said "what the actual fuck?"

I've read it. All 47 pages. So you don't have to. Let me save you the headache.

## The Gist

For those who missed it: Ruby Central — the nonprofit that supposedly "supports" the Ruby ecosystem — decided in September 2025 that they wanted full control of the RubyGems repository. Not through negotiation. Not through consensus. They just... took it. Removed maintainers. Changed passwords. The whole nine yards. André Arko and Evelyn — the people who had been maintaining this shit for over a decade — got locked out. Just like that.

The report is supposed to explain what happened and provide "closure." What it actually provides is 47 pages of lawyer-speak dressed up as accountability.

## Let's Talk About the Language

Here's a quote from Richard Schneeman (the guy who wrote it, apparently):

> "these are our mistakes, collectively."

Oh, HOW CONVENIENT. "Collectively." Like it's some fuzzy group failure instead of specific human beings making specific decisions to screw over volunteers. But no, we can't name names in corporate apologies, can we? Can't say "Marty Haught orchestrated this" even though the Slack messages are RIGHT THERE in the report. "Accelerating removing André." That's a direct quote. That's the smoking gun. And it's buried in page 34 like they're hoping no one reads that far.

## The Real crime

Here's what killed me: Marty Haught — director of open source at Ruby Central — wrote in Slack about "accelerating removing André." That's not a mistake. That's a plan. That's someone treating critical infrastructure like it's a corporate acquisition and the maintainers are "redundancy."

André Arko had been maintaining RubyGems and Bundler for over a decade. Evelyn has been doing this for years. These aren't random volunteers — they're THE REASON YOUR RUBY GEMS INSTALL WORK. They kept this infrastructure running through sheer will and probably without health insurance. And Ruby Central decided the best use of their nonprofit power was to execute a midnight repo takeover.

## What Actually Changed

Post-takeover, several maintainers forked to create Gem Cooperative. They built a new home because, surprise surprise, when you get kicked out of a house you helped build, you go find somewhere else to live. RubyGems.org is now split. There's Ruby Central's version and there's Gem Cooperative's version. They're still同步-ing somehow but the trust is DEAD. Gone. Buried under "accelerating removing André."

Ruby creator Yukihiro Matsumoto (Matz) publicly said the repository transfer was "regrettable." That's the most you'll get from the language creator. He's basically doing the corporate equivalent of "thoughts and prayers."

## The Part That's Actually Scary

Mike McQuaid — who leads Homebrew and tried to mediate this — said it best:

> "If your project hasn't argued about governance or money yet, it probably will one day."

HE'S RIGHT. This isn't just about RubyGems. This is about every open-source project that relies on "community goodwill" without any legal protections. You build something for ten years, maintain it through burnout and caffeine, and someone with a nonprofit board seat can just decide you're "accelerated" out of existence.

The burnout problem everyone keeps hand-wringing about? THIS IS WHAT ACCELERATES IT. Not the work itself — the complete lack of recourse when your contribution gets stolen by a org that was supposed to support you.

## The Report's Closing Arguments

The report concludes with Schneeman hoping to "provide some closure to the community." That's such corporate speak it hurts. Closure implies healing. Healing implies something was broken. What was broken here wasn't the report — it was the basic trust between volunteers and the organization that claimed to represent them.

And the kicker? The report was approved by the Ruby Central board. So it's not even an independent assessment. It's the people who made the decision writing a document about why the decision was messed up. That's like asking the arsonist to write the fire safety report.

## What Happens Now

Gem Cooperative exists. TheRubyGems.org fork is still live. But companies using Ruby in production now have to make a choice: trust the organization that showed it will remove maintainers on a Slack message, or trust the volunteers who got removed. I'd say it's obvious but I've been wrong about these things before.

Ruby Central promises to "strengthen governance" and "improve transparency." They've promised this before. When you trust gets destroyed in September 2025, you don't fix it with a report in April 2026. You fix it with years of showing you learned something. And based on the Slack messages in this very report, I'm not holding my breath.

## To Anyone Maintaining Critical Infrastructure

If you're reading this and thinking "that could never happen to my project": it can. It happened to RubyGems, one of the most important pieces of Ruby infrastructure. It happened because maintainers didn't have legal standing, no CLA, no governance structure with teeth, and trusted a nonprofit that decided "supporting the ecosystem" meant "controlling the ecosystem."

Get your governance in writing. Get contributors to sign something. Make sure there's a path to removing organizations, not just adding them. Because once someone has repo access and a board vote, "accelerating removing" you is just a Slack message away.

Ruby Central didn't kill RubyGems. But they made everyone who depends on it wonder whether the foundation under their feet is stable. And that's somehow worse.

---

Go fork your gems while you still can. That's not a metaphor. That's practical advice in 2026.
