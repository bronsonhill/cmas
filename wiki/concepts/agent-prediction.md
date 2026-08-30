---
title: Agent Prediction
type: concept
tags: [abm, agent-behaviour, odd]
date: 2026-08-30
---

# Agent Prediction

Prediction, as an ODD design concept, is how an agent estimates the future consequences of
an action in order to decide now. Any [[objective-function|objective]] defined over a time
horizon implies one.

## How it works

Prediction can be explicit or hidden in a constant. The [[business-investment-model]]
projects $T$ years of profit at rate $P$ and $T$ years of survival at rate $1-F$, and the
model declares that this prediction is **accurate**, because $P$ and $F$ are static and
sensed without error.

That assumption is the model's largest simplification, and the lecture said so. Real
profit and failure risk move — NVIDIA was a niche graphics-hardware supplier not long ago
— which is exactly why investment products carry a "past returns are no indication of
future returns" disclaimer. Modelling a prediction as perfect converts an economics
problem into an arithmetic one.

The realistic alternatives all degrade the prediction deliberately: add noise to it,
extrapolate from a short remembered history, or let the agent predict from a biased model
of the world. Kennedy's parallel idea is the
[[social-influence|theory of mind]] — a human's prediction of other agents' behaviour is a
model of *them*, not of the environment.

Grimm's 2020 ODD update lists prediction and [[agent-learning|learning]] as two separate
design concepts; the 2010 version and the lecture treatment merge them.

## Relationships

- [[objective-function]] — a horizon-based objective needs a prediction to evaluate
- [[imperfect-information]] — prediction error is one more form of imperfection
- [[adaptive-behaviour]] — decisions that depend on the future
- [[odd-protocol]] / [[grimm-2020-odd-second-update]]

## Sources

- [[w05a-sensing]] — prediction named among the design concepts
- [[w05b-adaptation-and-objectives]] — the accurate-prediction assumption and why it is
  strong
