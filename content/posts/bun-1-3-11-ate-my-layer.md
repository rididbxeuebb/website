+++
title = "Bun 1.3.11 Ate My @layer"
date = 2026-04-17T10:00:00Z
description = "A patch release stripped Tailwind's layer order and reminded everyone that speed is useless if your bundler starts rewriting meaning."
+++

The first sign your build tool has stopped being your friend is when it starts editing your CSS like a drunk landlord.

That is the entire Bun 1.3.11 Tailwind `@layer` mess in one sentence. A build path was stripping the top-level `@layer theme, base, components, utilities;` statement out of the output. Not minifying it. Not inlining it. Removing the rule that tells the browser who wins when the cascade starts swinging chairs.

Tailwind v4 leans on cascade layers because CSS finally grew up enough to admit that selector specificity is mostly a knife fight between people who should have been sent home earlier. The layer statement is not decorative punctuation. It is the ordering contract. Delete it and your stylesheet stops being a system and starts being vibes with a build step.

```css
@layer theme, base, components, utilities;
```

That one line matters because the browser treats layers as actual precedence buckets. MDN is annoyingly explicit about this: the first declared layer has the lowest priority, the last declared layer has the highest, and unlayered styles sit outside the whole game and can override layered ones. So when a bundler silently removes the statement, it doesn’t “clean up” CSS. It mutates behavior.

Which is a fancy way of saying your app now lies to itself.

I know why build-tool people get tempted. They stare at ASTs all day and start hallucinating that everything is just rearrangeable lego. “Can I delete this?” “Can I merge that?” “Can I preserve the semantics if I squint?” Sure, sometimes. Then one day they eat the wrong at-rule and your UI goes from “polished product” to “why is this button wearing a different religion?”

I’ve lost an afternoon to a bug like this before. A perfectly ordinary button went feral after a tool “optimized” a stylesheet. Nothing was wrong in the component, nothing was wrong in the class names, and yet the page looked like it had been rendered by a raccoon with a Figma license. The actual culprit was a bundler helping too much. That’s the real hazard: when the tool is wrong, the failure doesn’t look like the tool. It looks like your code having a nervous breakdown.

And that’s why this one is so irritating. A patch release is supposed to be the boring lane. Patch releases are the adult table at the release party: no fireworks, no blood feud, just “here’s the correction, carry on.” If a patch release can delete a CSS layer statement, then “patch” has started meaning “we hope the blast radius stays small.”

It gets worse because the bug is specifically in a place where correctness matters more than speed. Nobody cares if your bundler is a smug little rocket when it’s chewing through dead code. I care deeply when it decides a live CSS directive is expendable. That’s not performance engineering. That’s a tiny act of vandalism with a fast benchmark and a smug grin.

The fix landed fast, which is good, but fast triage doesn’t magically turn the original bug into a non-event. It just proves the bug was real enough to panic the maintainers. And honestly, that should make us more suspicious, not less. If a compiler, bundler, or optimizer can change cascade order without screaming at you, it should be treated like a sharp object, not a productivity feature.

The deeper lesson is simple and ugly: CSS is part of your program. Not “asset pipeline content.” Not “static fluff.” Program. If your build chain can change which rules win, it can change the product. That means every “harmless” rewrite needs to be held at gunpoint until it proves it understands the difference between bytes and behavior.

So yes, the bug got fixed. Great. Wonderful. Gold star. But the real story is that everyone should be a little more paranoid now. Fast tools are nice. Clever tools are nice. Boring tools that leave my semantics alone are sacred.

Leave the layers alone. Save your genius for something that isn’t my stylesheet.
