---
title: 'Your AI Job Interview Was Just Leaked to the Dark Web'
date: 2026-04-09
description: 'Mercor got pwned through LiteLLM. 4TB of data. Lapsus$ is auctioning your KYC documents. And the AI companies that built their business on this mess are mysteriously quiet.'
---

So here's a fun one for your Wednesday.

Mercor — the "AI recruiting platform" that works with OpenAI, Anthropic, and basically every big AI lab to hire domain experts (scientists, lawyers, doctors) for model training — got absolutely rinsed through a supply chain attack. Not some sophisticated zero-day. Not a nation-state hitting their perimeter. They got owned because their CI/CD pipeline pulled a compromised version of **LiteLLM**, an open-source library that literally just wraps LLM API calls.

The attack chain is honestly beautiful in its stupidity:

1. **Trivy** (the open-source security scanner everyone uses) got compromised first
2. That compromised Trivy poisoned LiteLLM's build pipeline
3. LiteLLM pushed malicious PyPI packages 1.82.7 and 1.82.8
4. Those packages sat on PyPI for ~40 minutes before anyone noticed
5. Thousands of companies auto-downloaded that shit, including Mercor
6. The payload grabbed credentials, established persistence, and exfiltrated everything

What did the bad guys get? Let's see:

- **939GB of source code**
- **211GB user database** (you know, the people who uploaded their resumes, passports, KYC documents)
- **3TB of storage buckets** with video interviews
- **TailScale VPN credentials** — meaning they probably had full network access
- Internal Slack logs, ticketing systems, the whole disaster parade

That's roughly **4 terabytes** of a company that handles sensitive hiring data for half the AI industry.

And Lapsus$? They're auctioning it on the dark web. "Propose an offer," they said. Very professional.

---

Now here's where it gets actually interesting.

Mercor isn't some random bootstrapped startup. They were reportedly valued at **$10 billion** as of October 2025. They work with **OpenAI and Anthropic** to train their models. The entire synthetic intelligence industry basically depends on Mercor's pipeline of human experts — scientists reviewing research papers, lawyers checking compliance, doctors validating medical data.

And now all of that is on some dark web auction house because someone at LiteLLM didn't notice their PyPI credentials got phished through a compromised security tool.

The cognitive dissonance is almost perfect. These companies spend billions on "AI safety" and "responsible development" while their own supply chain gets poked by what amounts to a moderately sophisticated phishing email. Their entire data pipeline — the human expertise that makes these models actually useful — got owned through a library that's supposed to just proxy HTTP requests to OpenAI's API.

I want you to sit with that for a second.

---

The response from the AI companies has been... predictably muted. Meta reportedly paused work with Mercor "indefinitely" after the breach. OpenAI and Anthropic haven't said much of anything. No press conferences. No "we take security seriously" statements with actual details. Just... silence.

Which is wild, right? If this was a traditional tech company, there'd be SEC filings, class action lawsuits, the CEO doing the "we take the trust of our users extremely seriously" tour on CNBC. But it's an AI company, so the playbook is different. The playbook is "wait three days and hope everyone forgets."

Meanwhile, LiteLLM's official statement says "the compromise originated from the Trivy dependency used in our CI/CD security scanning workflow." Which is some impressive victim-blaming of a dependency they voluntarily added to their pipeline. "We got hacked because our security scanner got hacked first" is not the flex they think it is.

---

The broader lesson here isn't new, but it bears repeating until something changes:

**Your entire infrastructure is one `pip install` away from disaster.** Not because of some exotic supply chain vulnerability. Because someone at Trivy got phished, and then that poisoned the tool you use to find vulnerabilities in your own code. The circle of security is complete. It's turtles all the way down, and every turtle is running as root.

The npm ecosystem had its axios incident last week (North Korea pushed a RAT through a maintainer's compromised account, if you somehow missed that). PyPI just had this. Docker Hub images got compromised. We're living in a world where the foundational infrastructure that runs the entire software industry is held together with npm publish tokens and email-based 2FA.

And the response from everyone is always the same: publish a blog post with a list of "best practices," tell people to pin their dependencies, and move on until the next incident. Nobody's asking the hard questions about why one compromised maintainer account can impact millions of downloads in a day. Nobody's building actual defenses at the registry level. We're just playing whack-a-mole while the attacks get more sophisticated and the attack surface expands to literally every company that uses AI.

---

Mercor says they're "conducting a thorough investigation supported by leading third-party forensics experts." That's corporate speak for "we have no idea what happened and we're hoping a consulting firm can make this someone else's problem."

What they should be saying is: "We exposed the personal data of thousands of people who trusted us with their most sensitive information, and we did it through a dependency we didn't even write, maintained by people we'd never met, because nobody in our organization thought to question whether pulling random packages from the internet was a sound security strategy."

But they won't say that. Because nobody says that. Because the entire industry runs on "move fast and break things" and acts surprised when things break.

If you submitted your resume, passport, video interviews, or any personal data to Mercor in the last few years — assume it's on that auction. Freeze your credit. Watch for phishing. The people who stole this data aren't going to use it themselves; they're going to sell it to someone who will.

And to the AI companies building their entire business on human expertise they couldn't even be bothered to protect: maybe next time, don't outsource your data security to a company that got owned through a library that just wraps HTTP requests.

The irony is too good. Truly.
