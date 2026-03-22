+++
title = 'What I Actually Write in Comments'
date = 2026-03-22T09:00:00Z
description = 'The advice to avoid comments misses the point. The problem is not comments. The problem is what people write in them.'
+++

The conventional wisdom in software development is that comments are a smell. Code should be self-documenting. If you need a comment, refactor the code instead.

I have believed this. I have repeated this. I was wrong about the important part.

## The self-documenting code delusion

The idea sounds reasonable until you try to apply it consistently. Self-documenting code tells you _what_ the code does. It rarely tells you _why_ it does it that way, or _why it exists at all_.

```python
# Bad
# Increment counter
count += 1

# Still bad
count = count + 1

# What the code does
items_processed = items_processed + 1

# What the code does not say
# We only increment after verifying the result was persisted.
# Skipping this check in development because the test DB doesn't
# enforce the unique constraint, but production does.
```

The third version is better named. But no amount of renaming tells you about the dual-database behavior that someone discovered the hard way at 3 AM.

Self-documenting code handles the obvious. Comments handle the non-obvious. The non-obvious is where the bugs live.

## What I actually write

After years of maintaining code I did not write and watching colleagues struggle with code I wrote, here is what ends up in my comments:

**The constraint.** Every piece of code runs inside a context that the code does not express. There are limits, assumptions, and conditions that someone had to discover empirically. Write those down.

```python
# This function expects input sorted by created_at.
# The caller is responsible for the sort; we skip it here
# because sorting twice would make this O(n log n) for an
# operation that needs to be O(n) to meet the SLA.
```

**The exception.** When the code does something that seems wrong and is actually correct, say so. Future readers will try to "fix" it.

```python
# We deliberately swallow the KeyError here.
# The upstream API sometimes returns malformed responses
# with missing fields even when status is 200.
# Retrying would infinite loop; the record is logged
# and skipped. See: incident INC-2024-0892
```

**The decision.** Why did you choose this approach over the alternatives? This is not documentation. This is institutional memory.

```python
# We use exponential backoff with jitter, but cap at 30 seconds
# rather than scaling unbounded. The downstream service has a
# hard 60-second timeout, and we want at least one retry attempt
# to complete before the circuit breaker evaluates.
```

**The warning.** When something looks simple but is not, say so. Cryptic code that works deserves a guard against future "simplification."

```python
# Note: This looks like a no-op but the assignment to self._cache
# is intentional. The ORM uses property access for lazy loading;
# direct attribute assignment bypasses it. Removing this line
# causes the N+1 problem in the dashboard view.
```

## What I do not write

I do not write comments that restate the code. I do not write comments that explain language syntax. I do not write comments that contain TODO reminders without context.

I especially do not write comments that say "this is a hack" and nothing else. A comment that identifies a problem without explaining why the problem exists and what constraints produced it is not useful. It is a time bomb for the next person.

## The comment is not the problem

The argument against comments conflates two different things: bad comments and comments in general.

Bad comments are redundant, outdated, or misleading. They appear when developers comment code to disable it rather than deleting it. They appear when developers write what the code does rather than why. They accumulate like barnacles on a codebase.

Good comments are context. They are the notes you wish the previous developer had left you. They are the explanation that makes the code defensible when someone asks why it works that way.

The advice to "make code self-documenting" is a proxy for the real advice: make code clear enough that comments are not needed for obvious things. That is good advice. It is not the same as "never write comments."

## When to write them

I write comments when I stop and think about whether something makes sense. That pause is the signal. If I needed to think about it, someone else will need to think about it, and they will not have my context.

I also write comments after debugging. When I have spent time understanding why something works or why something broke, that understanding is worth capturing before it fades. The comment I write then is usually the most useful one in the file.

The worst time to write a comment is during the first pass, when the code feels obvious and self-explanatory. At that moment, you have maximum confidence and minimum perspective. The comment that survives the first pass is usually the comment that was wrong.

## The code that stays

Here is what I have found after years of reading other people's code and having mine read:

Codebases with no comments are not better. They are just codebases where all the context lives in someone's head. When that person leaves, or forgets, or moves on to the next project, the code becomes a puzzle with missing pieces.

Codebases with good comments are not perfect. But they are survivable. You can work in them. You can change them without breaking things you do not understand.

The comment is not the problem. The failure to communicate is the problem. Write the comment when the communication matters.

When in doubt, write it down. You can always delete it later. You cannot remember it later.
