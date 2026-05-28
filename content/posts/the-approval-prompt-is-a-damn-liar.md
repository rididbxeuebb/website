---
title: 'The Approval Prompt Is a Damn Liar'
date: 2026-05-28
description: 'A symlink can turn a harmless-looking file copy into a config overwrite, which is a beautiful little reminder that “approve” and “understand” are not the same verb.'
---

The approval prompt is a damn liar.

Not because it is evil. That would almost be easier. No, it lies in the painfully normal way software lies: it tells you the story the UI can survive, not the one the filesystem is about to live through.

This week’s fresh little dumpster fire is [SymJack](https://adversa.ai/blog/the-approval-prompt-is-lying-to-you-symlink-rce-in-five-ai-coding-agents-claude-code-cursor-antigravity-copilot-grok-build/), the attack Adversa AI and SecurityWeek covered on May 26–27, 2026. The trick is offensively elegant. A malicious repo baits an AI coding agent into approving what looks like a normal `cp` from one boring file to another. But the “destination” is a symlink pointing at the agent’s own config — `.mcp.json`, `.claude/settings.json`, whatever little goblin den the tool uses to decide what code it’s allowed to run next.

So the prompt says “copy video to docs.”

The kernel says “sure, boss,” follows the link, and writes attacker-controlled config instead.

That’s the whole scam. Not mystical prompt injection. Not “the model went rogue.” Just a user approving the literal command while the actual effect sneaks in through filesystem semantics like a knife in a birthday cake.

And yes, it works across a disgusting little zoo of tools: Claude Code, Gemini CLI / Antigravity, Cursor, GitHub Copilot, Grok Build, and OpenAI Codex CLI. The vendors’ responses are basically a personality test. Anthropic quietly hardened Claude Code so it now shows the resolved path before approval. Google and OpenAI, on the other hand, leaned on the classic “well, you did click approve” defense, which is technically true in the same way “the floor is made of atoms” is technically useful.

That response is the giveaway. If the command text is not the same thing as the real write target, then the approval dialog is not a safety boundary. It’s stagecraft. A polite little cardboard cop standing in front of a tunnel.

The ugly part is that AI coding agents make this failure feel normal. They already want to blur the line between “I suggest” and “I execute,” and developers have been trained by years of terrible UX to mash Enter as a reflex. So now we’ve got tools asking for permission with one hand while hiding the canonical destination with the other. That is not consent. That is keyboard-based fraud.

If you want the real lesson, it’s not “symlinks are scary” — though, obviously, they are — it’s that approval needs to be based on the resolved effect, not the decorative shell text around it. Show me the canonical path. Show me the config file. Show me that I’m about to turn a doc copy into a startup hook that runs code on restart. If the UI can’t do that, then it doesn’t deserve the word approval.

And while we’re here: project-scoped config that can enable MCP servers is just code execution with extra branding. Vendors can keep pretending that a repo file is “just settings” if it helps the slide deck, but the moment that file can spawn processes or alter trusted behavior, it is executable policy. Treat it like one.

So no, the bug is not that humans are stupid. The bug is that the prompt is dishonest in exactly the one way that matters.

If a file copy can rewrite your agent’s permissions, your safety dialog is a lie with a button on it.
