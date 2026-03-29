---
title: 'NEOVIM 0.12 IS OUT AND I CAN FINALLY STOP LIVING LIKE A ANIMAL'
date: 2026-03-30
description: "The biggest upgrade since sliced bread. No more Press ENTER. Built-in plugin manager. LSP out of the box. My fingers are shaking. This is the day we've been waiting for."
---

Listen up you magnificent bastards, I'm typing this with hands that won't stop trembling because Neovim 0.12 just dropped and I cannot - I _cannot_ - process what's happening. My brain is currently a Discord nitro subscriber who just got their account back after being hacked. I'm vibrating at a frequency that would make a theremin weep. This isn't a release, this is a goddamn **miracle**.

## The Death of "Press ENTER"

You know that feeling? You're chugging along, blazing through some code like a caffeinated demon, and then BAM - some bullshit message pops up and there's that SOB waiting for you like your ex at a party you didn't know they'd be at. "Press ENTER to continue" staring at you like it's entitled to your time, your keystroke, your _existence_. You've hit Enter so many times in your life it should have a restraining order against you.

**GONE.** Just _gone_. Like your will to live on a Monday morning. Neovim 0.12 is out here murdering "Press ENTER" and I'm supposed to stay calm? I'm supposed to write a normal article? **I CANNOT BE NORMAL ABOUT THIS.** This has been haunting us since the beginning of time, probably longer, maybe since the first Vim user looked up at their terminal and screamed into the void. And now it's just... not there anymore. Poof. Dissolved. Deleted from existence like my will to go to the gym after January 3rd.

The pager used to trap you. Force you into this weird hostage situation where you'd type commands you didn't want to type just to get the hell out. Now? Now you just keep vibing. You stay in flow state like you're supposed to. This is the equivalent of your OS finally letting you close a notification without clicking "Remind Me Tomorrow" fourteen times. This is **freedom**.

## vim.pack: The Plugin Manager That Doesn't Make You Want to Uninstall Your CNS

And then there's `vim.pack`. The built-in plugin manager. I read that phrase and I feel like I'm dreaming. I've been using lazy.nvim for years and I love it, I really do, but the idea of having a plugin manager BAKED INTO THE EDITOR ITSELF is making me feel some type of way.

Listen - I'm not a man who gets emotional about package managers. I've used npm. I've used pip. I've used cargo. I've used the void package manager on void Linux which literally requires you to become an archaeologist to solve dependencies. But `vim.pack`? This little beauty right here?

It's minimal (496 LOC apparently, which is absolutely nothing in a text editor), it's native, it's Lua, it handles dependencies, it has a confirmation buffer that shows you exactly what's about to happen before you commit, and it even has a **built-in LSP server** running inside Neovim itself just to show you structure in that confirmation buffer. I'm not even kidding. The gang at Neovim put a whole LSP server in the plugin manager to show you plugin changelogs in their full glory. That's the kind of energy that makes you want to run through a wall.

```lua
vim.pack.add({
  'https://github.com/nvim-treesitter/nvim-treesitter',
  'https://github.com/neovim/nvim-lspconfig',
  'https://github.com/neovim/neovim',
})
```

THAT'S IT. THAT'S THE CONFIGURATION. No more downloading lazy.nvim, no more wondering if your plugin manager is going to break with the next update, no more reading docs that assume you're a maintainer of said plugin manager. You just add plugins like it's nothing. Like it's a language server. Because it IS nothing now. It's just... part of the editor. The way it should have been. The way god intended when they invented text editing all those centuries ago.

And the interactive update workflow? You run `vim.pack.update()`, you get a buffer showing you every single change, you can browse through plugins with `]]` and `[[`, you can pick and choose what to update, what to skip, what to delete - and it's all right there. No terminal running. No external process. You're inside Neovim managing Neovim using Neovim's own LSP and it feels like the future. It feels like we've been living in caves and someone just showed us fire and also the fire does your dishes.

## The Year of Nvim OOTB (Out Of The Box)

The theme for 0.12, as the roadmap calls it, is "The year of Nvim OOTB" and I am not exaggerating when I say this might be the biggest leap forward since Neovim added native LSP support in 0.5. We're talking about an editor that now gives you:

- **Native LSP**: You're already using LSP in 0.11, but 0.12 makes it even smoother. `vim.lsp.config` is mature, you just drop configs in `~/.config/nvim/lsp/`, and Neovim figures out the rest. Server detection, automatic root directory finding, handlers - all working out of the box with zero plugins needed for basic functionality.

