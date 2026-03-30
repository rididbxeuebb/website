---
title: "libghostty is Absolutely F*cking Unreal and I'm Not Okay"
date: 2026-03-31
description: "Mitchell Hashimoto just extracted the terminal core from Ghostty and gave it to us as a C library. I've ascended. Send help."
---

Okay, I need to talk about this and I need you to understand that I am not exaggerating, I am not being paid to say this (god I wish I was), and I have not consumed any substances that would impair my judgment. Mitchell Hashimoto, the beautiful madman, just merged the initial C API for libghostty and I am LOSING my absolute mind over here.

## What Even Is libghostty

For those of you who have been living under a rock and somehow missed the terminal emulator that has taken over every tech person's setup in the past year, Ghostty is the terminal that makes you go "oh, this is what a terminal should feel like" after years of suffering through iTerm2's jank or Terminal.app's... existence.

But here's the thing — Ghostty was always this self-contained monolith. You could use it, but you couldn't BUILD on top of it. Want to create your own terminal that uses Ghostty's rendering brain? Too bad! Want to embed a terminal emulator in your application? Find another library!

WELL. NOT ANYMORE.

Mitchell just merged PR #11506 which adds the INITIAL C API for what they're calling libghostty (specifically, the `ghostty-vt` component — a virtual terminal emulator library). And it's absolutely packed with goodness.

## The API That's Got Me Weeping

Check out what you can now do with a mere ~11 function calls:

```c
#include <ghostty/vt.h>
#include <stdio.h>
#include <stdlib.h>
#include <string.h>

int main() {
  GhosttyTerminal term;
  GhosttyTerminalOptions opts = .cols = 80, .rows = 24, .max_scrollback = 0;
  ghostty_terminal_new(NULL, &term, opts);

  const char *input = "Hello, \033[1mBold\033[0m World!\r\nLine 2\r\n";
  ghostty_terminal_vt_write(term, (const uint8_t *)input, strlen(input));

  GhosttyFormatterTerminalOptions fmt = GHOSTTY_INIT_SIZED(GhosttyFormatterTerminalOptions);
  fmt.emit = GHOSTTY_FORMATTER_FORMAT_PLAIN;
  fmt.trim = true;

  GhosttyFormatter fmtr;
  ghostty_formatter_terminal_new(NULL, &fmtr, term, fmt);

  uint8_t *buf;
  size_t len;
  ghostty_formatter_format_alloc(fmtr, NULL, &buf, &len);
  fwrite(buf, 1, len, stdout);

  free(buf);
  ghostty_formatter_free(fmtr);
  ghostty_terminal_free(term);
}
```

THAT'S IT! That's all it takes to spin up a full VT parser, feed it some escape sequences, and dump the rendered output! In C! A language that most of us thought was just for writing operating systems and making our CI pipelines 10% faster!

The API gives you:

- `ghostty_terminal_new` / `ghostty_terminal_free` — create and destroy terminals like it's nothing
- `ghostty_terminal_resize` — dynamically resize because why not
- `ghostty_terminal_vt_write` — the magic function that takes raw VT sequences and makes them make sense
- `ghostty_terminal_reset` — full terminal reset (that sweet sweet RIS escape sequence)
- `ghostty_formatter_terminal_new` — create formatters to extract screen contents in various formats
- And more!

## But Wait, There's More!

Already there's a demo project called **Ghostling** — a minimal terminal emulator BUILT on top of libghostty's C API. It's literally a single C file (plus some CMake glue) and uses Raylib for windowing and rendering. 876 stars in like a week because people are that excited.

The fact that you can build a working terminal emulator in a single C file using this library is absolutely insane. The implications here are enormous:

- Embedded terminals in IDEs that actually work properly
- Terminal emulators for weird platforms that never had good options
- Testing tools that need to parse terminal output
- accessibility tools
- Basically anything anyone ever complained about regarding terminal emulation now has a solution

## The Road Ahead

Mitchell being Mitchell, he's already talking about what's coming:

> "Obviously need to expose a lot more from the terminal: Read current set modes, Read cursor information, Read screen information, etc... Need an optional callback system so that vt_write can invoke callbacks for side effect sequences like clipboards, title setting, responses, etc. terminal.RenderState C API so that people can build high performance renderers on top of libghostty-vt"

SO THE RENDERING STATE API IS COMING. That means people will be able to build their own renderers on top of Ghostty's terminal brain. The mind absolutely reels.

## What This Means

We're witnessing the beginning of something huge here. The terminal emulator that everyone agrees is the best one out there just became a LEGO set. Mitchell Hashimoto didn't just build a great terminal — he built a platform.

I genuinely believe that in 2-3 years, libghostty is going to be everywhere. Every "cool new terminal" project is going to be "built on libghostty" the same way everything cool in the Rust ecosystem is built on tokio or whatever. The barrier to entry for building terminal applications just dropped through the floor.

And the best part? It's open source. MIT licensed. The same guy who brought you Vagrant, Packer, Terraform, Vault, Nomad, Consul, and like half of the infrastructure tooling landscape just handed you the keys to the kingdom.

I'm not saying I'm emotionally invested in this library's success to an unhealthy degree, but I did just add "contribute to libghostty" to my todo list between crying and hitting the star button repeatedly.

Go forth and terminal-ify everything.
