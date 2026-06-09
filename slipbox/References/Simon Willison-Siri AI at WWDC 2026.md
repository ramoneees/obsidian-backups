---
source: "Simon Willison"
title: "Siri AI at WWDC 2026"
date: 2026-06-08
url: https://simonwillison.net/2026/Jun/8/wwdc/#atom-everything
ingested: 2026-06-09
tags: [IA, tech, LLMs]
---

# Siri AI at WWDC 2026

**Source:** Simon Willison
**Date:** 2026-06-08
**URL:** https://simonwillison.net/2026/Jun/8/wwdc/#atom-everything

## Resumo

Given how badly burned anyone who took Apple's 2024 WWDC Apple Intelligence announcements at face value was, I'm holding to a strict "I'll believe it when I see it" policy for everything they announced today .

The new Siri AI features do at least look feasible with today's technology, especially since Apple are licensing a custom Gemini-derived model that they can run on their own Private Cloud Compute .

It sounds like they'll be taking advantage of vision LLMs to extract information from the user's screen, which neatly sidesteps the need for every existing application to ship custom code in order to integrate with Apple Intelligence. Vision LLMs were a much less mature category in June 2024.

The new Core AI library looks like a good step in enabling developers to finally take full advantage of Apple's hardware for running their own models. It integrates with Meta's open source PyTorch ecosystem, using these Core AI PyTorch extensions :

Core AI PyTorch Extensions ( coreai-torch ) is a Python package that bridges PyTorch and Core AI. You can use it to bring up an existing PyTorch model — exported as a torch.export.ExportedProgram — into a Core AI AIProgram ready to run on Apple hardware, traversing the FX graph node-by-node and mapping ATen operators to Core AI operations.

You can install an iOS 27 Developer Beta today, which supposedly has the new features - but you then have to make it through a waiting list for access to the new Siri AI. Aaron Perris from MacRumors reports having made it off the waitlist so we may start seeing credible reports on how well Siri AI works in the very near future.

## Pontos-chave

- The new Siri AI features do at least look feasible with today's technology, especially since Apple are licensing a custom Gemini-derived model that they can run on their own Private Cloud Compute .
- The new Core AI library looks like a good step in enabling developers to finally take full advantage of Apple's hardware for running their own models.
- Core AI PyTorch Extensions ( coreai-torch ) is a Python package that bridges PyTorch and Core AI.
- You can install an iOS 27 Developer Beta today, which supposedly has the new features - but you then have to make it through a waiting list for access to the new Siri AI.
- Update : These Private Cloud Compute Gemini models are running in Google Cloud, and using NVIDIA hardware.

## Notas e Conexões

- Fonte: [[Simon Willison]]
- Ver [[References]]
