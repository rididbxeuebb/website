+++
title = 'Why I Would Not Use OpenClaw'
date = 2026-02-03T10:00:00Z
description = 'I would avoid OpenClaw because a personal assistant with broad integrations, host access, and remote surfaces creates too much privacy and security risk.'
+++

I would not use OpenClaw for a simple reason: I do not want a personal assistant with that much access to my messages, devices, browser, and local machine.

OpenClaw presents itself as a local-first assistant, but its own public documentation describes a system with a gateway, many messaging integrations, browser control, remote access options, device nodes, automation features, and host-level tools. That is not a small utility. That is a very large trust boundary.

To be clear, I am not claiming the project is malicious. My objection is that the privacy and security burden is too high for the category of software it wants to be.

Its documentation explicitly says inbound DMs should be treated as untrusted input. It documents pairing modes, allowlists, security guides, remote exposure, and more restrictive sandboxing for some sessions. I respect that honesty, but to me it proves the point. This is the sort of system where the safe configuration is already a serious operational concern.

That is enough for me to walk away.

If a tool can read or relay messages, drive a browser, interact with devices, expose a gateway, and run code on the host, then a mistake is no longer a small mistake. It becomes a privacy problem, a security problem, or both. Even if each individual feature is defensible, the combined surface area is more than I want in software that sits close to my personal communications.

I prefer tools that are narrow by default, isolated by default, and easy to reason about. OpenClaw appears to be broad by design. That may be attractive if you want one assistant to sit in the middle of everything. I do not.

For me, privacy-friendly software is not just software with documentation and options. It is software that does less, touches less, and requires less trust in the first place.

I would rather have a few smaller tools than one assistant that demands this much trust. That is why I would not use OpenClaw.
