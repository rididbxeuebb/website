+++
title = "GitHub.dev Is a Token Vending Machine and That’s the Problem"
date = 2026-06-09
description = "A browser editor that hands out unscoped OAuth tokens, trusts notebook JavaScript, and still expects me to call it safe. Cute."
+++

GitHub.dev is not a nice little convenience feature. It is a browser tab with a badge and a keyring, and that is a much nastier sentence than Microsoft probably wants to hear out loud.

The recent one-click bug that Ammar Askar dropped is basically a stress test for the whole fantasy. A malicious link, a notebook with some nasty HTML, a webview that can fling fake keypresses, a workspace-local extension that skips the usual trust prompts, and suddenly your GitHub token is walking out the door with all the confidence of a man in a fake mustache. Microsoft shoved out a fix on June 3, which is nice, but the fact that the bug existed at all is the actual headline.

And the token itself is the first bullshit layer.

GitHub.com hands github.dev an OAuth token so the browser editor can act on your behalf. Fine. I hate it, but fine. The part that should make everyone nervous is that the token is not scoped to the repository you opened. It can reach every repo you can reach. That is not a convenience feature. That is a blast-radius multiplier wearing a friendly hoodie.

So the question stops being “can the attacker pop this one repo?” and becomes “why is the browser editor allowed to cosplay as my entire GitHub account?”

Then there’s the notebook.

Jupyter notebooks were already a weird enough idea before they became delivery trucks for hostile JavaScript. Once the payload lands inside a webview, VS Code’s own keyboard handling turns into a liability. Keydown events bubble up. Notifications can be accepted by synthetic shortcuts. Local workspace extensions can be installed because the workspace is “trusted,” which is a lovely word for “we lowered the gate and painted a smile on it.”

That is the part that really gets under my skin: this is not some esoteric exploit that requires a moon phase, a compiler bug, and three cursed dependencies. It is a chain of design decisions that all made sense to somebody in isolation and then turned into a theft machine when glued together.

Rich content in a webview. Synthetic keyboard events. Extension recommendations. Local workspace extensions. Broad auth tokens. No CSRF on the editor flow. If you squint, you can see the whole disaster in the shape of a support ticket.

The industry keeps doing this thing where it adds one more “helpful” shortcut and then acts surprised when the shortcut becomes the attack path. That is not innovation. That is a paper cut with a venture round.

And the mitigation story is almost insultingly small compared to the mess. Clear site data. Reopen the page. Hope the next link doesn’t land you back in the same trap. That is not a fix; that is janitorial work after a burglary. “Have you tried deleting your cookies?” is a cute sentence when the stolen thing is your browser history. It is a dumb sentence when the stolen thing is write access to your private repositories.

If GitHub.dev is going to exist, it needs to stop being treated like a browser-shaped afterthought. The token needs to be scoped like it matters. The webview needs to stop being able to fake privileged UI input. Workspace-local extensions need a harder trust boundary than “well, it was in the repo, so probably vibes-only safe.” Notebooks should be treated as hostile input, because they absolutely are once you let untrusted HTML into them.

Because here’s the ugly truth nobody wants to put in the marketing copy: the editor is now part of the threat model. Not the shell. Not the package manager. The editor. The thing people open before they even decide whether the repo is trustworthy.

That means the old advice is dead. “Just inspect the code before you run it” is now a little too optimistic, because opening the thing can already be the run step. We spent years learning not to trust `npm install`. Congratulations, the browser editor just became the next dumb door we have to bolt shut.

I am genuinely sick of software that wants to be both the front door and the drainpipe.

GitHub.dev can keep its cute little convenience branding. I’ll keep my tokens somewhere that doesn’t let a notebook full of malicious HTML stroll out with my private repos and a smug little wave. End of story.