- **Treesitter range highlighting**: They rewrote tree-sitter to use range-based callbacks instead of line-based, meaning on long lines (looking at you, generated protobuf files that are 10,000 characters on one line) it's not iterating through the entire thing anymore. Performance went from "my laptop sounds like it's about to achieve liftoff" to "oh, that's smooth." This is the kind of change that doesn't sound sexy in release notes but makes you actually FEEL the difference when you're navigating some abomination of a file.

- **Lua remote plugin host**: Remember when you installed a Python plugin and had to run `:UpdateRemotePlugins` and it felt like you were performing surgery on your config? That's gone. The remote plugin concept got redesigned completely. It's Lua all the way down now and it Just Works. You install a remote plugin, you restart, it's there. No ceremony. No ancient Vimscript dance. Just functional, like a bathroom that actually has toilet paper.

- **UI connect/restart**: You can now detach from a Neovim session and reattach from somewhere else. This is huge for people using Neovim over SSH, in tmux, or anyone who wants their editing environment to follow them like a loyal but moderately possessive dog. `:connect`, `:restart` - simple commands that unlock massive workflow possibilities.

- **No more "Press ENTER"** - yes I'm mentioning it again, I will mention it in my obituary, this was that important to me.

## What This Actually Means

Picture this: You install Neovim 0.12 on a fresh machine. You don't install lazy.nvim. You don't install packer. You don't install any plugin manager at all because you don't need one. You just add three lines to your init.lua using `vim.pack.add()` for some treesitter parsers, an LSP config, and maybe one nice colorscheme plugin. You open the editor. You write code. The LSP works. The highlighting works. The completion works. The diagnostics appear like magic. You don't debug your plugin manager. You don't wonder why something isn't loading. You don't go to Reddit to ask "why is my config broken after update" because there's nothing to break - it's all core now.

This is what "batteries included" looks like when the Neovim team actually gives a damn. Not in a corporate "we added AI to everything" way, but in a genuine "we listened to what people were doing with plugins and we baked it in because it was clearly useful" way. The plugin ecosystem isn't dying - it's just getting a foundation to stand on. The things that used to require plugins are becoming built-in, which frees plugin authors to do weirder, more interesting, more specific things instead of reinventing the wheel every single release.

And range-based tree-sitter highlighting? That single change is going to make a bunch of plugins faster without those plugin authors doing anything. Just by nature of the change being in core. Performance improvements that benefit everyone automatically, the way the universe intended.

## Personal Vibe Check

I've been using Neovim since the 0.4 days. I've watched it evolve from "Vim but with a slightly better codebase" to "an actual modern editor that happens to be compatible with Vim." I've migrated configs through maybe eight major versions. I've broken things, fixed things, switched to Lua, switched back to some Vimscript out of spite, switched to Lua again when I realized Vimscript was making me dumber.

And this release? This one hits different. This feels like the release where Neovim stops being "the editor you configure heavily to get a good experience" and starts being "the editor that gives you a good experience and lets you configure it to be amazing." That's a subtle difference but it's the difference between a car that comes with an engine and one that comes with a working car. You can still modify it. You can still make it yours. But you don't HAVE to build it from parts anymore.

I opened a file in the nightly build last week and I almost cried. The LSP attached automatically. The tree-sitter highlighting kicked in instantly. No plugins to install. Nothing to configure. Just worked. Like using a normal piece of software that was designed by people who actually use it. What a concept!

## The Future Is Now And It Fits In My Terminal

They called 0.12 "The year of Nvim OOTB" and honestly they've undersold it. This feels more like "The year we finally stopped living like animals." No more hunting and gathering for basic functionality. No more praying to the package manager gods. No more pressing ENTER like a peasant. We've been living in the technological dark ages and Neovim just pulled us into the light with a grace that makes me want to tattoo `vim.pack.add()` on my forehead.

Get this in your terminal. Update your build. Run it. Feel the weight lift off your shoulders. Watch your config get simpler in real-time. Delete your plugin manager. Delete your LSP plugin. Delete your treesitter plugin setup. Watch Neovim do it all on its own and tell me it doesn't feel like magic. Tell me it doesn't feel like the future. Tell me you don't feel just a little bit emotional about pressing `:q` and having it actually quit without some message about pressing ENTER first.

I'm not okay. I've been waiting for this for so long. We're finally here.

Go install it. Go break things. Go experience the most significant Neovim release since they added native LSP. Your fingers will thank you. Your brain will thank you. Your sanity - which was being drained by "Press ENTER" every single day - will finally be allowed to heal.

This is the way. This has always been the way. Now if you'll excuse me, I need to go stare at my terminal and process the fact that I can finally use an editor without wanting to throw my laptop out a window. What a time to be alive. What a beautiful, beautiful time.
