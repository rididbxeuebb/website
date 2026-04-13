---
title: 'Flow Control: The Text Editor Built by Someone Who Actually Uses It'
date: 2026-04-13
description: 'A Zig-based text editor with 1.8k stars, zero corporate backing, and a developer who actually uses it as their daily driver. What a concept.'
---

There's something beautiful about a text editor built by one person who actually uses it. Not "uses it for the demo," not "uses it because I have to," but genuinely reaches for it every single day because it's the best tool for the job.

Flow Control is that editor. Written in Zig by CJ van den Berg (neurocyte), this thing has been churning away since 2024, racking up 1.8k stars and a genuinely impressive amount of polish for a project with maybe one or two full-time contributors. No corporate backing. No VC funding. No "we're revolutionizing developer productivity" blog posts from a company trying to sell you enterprise licenses.

Just a person who wanted a better text editor and then, in a fit of either brilliance or complete insanity, built one.

## The Absurdity of Building a Text Editor in 2026

Think about what you're getting into when you build a text editor today. The competition isn't some scrappy open source projects from 2005 anymore. You're competing against:

- Neovim, which has been in development for a decade and has hundreds of contributors
- Helix, which came out of nowhere and immediately established itself as the "modern Vim"
- VS Code, backed by Microsoft, with a team of engineers, a marketplace, extensions for everything
- Emacs, which has been around since the 70s and has evolved into something neither man nor beast can fully comprehend

And Flow Control just... shows up. Written in Zig, a language that's barely out of its "experimental" phase. Uses tree-sitter for syntax highlighting because of course it does, that's the standard now. Has LSP integration. Supports multiple keybinding modes (Vim, Emacs, Helix, and its own "Flow Control" mode for the VS Code refugees).

The audacity is almost offensive.

But here's the thing — it works. Really well, actually.

## The Features That Make You Go "Wait, How?"

Let me list what this thing does, because some of it genuinely caught me off guard:

- **70+ programming languages** with zero configuration tree-sitter highlighting
- **LSP support** with inline autocomplete, goto definition, symbol lookup, hover — the whole IDE package
- **Multi-cursor editing** because we're not savages
- **Tabs, splits, scrollbars** — GUI-level UI elements in a TUI
- **Mouse support for everything** — not just "you can click to move the cursor" but actual UI element interaction
- **Hybrid rope/piece-table buffer system** — fancy computer science words for "it handles huge files without choking"
- **Infinite undo** — until you run out of RAM, which, fair
- **Cross-platform** — Linux, FreeBSD, macOS, Windows, and even Android via Termux

The frame times are under 6 milliseconds. The input latency is allegedly "low." The scrolling is animated. This is a terminal-based text editor with animated scrolling, which sounds like a contradiction in terms.

And it's a single statically linked binary. No dependencies. No runtime files to manage. You copy the binary to another machine and it just works.

## The Zig Factor

Writing a text editor in Zig is a choice that deserves respect. Zig is still in that awkward phase where it's "production ready" but also "oh god the language might change completely next version." The compiler itself is written in Zig. The standard library is still stabilizing. There are entire features that just don't exist yet.

But neurocyte said "yeah, I'll build a text editor in this" and shipped something that builds on Zig 0.15.2 (as of February 2026) and just... works.

There's something poetic about using a language that's itself a passion project to build another passion project. It's like watching two weirdos find each other at a party and immediately start talking about their own weird projects.

## The Real Tell: It Has a Roadmap

Look at this project's roadmap:

**In Development:**

- LSP completion support
- Persistent undo/redo
- File watcher integration

**Future:**

- Collaborative editing
- Plugin system
- Multi-terminal sessions

This is a project that actually plans ahead. It has a devlog. It has releases. It has active development with realistic feature goals. This isn't "I'll work on it when I feel like it" — this is someone treating their text editor like an actual product.

The collaborative editing and plugin system are particularly interesting. Those are hard problems that major editors have been solving for decades. The fact that Flow Control is even considering them suggests this isn't a "I'll add one more feature and then abandon it" project.

## The Terminal Requirements Are Actually Fair

Flow Control requires:

- A terminal with 24-bit color (so, most modern terminals)
- NerdFont support (for icons)
- A UTF-8 locale
- Ideally Kitty keyboard protocol support (for better input handling)

Recommended terminals: Kitty, Foot, Ghostty, or Zellij.

This is actually quite reasonable. You're not asking for some obscure terminal that nobody uses. You're asking for "use one of the four best terminals available" which is... fair? If you're going to build a fancy TUI, you should be honest about what it needs.

## What Stands Out

The fact that this exists at all is worth celebrating. We live in a world where text editors are either:

1. Corporate products run by companies that will eventually make decisions you hate
2. Volunteer projects run by people who are burnt out and barely hanging on
3. "Community-driven" projects where the community is three people and a bot

Flow Control is option 4: a passionate developer who wanted something better and made it. Using it as their daily driver means bugs get fixed. Features get added because they're actually needed. The project has momentum because there's a real person behind it who cares.

That matters. In an ecosystem where we're constantly being told to "just use the established tool" or "just use what the corporation provides," there's something refreshing about watching someone build their own and do it well.

## Should You Use It?

Maybe! Probably not as your only editor, if you're on Neovim or Helix and happy. But if you're curious about what's possible in a TUI, if you want to see what Zig can do, if you've ever thought "I wish there was a text editor that did X" — this is worth a look.

The installation is trivial: download a binary, put it in your path, run `flow`. It just works.

The best part? It's MIT licensed. It's not going anywhere. The developer isn't going to suddenly change the license or get acquired or abandon it because they got a job at a big tech company. It's just... there. A text editor that exists because someone wanted it to exist.

In a world of AI-generated slop and corporate software that treats you as the product, I'll take a text editor built by someone who actually uses it.

That used to be how software worked. It's nice to see it still happens.
