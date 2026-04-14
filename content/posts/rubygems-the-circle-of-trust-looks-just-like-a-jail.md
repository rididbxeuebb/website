---
title: 'Ruby Central Just Published Their Incident Report and Somehow Made It Worse'
date: 2026-04-14
description: "The RubyGems fracture was bad enough. The incident report? It's a masterclass in missing the point so completely that you actually worsen the damage."
---

I've seen a lot of open source governance disasters in my time. Like, a LOT. You'd think nothing surprises me anymore. You'd think I'd be numbed to it by now. You'd be wrong. Holy shit, you'd be so wrong.

Ruby Central just published their "incident report" for the September 2025 RubyGems fracture — the one where they quietly removed every single maintainer from the RubyGems GitHub organization and then had the absoluteAUDACITY to call it "strengthening stewardship" — and somehow, SOMEHOW, it's worse than the original incident.

Let me break down what happened, because if you've seen one open-source foundation destroy community trust, you've seen them all. Except somehow this one manages to be even more painful than the LibreOffice disaster I wrote about last week.

## The Setup: Another Foundation, Another Quiet Coup

So here's what went down. In September 2025, Ruby Central — the nonprofit that " stewards" the Ruby ecosystem (more on those quotation marks in a second) — decided to unilaterally remove every maintainer from the RubyGems GitHub organization. We're talking André Arko, Samuel Giddins, Ellen Dash (duckinator), and others. The people who have been/maintaining this critical piece of Ruby infrastructure for YEARS. Gone. Just like that.

No warning. No discussion. No "hey, maybe we should talk about this first." Just: boom, you don't have access anymore, thanks for your service, good luck with your career.

The official justification? "Supply chain security." That's the phrase they used. "We need to strengthen supply chain security." And I'm supposed to take that seriously? Really? Because it sounds like the exact same corporate speak that every failing foundation uses when they're about to do something incredibly stupid and want to dress it up in security theater.

The timing was absolutely chefs kiss: André Arko was literally ON CALL for the RubyGems.org service when they removed his access. The guy was responsible for keeping the gem registry running, and they locked him out while he was on duty. That's not security. That's active sabotage dressed up in compliance clothing.

## The Report: A Masterclass in Missing the Point

Fast forward to March 2026. Ruby Central publishes their "incident report" attempting to "provide closure." And oh boy. Where do I even start.

The report is written by Richard Schneeman, who — and I need you to understand how absolutely perfect this is — JOINED THE RUBY CENTRAL BOARD A MONTH AFTER THE INCIDENT. That's like asking the guy who started the fire to write the fire investigation report. The conflict of interest is so obvious it's not even funny.

But wait, it gets better. The report acknowledges that Ruby Central "lacked documented offboarding policies." Let me say that again: they removed maintainers from a critical piece of infrastructure WITHOUT ANY DOCUMENTED PROCEDURE. They just winged it. And somehow that's supposed to make me feel better? "Oh, don't worry, we just made it up as we went along and accidentally destroyed years of community trust!" GREAT. That's exactly what I want to hear from the people who control how Ruby developers install dependencies.

The report also explains that Ruby Central wanted to "cleanly offboard" Arko and Giddins after they announced they were leaving, but "lacked the structural ability to make this change." So the response to "we don't have the tools to do this properly" was "do it anyway and deal with the consequences later." That's not stewardship. That's a toddler having a tantrum and breaking someone's sandcastle because they didn't get exactly what they wanted.

## The Real Story: Corporate Pressure and Governance Capture

But here's where it gets actually interesting. According to reporting from The Register and other sources, the Ruby Central takeover wasn't just internal incompetence — there were ALLEGED external pressures. The allegations suggest that Shopify, a major corporate sponsor in the Ruby ecosystem, applied financial and governance pressure that effectively turned Ruby Central into a proxy for corporate interests.

Think about that for a second. A nonprofit that exists to serve the community was allegedly captured by corporate interests and used to forcibly remove the volunteer maintainers who built the infrastructure those corporations depend on. That's not a foundation. That's a weapon.

And here's the kicker: Ruby Central was already financially strained. A major sponsor (Sidekiq, allegedly) withdrew a $250,000/year commitment after Ruby Central "platformed" Rails creator DHH at RailsConf. So instead of addressing the funding problem transparently, they apparently decided to consolidate power by force. Nothing says "we value community governance" like quietly removing everyone who actually builds things when the money gets tight.

## The Aftermath: Nobody Wins

The result of all this? RubyGems now has a governance structure that makes decisions behind closed doors, former maintainers have forked the project (Spinel, the new Ruby tooling effort is reportedly in development), and the community is more fractured than ever. Also, Ruby creator Yukihiro Matsumoto ("Matz") reportedly said the RubyGems repository ownership should transition to the Ruby Core team while continuing to be managed by Ruby Central — which is exactly the kind of vague, noncommittal statement that tells you nobody actually knows what's going on.

What did Ruby Central accomplish here? They "strengthened stewardship" by making everyone less engaged. They "protected the supply chain" by breaking trust with the people who actually maintained it. They "improved security" by creating an environment where nobody wants to contribute anymore.

Meanwhile, the actual security of the Ruby gem ecosystem hasn't improved one bit. The difference now is that when something goes wrong, there's no community of people who actually care about the project left to fix it. Congratulations. You played yourselves.

## This Is Why Everyone Is Cynical About Open Source Governance

Here's my unfiltered take: this incident, the LibreOffice disaster, the OpenTofu license fights, all of it — it proves that "open source foundation" is often just a fancy way of saying "we want the benefits of community trust without any of the accountability."

Ruby Central claims to represent the Ruby community, but the Ruby community wasn't consulted before this decision. They claim to be stewards, but their stewardship has made the ecosystem LESS stable. They claim to improve security, but all they've improved is their own internal power at the expense of everyone who actually does the work.

Mike McQuaid, who helped mediate during the incident, put it best: "If your project hasn't argued about governance or money yet, it probably will one day. Be boring. Have a governance document."

The Ruby community had no governance document. They had trust. And Ruby Central burned that trust to the ground in less than a week.

At this point, I genuinely don't know what it takes to make foundation governance work. Every single "community-led" project that gets any significant corporate funding seems to eventually face this exact same crisis. The incentives just don't align. Foundations need money, corporations have money, corporations want influence, foundations give influence, contributors get踢ed out, everyone acts surprised when the project implodes.

Maybe the lesson is that critical infrastructure shouldn't be governed by nonprofits with no accountability. Maybe it's that we should stop pretending that "stewardship" is a substitute for actual community control. Or maybe the lesson is that some lessons will never be learned, and we'll keep watching this same disaster play out different settings forever.

Check your RubyGems version. Pin your dependencies. And for the love of god, don't trust any foundation that uses the word "stewardship" unironically.

They're not stewards. They're jailers.

And the circle of trust looks just like a jail.
