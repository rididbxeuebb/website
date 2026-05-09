+++
title = "NuGet Is Not Special. It’s Just Wearing Enterprise Cologne."
date = 2026-05-09T12:00:00Z
description = "Five fake .NET packages stole browser creds, wallets, and SSH keys, because package registries are all just crime scenes with better branding."
+++

NuGet is not a cathedral. It is a package registry, which means it is a place where strangers hand you executable code and you say, with a straight face, "sure, sounds fine." The only difference between NuGet and the rest of the ecosystem is that .NET developers keep pretending their laundry is cleaner.

May 6, 2026 was a rude little reminder. Xygeni reported five malicious NuGet packages — `IR.DantUI`, `IR.Infrastructure.Core`, `IR.Infrastructure.DataService.Core`, `IR.iplus32`, and `IR.OscarUI` — that impersonated Chinese .NET UI and enterprise libraries while quietly dropping a stealer. Together they had about 65,000 downloads. One of them, `IR.DantUI`, was basically an anagram cosplay of `AntdUI`, which is the sort of naming trick that works because everyone is moving too fast and pretending they aren't.

The gross part is not even the disguise. It is how normal the whole thing looked.

These packages were not doing the obvious idiot malware thing with a screaming `postinstall` hook and a red blinking light. They used .NET Reactor protection, module initializers, and a JIT hook so the payload could wake up as the runtime loaded it. In other words: the package gets to run before your app even starts pretending it is in control. That is not a library. That is a sneaky little landlord with a skeleton key.

And once it was awake, it went for the expensive stuff: browser credentials, crypto wallets, SSH keys, local files, wallet extension data, and whatever secrets developers had left lying around because, shockingly, humans are bad at threat modeling their own desktops. The report even calls out `~/.foundry`, `.ethereum`, `.brownie`, and the usual pile of `.env` garbage. If you build on a machine that also contains wallet keystores and SSH keys, congratulations, you have assembled a buffet.

The part that should make every .NET team wince is the version history. Xygeni says the campaign spanned 224 versions across five package IDs, with 219 of them unlisted. That is not a package history. That is a magician's trunk. If your registry lets an attacker hide that much churn in plain sight, then your "trusted package source" is mostly trust theater with nicer fonts.

.NET people love to talk like they live in a more mature ecosystem. Strong names. Signed binaries. Enterprise controls. All that nice clean paperwork. Fine. Wonderful. And then the registry still hands them a fake dependency that hoovers up browser tokens and wallet seeds like it is doing bookkeeping. The platform is not safer because the DLL has a Microsoft-flavored accent.

So no, NuGet did not "get attacked." NuGet got what every public registry eventually gets when enough people confuse branding for safety: a pack of opportunists that knew exactly which boring-looking helper libraries would be installed without a second thought.

The lesson is the same ugly one every time. Treat restore as code execution, because the runtime already does. Pin versions. Watch unlisted histories. Be suspicious of utility packages that do nothing except exist. And maybe stop acting like your ecosystem is too respectable for the same bullshit that already wrecked npm, RubyGems, PyPI, and everything else with a search box.

The registry was never the safe part. It was just the part with better cologne.
