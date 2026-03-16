+++
title = 'Why I Reject Vibe Coding'
date = 2026-03-17T15:00:00Z
description = 'A case against treating code as disposable text when the real work is understanding, review, and responsibility.'
+++

I do not reject AI-assisted programming. I reject the specific attitude now marketed as vibe coding.

The phrase became popular as shorthand for a style of development where you prompt, accept, run, paste errors back in, and stop reading the code closely. The code is treated as an intermediate artifact that only matters if the screen appears to work. For a throwaway toy, that may be amusing. For software that other people depend on, I think it is irresponsible.

My objection is not moral panic and it is not nostalgia for artisanal suffering. I use AI tools. They are genuinely useful for summarizing unfamiliar code, drafting tests, suggesting refactors, explaining APIs, and accelerating repetitive work. Even vendor-sponsored research has shown real gains in perceived productivity and task completion speed. That part is not hard to believe. Of course a machine that emits plausible code instantly can make a developer feel faster.

The problem is that speed is not the same thing as software engineering.

If a tool helps me reach a first draft in half the time, that is valuable. If it also makes me less likely to understand what I am shipping, less likely to notice subtle errors, and more likely to leave behind code that nobody wants to maintain, then the apparent gain is only local. The cost has merely been deferred.

This is why I keep returning to one question: would I still deploy this if I were on call for it tonight?

That question clears away a lot of nonsense. A login flow, a billing rule, an admin tool with private data, a migration script, or a long-lived internal service does not become safe merely because a model produced the code quickly. Someone still has to own the failure mode. Someone still has to explain the system to the next developer. Someone still gets woken up when the cheerful demo turns into an incident.

Much of the more serious writing on this subject ends up in the same place. Simon Willison drew a useful distinction early on: not all AI-assisted programming is vibe coding. The critical difference is whether you still review and understand the generated code. Thoughtworks wrote persuasively in 2025 and 2026 that the real variables are probability, impact, and detectability. How likely is the model to be wrong here? How bad is it if it is wrong? How likely am I to catch it? Those are engineering questions. Vibe coding, at its worst, treats them as optional.

That is exactly why I reject it. It normalizes the removal of judgment from the one part of the process that most needs judgment.

There is also a category error hiding inside a lot of hype. People talk about coding models as if they were compilers for English. They are not. A compiler takes structured input and produces a predictable output. A language model infers a likely continuation based on patterns. Sometimes that continuation is excellent. Sometimes it is subtly wrong. Sometimes it is structurally wrong in a way that only becomes visible months later when the code has to change.

That difference matters. If I mistype a variable name, my tools usually tell me quickly. If a model introduces the wrong abstraction, duplicates logic that already exists elsewhere, writes overly broad tests, chooses a fragile dependency, or produces a security story that only looks convincing, the feedback loop is much slower. Those are the expensive mistakes.

This is one reason some of the more skeptical data is worth taking seriously. GitClear's large-scale analysis argued that the AI era is associated with more churn and less reuse in changed code. Even if one argues about the exact interpretation, the warning is familiar to anyone who has used these tools heavily: they are very good at producing more code, and not reliably good at producing less code. More code is not neutral. It increases review surface, maintenance cost, and the number of places bugs can hide.

I have seen the small-scale version of this myself. Ask for a narrow fix and you may get a broad rearrangement. Ask for a utility and you may get a tiny framework. Ask for a style adjustment and you may get fifty lines of redundant CSS. The output often works just enough to tempt you into acceptance. Then, a week later, you notice that the change introduced duplication, obscured the original intent, or quietly made the next edit harder.

That is the central danger for competent developers: not that the model always fails, but that it often fails in a flattering way.

It gives you something that feels complete before the thinking is complete. It gives you momentum before you have earned confidence. It gives management a story about acceleration before anyone has accounted for the downstream maintenance bill.

The same pattern appears outside AI marketing too. Developers have been warned for years about the hidden cost of speed: rushed decisions, weak review, and architecture chosen under deadline pressure eventually return as tech debt with interest. Vibe coding is that same old mistake with a new and more seductive user interface. It promises relief from drudgery, and then quietly asks you to suspend the habits that keep software trustworthy.

I also reject vibe coding because it confuses who the work is really for.

Code is not only written for the machine. It is written for future change. It is written for teammates, for incident response, for audits, for security review, for debugging, for migration, for the miserable afternoon when a requirement changes and the "temporary" shortcut is now business critical. If I cannot explain what a change does, why it exists, and what trade-offs it introduced, then I have not finished the work. I have only accelerated the typing.

This is where I part company with the more carefree version of the trend. I do not find it liberating to "forget that the code even exists". The code exists. The dependencies exist. The attack surface exists. The operational cost exists. The maintenance burden exists. Declaring indifference to those things does not remove them. It just assigns them to your future self or to a colleague who did not consent to inherit your vibes.

None of this means AI tools are worthless. It means they need a harness.

I want AI in the loop, not in charge. I want it drafting, searching, summarizing, and proposing. I want tests, diffs, type checks, review, and the right to throw away generated code that technically works but clearly does not belong. I want boring feedback loops. I want small commits. I want enough comprehension that I can defend a change in plain language.

If that sounds less magical than vibe coding, good. The magic is exactly what I do not trust.

My position is simple. Use AI where it reduces toil. Do not use it as an excuse to abandon ownership. The moment "I did not really read it" becomes an acceptable description of production code, the practice has stopped being engineering.

That is why I reject vibe coding. Not because I hate new tools, but because I still care about the code, and I still think somebody should.
