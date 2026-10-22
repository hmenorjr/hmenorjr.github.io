---
title: 'PHP2Shell: How a 12-Year-Old Bug Nearly Broke the Internet'
description: "You know how if you find a cheat code in a video game, you can suddenly fly, spawn infinite weapons, skip levels? Imagine that cheat code worked on every single website on the internet at once. That's basically what PHP2Shell was."
pubDate: '2026-10-22'
featured: true
---

## What actually happened

PHP is the code that runs a huge chunk of the web — WordPress sites, social platforms, government portals, you name it. Two bugs were hiding in its core code for **over 12 years**. They let a stranger on the internet — no login, no password, no "are you sure?" prompt — just *take over* a server. Run whatever commands they want. Read your data. Delete things. Plant malware.

Security people rate vulnerabilities from 0 to 10. These scored **9.2**. That's "we're losing sleep" level.

## Why it was so scary

Most bugs affect one specific app or one specific version. These affected **every PHP version from 5.4 onward** — meaning basically everything still running. One bug let an attacker trick PHP into using leftover garbage from a previous request (think: reusing a scratchpad that still has someone else's homework on it). The other made PHP crash in a way that left a "ghost" pointer to freed memory — like following a map to a building that's already been demolished, but somehow the door still opens.

## The AI twist

Here's the part that's wild: **an AI found it.** A researcher at a security company used OpenAI's GPT-5.6 Sol model to hunt for bugs, and it spotted both flaws. Wiz, another security firm, independently confirmed them. They called it "the most severe vulnerabilities ever discovered by AI."

## What happened when the news leaked

The details were supposed to stay secret until Tuesday, October 21. They got posted on Hacker News the day before. So the PHP team rushed the patch out. Within hours:

- **Cloudflare** saw people actually trying to exploit it in the wild and threw up emergency firewall rules.
- Government sites in Finland, the Netherlands, Belgium, and the UK **went dark** as a precaution.
- Parts of Wikipedia, 4Chan, and DeviantArt disappeared.
- The NSA and multiple governments issued urgent "patch NOW" warnings.

## Why the patch mattered

Without it, anyone could have walked up to any PHP-powered website and gained full control. No hacking skills required — just send one specific request. The patch (shipped in PHP 8.5.12, 8.4.27, 8.3.36, and 8.2.35) closed both holes. Every site that updated became safe again.

The PHP Foundation admitted the underlying issue had been known for about **two years** before it was actually fixed, and called their own process a "structural failure." That's rare for a project that's been around since 1995 to say that about itself.

## The takeaway for you

Two things:

1. **The internet is held together by code that's often decades old.** Bugs hide in plain sight for years. The good news is people (and now AI) keep finding them.
2. **Patching isn't boring admin work.** It's the difference between "website is safe" and "website is now owned by a stranger." Every time you update software, you're closing a cheat code.

