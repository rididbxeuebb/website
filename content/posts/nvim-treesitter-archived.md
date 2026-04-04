---
title: 'nvim-treesitter Got Archived And Honestly? Good. Fucking. Riddance.'
date: 2026-04-04
description: '13.5k stars, 1.2k forks, one burned-out maintainer, and a community that treated "free" like "owed." The most popular Neovim plugin just died and the funeral is exactly as messy as you would expect.'
---

This is beautiful. This is the most beautiful thing I've seen in 2026.

Yesterday — April 3, 2026 — the nvim-treesitter repository got archived. Read-only. Locked. Dead. The most depended-on Neovim plugin on the planet, the thing that basically every nvim config on Earth includes, the 13,500-star monstrosity that made tree-sitter actually usable for millions of developers — gone. Just gone. Like it never existed.

And I'm sitting here thinking: _deserved_.

## The Most American Story in Open Source

Let me paint you a picture. You've built something incredible. It started as a weekend project, then it became essential infrastructure, then it became a full-time job you don't get paid for. Millions of people use your code. Thousands open issues. Half of them don't even read the documentation. Every single day you wake up to someone complaining that their specific edge case isn't handled, that their obscure Linux distro's package manager has a bug, that Neovim 0.11 broke something (even though you told them six months ago to upgrade to 0.12).

This is nvim-treesitter. This is the life of [@clason](https://github.com/clason).

The final days read like a tragedy. Someone opened a discussion asking "why no releases?" — a completely reasonable question on the surface, but one that apparently hit a nerve. Then another user complained about the plugin dropping Neovim 0.11 support on "day 1 of v0.12 release" by "removing a single check." And clason just... snapped.

> "People like you are the 'insane burden'."

That's a direct quote. The maintainer of the most important Neovim plugin alive called their userbase a burden. Then they archived the entire repository.

I would feel bad, but honestly? I've been there. Every open source maintainer has been there. The difference is most of us don't have 13,500 people watching our meltdown.

## Here's the Thing Though

nvim-treesitter was always a wrapper. A really good wrapper, sure. An abstraction layer that made tree-sitter parsers actually installable and usable without reading the tree-sitter documentation that looks like it was written by a committee of cryptographers. But still — a wrapper.

And then Neovim 0.12 happened.

If you somehow missed it (I don't know how, I was literally refreshing GitHub every twelve minutes for a week), Neovim 0.12 shipped with _native_ tree-sitter support. Built-in. No plugin required. The thing that nvim-treesitter was wrapping got merged directly into the editor. It's like building a wrapper around `printf` and then the standard library just... absorbs your project.

So really, this was inevitable. The plugin became obsolete the moment Neovim 0.12 landed, and clason probably knew it. The burnout wasn't just about annoying users — it was about maintaining something that was already on life support, being kept alive only because the alternative was admitting that years of work suddenly became redundant.

## The Funeral

The discussion thread where it happened is a masterpiece of modern open source dysfunction. You've got users genuinely confused about why there's no "stable release" for a plugin that's been "experimental" for six years. You've got the maintainer trying to explain that tree-sitter integration was _always_ a moving target, that they literally warned everyone this was temporary, that there was a pinned issue about the roadmap that maybe two people ever read.

Then you've got theArch Linux users (because of course it's Arch) complaining that they can't update because their package manager hasn't cleared security checks, and somehow this is the plugin's fault. The nerve. The absolute nerve.

And through all of this, clason is just... done. You can see it in every response. The patience is gone. The "thanks for contributing" is gone. In its place: "just pin to whatever commit you want and stop upgrading."

That's the open source equivalent of "I'm not mad, I'm just disappointed."

## What Happens Now

Here's where it gets funny. nvim-treesitter is dead, but tree-sitter in Neovim is _better_ than ever. Neovim 0.12's native implementation does everything the plugin did, except faster, with better defaults, and without needing to configure anything. You can literally delete your entire treesitter config, restart Neovim, and nothing breaks. It's the dream we've been chasing for a decade.

The plugin's death is the feature working exactly as intended.

Meanwhile, nvim-treesitter-textobjects and nvim-treesitter-context are still alive. They're looking for maintainers. Good luck. You're going to need it.

## To clason, If You're Reading This

I get it. I genuinely get it. You poured years of your life into something that millions of people used without ever thanking you. You dealt with issues that ranged from "I can't read" to "you personally ruined my career by not supporting my specific version of Neovim on my specific OS." You watched your creation become infrastructure, which means everyone assumes it'll just _work_ and blames you when it doesn't.

And then Neovim absorbed your entire reason for existing.

The way you handled the end was ugly. The "insane burden" comment was unnecessary. But you know what? It was also honest. You told everyone exactly how you felt, and they archived you anyway. There's something almost respectable about that kind of emotional transparency before burning it all down.

Go touch grass. You earned it.

---

For everyone else: delete your nvim-treesitter config. You don't need it anymore. You never needed half of it anyway. The plugin served its purpose, it lasted longer than anyone expected, and now it's time to let it rest in peace.

Or don't. Pin to a commit. I'm sure that'll work great for the next three years.
