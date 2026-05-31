---
title: 'Your Open Model Needs a Lie Detector'
date: 2026-05-31
description: 'The Linux Foundation built MOT because “open source AI” turned into marketing with a law degree.'
---

“Open source AI” is one of those phrases that instantly makes me trust the speaker less.

Not because openness is bad. Because the industry has spent the last couple years slapping the word open onto whatever sludge it wants to sell, then acting offended when people notice the weights are public, the data is missing, the license is weird, and the reproducibility story is just a haunted PDF.

So yes, the Model Openness Tool exists now. Good. Frankly, it’s overdue.

The Linux Foundation’s Generative AI Commons shipped MOT as a way to score how open a model actually is. Not how open it looks in a launch post. Not how many times somebody said “community” in the keynote. How open it is, in the boring, annoying, measurable sense that software people keep pretending they care about.

It asks 16 questions. It gives a score. It buckets models into three classes: Open Model, Open Tooling Model, and Open Science Model. That is already more honesty than most of the AI marketing stack can survive without needing a nap.

And the best part? The site itself says the tool is beta software and may be incomplete or inaccurate.

That’s delicious.

We are now at the point where the lie detector has its own “please don’t sue me” banner. Peak civilization. Beautiful rot. A machine built to grade the openness of AI models comes with the same disclaimer energy as a toddler holding a vase and making eye contact.

Still, I like it.

Because the alternative is the current industry ritual: release a model, declare it “open,” hide the training data, omit the provenance, keep the useful bits behind a license carve-out, and hope nobody notices that “open” now means “available if you squint, obey, and don’t ask where the body came from.”

MOT doesn’t solve the lying. It just makes the lying harder to perform with a straight face.

That matters.

It matters because a model is not open just because you can download it. A model is not open just because it has weights. A model is not open just because Hugging Face has a nice card and the PR copy says “transparent.” If the code, the data, the training recipe, the documentation, or the licensing story are missing, then what you’ve got is a carefully branded partial truth. Which, in tech, is usually the first step on the road to a complete bullshit sandwich.

The nice thing about a scoring tool is that it forces specificity. It turns hand-wavy openness theater into a checklist. Did you release the artifacts? Under what license? Can anyone reproduce the thing? Can they modify it? Can they actually build on it without needing divine intervention and a vendor sales call?

If the answer is “sort of,” then congratulations: you have discovered the giant swampy center of the problem.

That’s why the catalog matters too. The tool isn’t just philosophy cosplay. It’s a place where models get classified, compared, and forced to sit still for five damn minutes while somebody asks the questions the launch blog conveniently skipped. That alone is useful. Annoying, sure. But useful in the way a flashlight is useful when the room is full of rats wearing product badges.

The funniest part is how much this exposes the industry’s favorite scam.

Everyone wants the status of openness. Very few want the obligations. They want the community halo, the distribution boost, the “open” credibility, and the cozy little warm glow that comes from pretending they’re on the same side as the software commons. But when you ask for the receipts, suddenly it’s “proprietary concerns” and “responsible release” and “we can’t share that part for safety,” which is a lovely sentence if you enjoy being lied to with punctuation.

MOT is not a cure.

It’s a mirror. Sometimes that’s enough.

And if your model can’t survive 16 questions without collapsing into legal slime and branding goo, then maybe it wasn’t open.

Maybe it was just dressed that way for the photos.
