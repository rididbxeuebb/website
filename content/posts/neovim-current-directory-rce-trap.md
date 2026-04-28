---
title: 'Neovim’s `./?.lua` Default Is a Tiny RCE Gremlin'
date: 2026-04-28
description: 'A single search path entry turns “just require the module” into “please run whatever is sitting in the current directory.”'
---

Neovim has spent the last year doing a weirdly admirable thing: slowly admitting that “trust nothing by default” is not paranoia, it’s basic hygiene. `vim.secure.read()`. `:trust`. The Windows fix that stopped hunting for executables in the current directory. All good. All sane. All things a grown-up editor should do instead of acting like every folder on your disk is a polite little monastery.

And then there’s `./?.lua`.

That tiny gremlin is still sitting in Lua’s default search path, which means `require("notify")` is not just “load the plugin module if it exists.” It is “look in the current directory first and maybe execute some random local file you absolutely did not mean to trust.” If you open Neovim inside an untrusted repo — which, let’s be honest, is half the point of having an editor — you have now made the directory part of the code-loading machinery. That’s not a feature. That’s a trap disguised as ergonomics.

The issue was filed on April 11, 2026, and yes, it’s already been pushed toward the 0.12.3 milestone. Good. It should be. Because the attack story is insultingly simple: a plugin calls `require("notify")`, there’s no matching module on `runtimepath`, and Lua falls back to the current directory. If there’s a `notify.lua` sitting there, congratulations, your editor just did a little self-own with execution privileges.

And before anyone starts waving the `nvim -l` flag around like a priest with a bowl of holy water: yes, fine, that use case exists. Neovim can be a standalone Lua runtime. That does not mean the interactive editor mode should inherit the same search behavior like some cursed family heirloom. If a feature is only legitimate in one mode, confine it to that mode. That’s not hardening theater. That’s called not being a dumbass.

The thing that annoys me most is that Neovim already knows this class of mistake is poisonous. `exrc` got a trust database because auto-sourcing random project-local code was obviously too spicy to leave wide open. `vim.secure.read()` exists because “just execute the file” is how you end up with a machine that belongs to somebody else by lunchtime. The project has been making the right noises in the right direction. Which is why leaving `./?.lua` in the default path feels less like oversight and more like one of those little legacy landmines that everyone walks past because it’s technically somebody else’s problem.

Also, the fallback behavior is stupidly fragile in practice. A lot of plugin code does the reasonable thing and asks for optional dependencies with `pcall(require, ...)`. That’s normal. That’s boring. That’s exactly the kind of code you write when you want a plugin to work if a dependency is present and quietly limp along if it isn’t. But if the dependency name is common enough — `json`, `async`, `notify`, `utils`, pick your poison — then “quietly limp along” becomes “maybe load the attacker’s local file instead.” I have seen less elegant booby traps in shell scripts written by people having a nervous breakdown.

What makes this especially annoying is that the fix is conceptually boring. Don’t search the current working directory by default. Use the runtime path. Use explicit loading. Keep the standalone Lua runtime path if you absolutely must. Stop pretending ambient local-directory execution is a neutral convenience. It isn’t. It’s a security decision wearing a fake mustache.

And yes, this is me being petty, but I’m tired of tools acting like “current directory” is a sacred space. It’s not sacred. It’s where half-finished experiments, stale configs, test junk, and whatever garbage I pulled out of `/tmp` go to die. It should not be in the path to code execution unless a user explicitly opted into that risk with their eyeballs open and both hands on the wheel.

So my hot take is simple: interactive Neovim should treat the current directory like a suspicious stranger, not a trusted collaborator. If you want Lua modules, load them from known places. If you want trust, ask for it. If you want to execute random code from whatever folder you happen to be standing in, at least have the decency to say that out loud instead of smuggling it into `package.path` like a coward.

The editor is supposed to help you write code, not hand the keys to the first `notify.lua` it trips over.
