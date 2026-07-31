---
title: Modelling Cycle
type: concept
tags: [methodology, abm]
date: 2026-08-01
---

# Modelling Cycle

The modelling cycle is the iterative process by which a [[model]] is developed: start from
a hypothesis, build the model, check whether it reproduces the patterns of interest, then
refine — repeating until the model is adequate for its purpose.

## How it works

The loop, as introduced in Week 1:

1. **Hypothesis** — state the question and the mechanism you believe generates the
   behaviour of interest.
2. **Build** — implement the model, choosing agents, rules and environment in light of the
   purpose (see [[model]]).
3. **Verify** — run it and check whether the expected patterns are reproduced.
4. **Refine** — adjust structure or parameters and repeat.

Termination is a judgement call: you stop when the model does what you need it to do for
the question at hand, not when it is maximally realistic.

The cycle is elaborated in weeks 1–3 alongside the ODD (Overview, Design concepts,
Details) protocol for describing ABMs, and its later stages connect to the week 10–12
material on calibration, sensitivity and uncertainty analysis.

## Why it matters

Modelling is not a one-shot translation from system to code. The cycle is what makes model
building an empirical practice — it enforces the discipline of checking the model against
patterns rather than trusting its plausibility, and it makes explicit that a first model
is expected to be wrong.

## Relationships

- [[model]], [[agent-based-model]] — what is being built
- [[stochasticity]] — verification of a stochastic model requires replication
- [[optimisation]] — model-level parameter tuning at the end of the cycle

## Sources

- [[w01a-introduction]] — outlines the cycle as the weeks 1–3 content, alongside the ODD
  protocol and visualisation of model outputs.
