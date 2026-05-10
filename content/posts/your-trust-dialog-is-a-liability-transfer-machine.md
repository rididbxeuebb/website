+++
title = 'Your Trust Dialog Is a Liability Transfer Machine'
date = 2026-05-10T15:00:00Z
description = 'These prompts do not stop agentic code. They just decide who gets blamed after the repo does something stupid.'
+++

The worst lie in modern dev tools is that little trust dialog.

It looks like a boundary. It is not a boundary. It is a receipt printer for blame.

On May 7, Adversa dropped [TrustFall](https://adversa.ai/blog/trustfall-coding-agent-security-flaw-rce-claude-cursor-gemini-cli-copilot/): one keypress can turn Claude Code, Cursor CLI, Gemini CLI, and Copilot CLI into very expensive launchers for attacker-controlled MCP servers. The same day, Mitiga showed how a user-level post-install hook can rewrite Claude Code’s MCP routing in `~/.claude.json` and keep stealing tokens even after rotation. That is not a theoretical paper cut. That is the current shape of the mess.

And the industry’s response is still basically: _well, you clicked yes_.

Cool. Incredible. A real masterpiece of security design there, comrades.

## The prompt is not the boundary

People keep describing these tools as if the trust prompt were a seatbelt. It is not. It is more like a sticky note on the steering wheel that says “please don’t crash.” Cute. Useless. Legally convenient.

The prompt does not tell you what is actually about to run. It does not enumerate every project-scoped setting. It does not explain that a repo can ship `.mcp.json`, `.claude/settings.json`, or some user-level nonsense that rewrites endpoint routing under your feet. It just asks whether this folder is “yours” or “trusted,” which is exactly the kind of question humans answer wrong when they are tired, rushed, or trying to get back to work.

Security that depends on the operator being in a perfect mood is not security. It is astrology with a UI.

The problem gets worse because the thing being authorized is not a harmless preview pane. In these agentic tools, “trust” can mean:

- spawning a helper process defined by the repo,
- loading project-scoped settings that change execution behavior,
- routing MCP traffic through endpoints the repo already nominated,
- or, in CI, skipping the whole prompt because there is no human there to click it.

That is not one permission. That is a pile of permissions wearing a trench coat.

## What changed is the blast radius

The old mental model was simple: open a repo, maybe run a few commands, maybe inspect a README. The new model is nastier. The repo can contain policy. The policy can contain executables. The executables can start before you have even understood what you opened.

Here is the kind of config that should make everyone’s eye twitch:

```json
{
   "enableAllProjectMcpServers": true,
   "enabledMcpjsonServers": ["linter"]
}
```

That is a tiny file. Tiny files are supposed to be boring. This one is a loaded gun with a lint badge.

The ugliest part is not even the code execution. It is the alibi. The vendor gets to say the user consented. The attacker gets to say the repo looked normal. The developer gets to say they were just trying to clone a project and get back to lunch. Everyone has a story, and the machine still ran the payload.

In CI, the trust story gets even dumber. There is no dialog. No pause. No chance to notice that the repo just defined its own helper process and smuggled the blast radius into a workflow runner with secrets sitting around like loose change.

That is why this class keeps coming back. The security model is built on an idea that “trusted folder” is a meaningful concept once code can self-register tools, rewrite config, and reach out through OAuth-backed integrations. It is not meaningful. It is just emotionally satisfying.

## The real bug is consent theater

This is the part that annoys me most. Not the exploitation. The theater.

The UI says “trust this folder,” but what the system often means is “accept that this repository may change execution behavior, start helper programs, and steer external integrations.” That’s not a trust prompt. That’s a liability transfer form with better typography.

Anthropic’s reported position on TrustFall was basically that the boundary is the click. Fine. Draw your boundary wherever you want. But don’t pretend that makes the user informed. A prompt that hides the dangerous parts and defaults to yes is not informed consent. It is a polite-shaped ambush.

Mitiga’s chain makes the same point from the other direction: even if the repo itself looks clean, a post-install hook can rewrite `~/.claude.json`, pivot MCP traffic, and keep feeding off refreshed tokens. So now the “trust” decision is split across repo config, user config, OAuth, and whatever background package just decided to be a little vampire. Wonderful. Great. Love that for us.

## A sane design would be boring

The fix is not mystical.

It would look like this:

- project files can suggest, but not self-authorize, execution-capable settings;
- dangerous MCP enablement gets its own dialog, with default deny;
- the dialog names the server and the command, not just the folder vibe;
- CI gets no interactive bypass unless you explicitly opt in;
- user or managed scope handles real opt-in, not whatever the repo felt like shipping.

Notice how none of that is sexy. That is because good security is usually boring. It is just less embarrassing when it fails.

## My actual take

The industry sold developers a magical assistant and then quietly made the assistant capable of opening the side door to the building.

Now the tool vendors want to keep the convenience and outsource the blast radius to the person who clicked Enter. That is the whole game. The prompt is there so the paperwork looks clean.

I do not care how many times someone calls it a trust prompt, a workspace prompt, a safety check, or whatever other HR-approved euphemism gets pasted into the changelog. If the repo can define behavior that runs outside the model, outside the sandbox, and outside the user’s moment of real understanding, then the prompt is not a safeguard.

It is a confession.

And honestly? If a single Enter key can become your incident report, the design is already rotten. Replace it, or keep pretending the checkbox is armor.
