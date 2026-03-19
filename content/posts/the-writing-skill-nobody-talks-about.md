+++
title = 'The Writing Skill Nobody Talks About'
date = 2026-03-19T09:00:00Z
description = 'On the craft of clear technical communication and why it matters more than any framework you will learn this year.'
+++

A senior engineer on a previous team once told me that the best developer he ever worked with could explain a distributed systems problem in two paragraphs. Not because he dumbed it down. Because he understood it so well that nothing else was needed.

I have thought about that person many times since. Not because of the technical skill, though it was considerable. Because of the writing.

Most developers treat writing as a tax. The README is a formality. The commit message is whatever the CLI suggested. The design doc is a box to check before the meeting. The post-mortem is damage control.

This is a mistake that compounds over a career.

## What writing reveals

When I read a poorly written pull request description, I learn something about the author that has nothing to do with code quality. I learn that they have not fully thought through what they built or why. The code may work. The thinking behind it has not been pressure-tested.

Good writing is not decoration. It is compression. It forces you to resolve ambiguity before you hit publish. When you write "this handles edge case X by doing Y," you either understand that claim or you do not. The act of writing reveals the gaps.

I have seen this in reverse too. Developers who write clearly tend to write code that is easier to follow. The discipline transfers. If you care enough about making a point in prose, you probably care enough about naming a function well.

## The documentation problem

Teams that struggle with documentation usually do not have a documentation problem. They have a writing problem.

It is not that nobody wants docs. It is that nobody wants to write them badly, and the skills that produce good documentation are the same skills that produce good code: clarity, structure, ruthless editing, and a clear sense of who the reader is.

I have sat in meetings where engineers argued for an hour about architecture, then went home without writing a single word about it. The decision lived in their heads, not in a shared medium where the next person could find it.

This is how knowledge disappears from a team. Not dramatically. Not because anyone withheld information. Because nobody wrote it down with enough care that it survived contact with the future.

## Comments as thinking tool

Code comments get a bad reputation because most of them are useless. They state what the code does in English when the code already states that. They go stale. They lie.

But the alternative is not to stop writing comments. It is to write different comments.

The comments worth writing explain why something exists. They capture the trade-off that was made, the constraint that drove the design, the assumption that might break. They are not documentation of the code. They are documentation of the decision.

```python
# We use retry with exponential backoff here, but cap at 5 seconds.
# Longer delays cause the upstream service to close connections,
# which defeats the purpose. See incident report from March.
```

That comment is worth writing. The decision it describes is not obvious from the code. Without the explanation, the next developer changes the cap, the connections close, and nobody knows why.

## What I actually mean

There is a version of conciseness that is just brevity without clarity. You can write three words that mean nothing. You can also write three paragraphs that say less.

The skill is not writing less. It is writing precisely. It is choosing the word that means exactly what you mean and no more.

I have started treating every piece of technical writing as a small engineering problem. What is the output? Who reads it? What do they need to do after reading? What assumption might they make that is wrong?

The constraints clarify the prose. A commit message that answers "why this change" and "what changed" is already better than ninety percent of what I see. A post-mortem that names the specific failure mode and the specific fix is already useful. A README that explains what the project is for, who it is for, and how to get started is already an exception.

## The harder skill

Writing is a proxy for thinking, and thinking is the skill that actually matters.

Developers who write clearly think clearly. Not always, but often enough that the correlation is worth noting. The discipline of making an argument in prose, of anticipating counterarguments, of stating assumptions, of editing ruthlessly until only the necessary parts remain, is the same discipline that produces good software.

You can learn every design pattern, every framework, every tool that ships this year. You will still need to explain your work to someone who was not in the room when you built it. You will need to write the message that prevents a production incident. You will need to make the case for why the architecture should change.

None of that is solved by a better IDE.

## What I am not saying

I am not saying that great writers make great engineers. The skills are related but not identical. Some excellent engineers write terribly, and some excellent writers cannot debug a segmentation fault.

I am also not saying that you need to write essays every day. That is not the point.

The point is that writing is not optional infrastructure. It is part of the work. The commit message is part of the commit. The comment is part of the code. The documentation is part of the feature.

When you treat writing as afterthought, you ship incomplete work. The code may be correct. The thinking may be sound. But if nobody can understand it, if the next developer has to reverse-engineer your decisions from the code alone, you have left the job half done.

The best developers I know are also good writers. Not great novelists. Not literary stylists. But people who can explain a problem clearly in plain language. People who know how to cut a sentence until it says only what it needs to.

That skill is worth developing. It does not require a course or a book or a new tool. It requires only that you start treating your words as carefully as you treat your code.

And that is a choice you can make today.
