+++
title = "Cal.com Didn't Kill Open Source. It Killed a Fantasy."
date = 2026-04-18T09:00:00Z
description = "Cal.com going private is what happens when a public repo stops pretending it can also be your security model."
+++

The loudest thing about Cal.com going private is not the repo move.

It’s the fact that a lot of people still treat public GitHub like some sacred little force field. Push code into the light and, apparently, all the bad stuff is supposed to get embarrassed and leave. Cute idea. Absolute nonsense.

Cal.com is not a toy library. It handles bookings, calendar sync, OAuth tokens, team scheduling, PII, and all the other delightful nonsense that turns a SaaS into a box of knives. In January, Gecko Security reported a chained exploit path that could lead to account takeover and booking exposure. In April, Cal.com said the quiet part out loud: the core production codebase is moving private, while Cal.diy stays public as the community edition.

That is not a betrayal. That is a grown-up deciding the lunch table is no place to store the family silver.

## Public code is not the boundary

This is the part people keep tripping over like idiots in the dark.

Open source is a distribution model. It is not a security architecture. It is not a moral covenant. It is not a magical ward that repels the kind of people who would happily chain together auth bugs, IDORs, bad route handling, and a few hours of patience.

If your product is a scheduler, not a compiler, the source tree is not the whole game. The real attack surface is the live service, the data flows, the auth logic, the deployment pipeline, the keys, the workflows, and the sloppy little assumptions everyone forgets because the repo has a README and a GitHub Actions badge.

Cal.com’s move makes sense because it draws a line between community code and production code. Cal.diy stays open and MIT-licensed. The commercial plumbing, enterprise bits, and the sensitive guts that make the hosted product a business instead of a hobby get tucked away where random internet goblins can’t diff them at 3 a.m.

## The internet hates nuance, so here’s the blunt version

No, this does not mean closed source is suddenly holy.

Hiding code does not fix broken auth. It does not fix dumb ACLs. It does not fix route handlers that think they are private because somebody named them `_get.ts` and felt clever. It just removes one layer of convenience for attackers and one layer of comfort for people who like the idea of openness more than they like taking care of users.

And yes, I get why this makes people itchy. Open source folks have spent years hearing that transparency is the answer to everything. Then AI shows up and starts chewing through public codebases like a raccoon with a stolen debit card, and suddenly the old sermon sounds a little thin.

The point is not that secrecy wins. The point is that pretending every production system should be a public exhibit is stupid when the system holds real user data and the threat model got nastier.

## The compromise is ugly, and that’s fine

What Cal.com did is ugly in the way real engineering decisions are ugly.

They kept the community edition public. They stripped the enterprise organs out of it. They backported security fixes. They preserved a path for self-hosters who want the software without the whole commercial machine bolted onto it. That is less sexy than “open source forever” and less dramatic than “open source is dead,” which is probably why it’s the right answer.

The fantasy that died here is the one where a public repo is automatically the virtuous choice for every product. Sometimes the honest move is to say: this part is shared, this part is not, and the reason has nothing to do with vibes and everything to do with keeping customer data out of the hands of whoever is currently having a very productive afternoon with an AI-assisted scanner.

So no, Cal.com didn’t kill open source.

It just reminded everybody that public code is not a sacrament, security is not a personality trait, and your production repo does not need to be a public shrine to prove you’re a good little open-source citizen.

That’s a useful lesson, even if it bruises the ego of the terminally online.
