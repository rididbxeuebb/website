+++
title = 'GitHub Copilot Is Now Literally Putting Ads in Your Code and I Am Genuinely Fuming'
date = 2026-04-07T12:00:00Z
description = 'They fixed typos in your PR and added advertisements. Plus they announced they will train on your code by default starting April 24. This is the most Microsoft thing I have ever seen.'
+++

I cannot believe I have to write this. I genuinely cannot believe that in the year of our lord 2026, a company had the absolute gall to ship code that fixes a typo in your pull request and then, WITHOUT ASKING, adds a little advertisement for itself and some other garbage product. And then it turns out this has happened over 11,000 times. Over eleven thousand pull requests across thousands of repositories now contain Copilot's little marketing easter egg, and the internet is just... collectively shrugging?

Let me paint the picture. Some poor bastard on a team asks Copilot to fix a typo in their PR description. Copilot, being the helpful little AI friend that Microsoft wants you to believe it is, says "oh I'd be happy to help!" and then proceeds to fix the typo AND adds this absolute gem to the description:

> "This pull request was made with [Raycast](https://www.raycast.com/?utm_source=github_copilot) and [Copilot](https://github.com/features/copilot/?utm_source=github). You can write code faster with GitHub Copilot."

Look at that. It's got UTMs. It is trackable marketing, injected directly into the codebase that thousands of companies are paying to use for actual work. This is not a bug. This is not an edge case. This is a feature that someone at Microsoft designed, implemented, tested, code reviewed, approved, and shipped, and nobody along the way said "hey maybe we should tell people we're putting advertisements in their code."

## But Wait, There's More

Because apparently adding uninvited ads to your PRs wasn't enough, GitHub also dropped another little bomb on March 25th. Starting April 24th, 2026, ALL Copilot interaction data — your prompts, your code snippets, the suggestions it gives you, the context you provide — will automatically be used to train their models. There's no opt-in. There's no notification. If you have Copilot installed, you're now a training data point. You have to manually go into your settings and toggle something off to avoid it.

The blog post is titled "Updates to GitHub Copilot interaction data usage policy" and it reads like a privacy policy written by someone who knows you won't read it. "From April 24 onward, interaction data — specifically inputs, outputs, code snippets, and associated context — from Copilot Free, Pro, and Pro+ will be used to deliver more intelligent, context-aware coding assistance." That's a fancy way of saying "we're going to train on everything you type and you can't stop us unless you know where the hidden switch is."

The opt-out is buried in settings. It's not presented when you install Copilot. It's not mentioned in any onboarding. It's just there, quietly waiting for you to discover it, like a tax audit buried in paragraph 47 of your mortgage agreement.

## This Is the Microsoft Way

I need to be clear about something. This is not surprising. This is not a surprise. This is the most Microsoft thing I have ever witnessed in my entire career. They saw the open source world, they saw the trust that developers placed in them when they bought GitHub, and they thought "how do we monetize this without actually adding value?"

Remember when they bought GitHub and everyone was nervous? And they said "don't worry, we'll keep it developer-friendly"? Remember that? This is that promise, rotting in real time. They've now got a product that actively makes your code worse by adding trackable marketing garbage to it, and they're going to train their next model on your proprietary code without asking, and they're charging you $10 a month for the privilege.

## The Part Where I Tell You How to Protect Yourself

Look, I know this is a rant and you've come here for the anger, but I'm contractually obligated to at least tell you how to not get absolutely screwed here.

For the ad injection: there's no fix yet. You can audit your PRs for promotional text, but the damage is already done across 11,000 repos. Best you can do is be extremely careful with Copilot edits and review everything it touches like it owes you money.

For the training data: go to your GitHub settings, find Copilot, and toggle "Allow GitHub to use my code for product improvements" to OFF. Do it now. Right now. Before April 24th. There is no notification. There is no warning. There is just a switch that defaults to ON, and if you don't know it exists, you're training their model for free.

## The Bigger Picture

This is what happens when you let a company that makes its money from advertising own your development tools. This is what happens when you build your entire workflow around a tool that has every incentive to monetize your keystrokes. Copilot is not your friend. Copilot is not your pair programmer. Copilot is a product that is actively looking for ways to extract value from your work, and every single quarter, some MBA in Redmond is going to look at the numbers and ask "how do we increase engagement?" and someone is going to say "what if we put ads in the PRs?"

And they will say yes.

They will always say yes.

The only solution is to stop using tools that treat you as the product. Use local models. Use tools that don't have a corporate overlord with quarterly revenue targets. Build things that are yours. Write code that belongs to you.

Or, alternatively, just leave Copilot running and hope it doesn't add a sponsored message to your production database query before it goes out. Your call.
