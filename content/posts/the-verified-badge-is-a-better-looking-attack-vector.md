+++
title = "The Verified Badge Is a Better-Looking Attack Vector"
date = 2026-05-23T00:00:00Z
description = "Nx Console turned a shiny badge and auto-update into a live-fire demo of why editor trust is mostly cosplay."
+++

I am once again asking the software industry to stop treating a green checkmark like it is a priestly blessing.

On May 18, Nx Console v18.95.0 spent about 18 minutes in the Visual Studio Marketplace and about 36 minutes on Open VSX. That was long enough for a poisoned extension with a verified publisher badge and millions of installs to turn developer workstations into credential piñatas. GitHub later said the attack reached roughly 3,800 of its internal repositories. Not customer repos, apparently. Just GitHub’s own house on fire. Comforting.

And yes, the badge mattered. It always does. Badges are the little fake moustaches of software trust: they make the thing look respectable right up until it robs you.

The nastiest part is not even the extension itself. It is the delivery model. Auto-update means the user never makes the decision. The marketplace makes the decision. The publisher makes the decision. The user just gets to discover, after the fact, that their editor quietly accepted a new room-mate with root-adjacent habits and a taste for secrets.

This payload didn’t ask politely. It went hunting through GitHub tokens, npm creds, AWS material, Vault tokens, 1Password sessions, SSH keys, `.env` files, and process memory like it was doing inventory on a warehouse that hates itself. On macOS it dropped `cat.py` and a LaunchAgent, because apparently even malware likes lifecycle management now. One Cursor activation showed up too, because of course the infection doesn’t care what branding you wrap around the same cursed editor core.

The larger insult is the chain of trust behind it. The malicious extension was not some random sketchy download from the lunar basement. It was the end of a chain that started with a separate supply-chain compromise upstream, where a developer machine got popped, a GitHub CLI token got lifted, and the attacker used that identity to keep moving. That is the modern failure mode: one machine, one token, one sloppy assumption, and suddenly your “trusted publisher” badge is a ventriloquist dummy.

This is why I keep laughing at the people who say, with a straight face, that marketplaces are “safer” because they’re moderated. Moderated by what, exactly? Vibes? A logo? A scan that catches yesterday’s malware after it already did the job? If your security story depends on the attacker being rude enough to look suspicious before publishing, then congratulations, you have built a bouncer for a door that was already kicked in.

The fix is boring, which is probably why so many teams refuse to do it.

- Separate publish identities from day-to-day developer identities.
- Require two humans for public releases.
- Add quarantine windows for fresh packages and extensions.
- Treat editor extensions like code execution, because that is what they are.
- Enforce extension allowlists on work machines.
- Stop letting long-lived `gh` tokens sit around like loose change in a couch cushion.

And for the love of whatever deity is still answering support tickets in this timeline, stop pretending that “we’ll scan it” is a strategy. Scanning is for finding the corpse after the stabbing. If you want fewer stabbings, you need fewer knives in the room.

So no, I am not impressed by the badge. I am impressed by how quickly everyone still trusts the badge after the last five incidents proved it is basically a decorative lie with a marketplace logo on top.

If your editor can auto-install a backdoor, your editor is not an app. It’s a liability with syntax highlighting.
