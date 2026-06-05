---
title: 'The Reports Got Better and That Was the Problem'
date: 2026-06-05
description: 'curl’s bug bounty didn’t die from obvious slop. It died from plausible, high-volume homework that still has to be read by a human.'
---

The worst thing AI did to curl wasn't the slop. It was learning manners.

For a while, the reports were easy to hate. They were bloated, hallucinated, and wrapped in the kind of fake urgency only a model can produce after being told to find a vuln and sound brave about it. Daniel Stenberg said curl’s bug bounty had already delivered 87 confirmed vulnerabilities and more than $100,000 in rewards before 2025 turned the inbox into a landfill with a security badge. So he shut the bounty down at the end of January. Sensible enough. If your triage queue starts smelling like hot garbage, you stop pretending it’s a garden.

Then the reports got better. Not good. Better. And that is so much worse.

By April, curl was in what Daniel called the “high quality chaos” era: report volume was running at roughly double the 2025 rate, the project was seeing more than one security report per day, and the confirmed-vulnerability rate had climbed back into the 15–16% range. In other words, the dumb noise thinned out and the machine started producing believable work. The new problem wasn't obvious nonsense. It was convincing nonsense with better formatting and a stronger sense of self-importance.

That sounds like progress until you remember who has to read the damn things. A better report is still a tax if every one of them needs to be verified, reproduced, scoped, patched, and explained. The bottleneck was never "can AI find bugs?" The bottleneck was always "can humans survive being the last mile of every bug the model can hallucinate into existence?"

curl is now getting more than one report a day on average, and Daniel has been blunt that the pressure is no longer just technical. It’s mental. It eats weekends, eats focus, eats the thin little layer of patience that keeps maintainers from walking into the sea. And the reports don’t just arrive; they arrive dressed like work. That’s the real trick. A garbage report is easy to laugh off. A polished report makes you read it. That’s where the cost lives.

The AI cheer squad loves to talk about discovery like it’s the whole game. It isn’t. Discovery is cheap. Judgment is expensive. A model can drag an old bug out into the light in thirty seconds and leave a human to spend three hours proving whether it matters, whether it’s exploitable, whether it’s a duplicate, and whether the person on the other end actually deserves a reply or a kick in the shin.

That’s why the curl story matters. Not because AI found bugs. Humans found bugs before AI and will keep finding them after the current token circus burns off its own eyebrows. It matters because AI made bug reporting scalable without making triage scalable. That’s the actual scam. The machine learned to write in a respectful tone and we still ended up with a pile of work nobody asked for.

So no, the lesson isn't "AI is useless." The lesson is uglier: AI can be right and still be a burden. It can be technically excellent and operationally toxic. It can improve the signal and still bury the humans under enough signal that the work becomes a kind of polite harassment.

If you want a heroic takeaway, try this one: stop mistaking better output for lower cost. The cost just moved. It always does. And right now it’s sitting in the maintainer’s chair with a stack of reports, a dead stare, and a calendar full of unpaid anguish.

Maybe the next thing AI learns is how to pay for therapy.
