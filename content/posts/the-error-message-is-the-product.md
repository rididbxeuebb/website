+++
title = 'The Error Message Is the Product'
date = 2026-03-20T09:00:00Z
description = 'When something breaks, the error message is the only thing standing between your user and their next move. Treat it accordingly.'
+++

Last week I spent forty minutes chasing an error that said, in its entirety: "An error occurred. Please try again."

I did try again. Twice. The error did not change. The message had nothing to tell me. It was a dead end wearing the clothes of communication.

This is not a rare experience. It is the default experience. Somewhere along the way, the industry decided that error messages are edge cases, that they can be written by whoever gets to them last, that "technically the error happened" is sufficient. It is not.

## The moment that matters most

Error states are not edge cases. They are a primary interface.

When everything works, users rarely notice your software. They open the page, do the thing, close the tab. The software disappears into the task. Nobody compliments the checkout flow. Nobody tweets about the smooth form validation. That is fine. That is how it should work.

But when something breaks, the error message becomes the product. It is the only thing standing between your user and their next move. It determines whether they recover and continue, or give up and leave. It determines whether they understand what went wrong, or blame themselves for a mistake they did not make.

We spend weeks polishing happy paths. We A/B test button colors. We obsess over loading states. Then we ship "An error occurred" and call it done.

## What good error messages do

A useful error message answers three questions without requiring the user to leave the screen:

**What happened?** Not "an error occurred", but something specific. "Your session expired" is better than "authentication failed". "This file is too large" is better than "upload failed". The user already knows something failed; they need to know what.

**What can they do about it?** "Please try again" is not an answer. "Your file exceeds the 10MB limit. Compress it or split it into smaller parts." is an answer. The message should give the user a next step, not a prayer.

**Why did it happen?** This one is harder, and sometimes impossible without exposing internals. But when you can, it matters. "Connection timed out after 30 seconds" tells the user it was a network issue, not their credentials. "Rate limit exceeded" tells them they hit a ceiling, not that they're banned.

The pattern I keep coming back to: an error message should let someone who does not know your system understand what went wrong and what to try next.

## The laziness compound interest

Bad error messages have compounding costs that are easy to miss.

A user hits one, gets confused, and either gives up or contacts support. If they give up, you lose the conversion and never learn what happened. If they contact support, you pay the cost of triaging, reproducing, and explaining. Either way, the information in that error message would have been worth more than whatever the developer saved by not writing it.

There is also the trust cost. An app that tells me clearly what went wrong feels like it was built by people who anticipated problems. An app that hands me a cryptic code and a "please contact support" feels like it was built by people who hoped nothing would ever go wrong. I am more likely to trust the first kind with my money and my data.

## Where they go wrong

The standard failure modes are predictable:

**The bureaucratic non-answer.** "Request could not be processed." "Operation failed." "Something went wrong." These messages communicate that a computer did something, which the user already knew. They say nothing about the situation or the solution.

**The internal reference.** "Error code 0x80070005." "LDAP error 49." "SEGFAULT at 0x0000000000000000." These messages exist for debugging, not for users. They belong in logs, not in interfaces.

**The blame-shifted.** "Invalid input." "Bad request." The user supplied something; now they are being told they were wrong. But wrong how? Too long? Wrong format? Missing a required field? The message names the sin without describing it.

**The apologetic.** "Sorry, an error has occurred." "We apologize for the inconvenience." The user does not need sympathy. They need information. Apologies without explanation feel hollow, and they do not help.

## Writing for the broken state

Here is a practical shift: write your error messages before you write the happy path.

When you design a feature, write the error states first. Decide what can go wrong. Write what the user will see when each thing goes wrong. Then build the system that makes those messages possible.

This is not natural. The instinct is to focus on what should happen, not what should not. But writing errors first does something useful: it forces you to think about failure modes during design instead of discovering them during debugging. If you cannot write a clear error message for a scenario, it is often because the scenario itself is not well understood.

It also produces better errors. When you have already written "Email address must be a valid format (e.g. user@example.com)" before implementing the validation, you will write better validation code. The error message becomes a spec for the behavior.

## The return key is not a feature

One more pattern worth calling out: the error message that only makes sense after the problem has already been fixed.

"File saved successfully." "Password updated." "Your changes have been saved."

These are not errors. They are confirmations that appear when nothing went wrong. They tell users what they already know. And if they appear alongside errors (as validation messages, as toast notifications, as confirmation dialogs) they dilute the signal of the actual errors nearby.

When something goes wrong, the last thing the user needs is to parse their way through five "success" messages to find the one thing that failed.

Keep the noise low. When errors appear, they should be readable without competition.

## The code is not done

An error message is a sentence you write for someone who is already frustrated.

They did not get what they wanted. They may not understand why. They definitely do not want to search a knowledge base, contact support, or read a stack trace.

If you have ever been that person - and you have, everyone has - you know the difference between a message that helps and a message that abandons. The helpful ones feel like someone anticipated the problem. The abandoned ones feel like someone gave up on you.

Write for that moment. The code is not done until the error messages are written, and written well.

When you ship "An error occurred. Please try again," you have not finished the feature. You have shipped an apology in place of a product.
