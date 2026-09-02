---
title: PECS Framework
type: concept
tags: [cognition, agent-behaviour, abm]
date: 2026-08-30
---

# PECS Framework

PECS (Schmidt 2002) models an agent's behaviour from four classes of factor: **physical**,
**emotional**, **cognitive**, and **social**. It was proposed as a more specific and more
implementable replacement for [[bdi-architecture|BDI]].

## How it works

PECS includes an explicit representation of perception and behaviour plus mathematical
representations of physiology, emotion, cognition and social status. Inside the cognitive
component sit transformations for a self-model, an environmental model, memory for
behaviour protocols, planning and reflection.

The pipeline runs: environmental parameters → internal state variables → **drives, needs
and desires** → **motives** → behaviour. Motives are state variables whose *intensity*
determines behaviour indirectly, which is what lets the framework span both simple
stimulus-response behaviour and deliberative behaviour in one structure.

Two difficulties, both named by Kennedy:

- Setting the internal parameters of the transformations from environment to internal
  state. There is rarely data to fit them against.
- Combining, prioritising and integrating multiple simultaneous motives into one selected
  behaviour. Maslow's hierarchy of needs is one ordering scheme available for this.

## Why it matters

PECS's advantage is explanatory: an agent's behaviour can be traced back to plausible
causes. That matters for [[model-communication|communicating]] a model to domain experts,
who will accept "the agent acted on hunger overriding a social motive" more readily than
"utility term three exceeded 0.6". The cost is a parameter set that is hard to justify
empirically, which is the recurring problem with every richer model of human behaviour.

## Relationships

- [[bdi-architecture]] — what PECS was proposed to replace
- [[cognitive-architecture]] — the more expensive tier above
- [[objective-function]] — motives play the role objectives do in simpler models
- [[kennedy-2012-modelling-human-behaviour]]

## Sources

- [[kennedy-2012-modelling-human-behaviour]] — the four factors, the motive pipeline, and
  the two challenges
