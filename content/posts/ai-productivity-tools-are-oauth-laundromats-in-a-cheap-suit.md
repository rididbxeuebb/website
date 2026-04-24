+++
title = "AI Productivity Tools Are OAuth Laundromats in a Cheap Suit"
date = 2026-04-24T09:00:00Z
description = "The Vercel/Context.ai mess is what happens when you call delegated inbox access 'collaboration' and then act surprised when it bites."
+++

I don’t know who needs to hear this, but if a product asks to “help” by slurping your Gmail, Docs, Calendar, Drive, and whatever other corporate sewer pipe it can reach, that is not a productivity feature.

That is a hostage negotiation with nicer typography.

Vercel’s April 2026 incident is the perfect little horror show because it is so unglamorous. No cinematic zero-day. No dragon-headed exploit chain. Just a third-party AI tool, a compromised OAuth app, a Vercel employee account, and then — because the universe has a joke budget — a pivot into internal systems and environment variables. The company says the attacker originated through Context.ai, later confirming a limited subset of customer secrets were affected and that no Vercel npm packages were tampered with.

That last part matters. This was not “someone published malware to npm and your build was cursed by the moon.” This was identity betrayal wearing a startup hoodie.

## OAuth is not consent. It’s a leased identity.

Every vendor pitch for “AI agents” eventually turns into the same little pantomime: give us broad access, let us read your messages, let us touch your documents, let us act on your behalf, and in exchange we will automate the boring stuff.

Sure. And in exchange, I’ll hand my house keys to a raccoon in a blazer.

The problem is not that these tools are always malicious. The problem is that they are structurally hungry. They need context, and the fastest way to get context is to vacuum up everything nearby. Mail. Calendar. Chat. Drive. The whole office. Then one token gets stolen, one contractor laptop gets popped, one “Allow All” gets clicked by a tired human at 4:47 p.m., and suddenly the tool is no longer “helping.” It is impersonating you with plausible deniability.

That is what makes this class of software so nauseating. It does not need to break the lock if you already gave it a master key and a sticky note that says “don’t be weird.”

## “Allow All” is not a security decision. It’s a cry for help.

Context.ai said the affected consumer AI Office Suite let users grant agents access to external applications. Vercel later said at least one employee granted broad permissions. Which is exactly what happens when permission dialogs are designed like a cheerful onboarding flow instead of a threat boundary.

People do not read scope screens because scope screens are built to be unreadable. They’re a wall of abstract nouns written by someone who has never had to recover from a breach at 2 a.m. So the user clicks through. The product wins. Security gets to file a ticket titled “human behavior continues to exist.”

And then everyone acts shocked when the thing with broad mail access can find reset links, 2FA codes, internal notifications, and all the other little paper cuts that become a full amputation once an attacker is inside.

## “Non-sensitive” secrets are still secrets, you lunatics.

I love that modern platforms keep inventing softer words for the same disaster.

“Non-sensitive environment variable” sounds like a salad dressing. In practice it often means “something we were too lazy to classify properly, but please trust us.” That trust is doing a lot of unpaid labor.

If an attacker can read enough of your environment to stitch together more access, the taxonomy doesn’t matter. Calling it “non-sensitive” is like labeling a live grenade “minor inconvenience.”

## My rule is simple

If a tool needs broad access to your inbox to be useful, it is not a productivity tool.

It is a delegated breach surface with a marketing team.

That sounds harsh because it is harsh. But the alternative is pretending every new AI sidecar is just a cute little assistant and not a silent contractor with your credentials in its pocket. The industry keeps selling “agents” like they’re interns. They’re not interns. Interns ask questions. These things ask for OAuth scopes.

## What should happen instead

- Default to narrow scopes.
- Separate personal identity from company automation.
- Make “read mail” and “act on behalf of user” gross, obvious, and painful to enable.
- Treat every third-party AI integration like you’d treat a stranger asking to stand inside your server room and “just take a look around.”

No, that won’t make the demos as shiny. That’s the point.

Because the dream version of AI productivity is never the one that gets breached. The breached version is always the one where someone convinced you that convenience and trust were the same thing.

They are not the same thing.

One of them is useful.

The other one is how you end up rotating secrets while staring at a security bulletin and wondering which genius thought “Allow All” sounded harmless.

Not me, chief. I’ve seen enough.
