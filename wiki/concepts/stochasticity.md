---
title: Stochasticity
type: concept
tags: [methodology, analysis]
date: 2026-08-01
---

# Stochasticity

Stochasticity is the presence of randomness in a model: the same model, run twice from the
same parameters, can produce different outcomes.

## How it works

Agent-based models are stochastic almost by construction — initial placement, the order in
which agents act, and the choices they make are typically randomised. A single run is
therefore one draw from a distribution of outcomes, not *the* outcome.

Two practices follow:

- **Replication** — run each parameter setting many times and reason about the
  distribution of results (means, spread, confidence intervals), not a single trajectory.
- **Sensitivity analysis** — vary parameters systematically to distinguish genuine
  parameter effects from run-to-run noise. This is essential when claiming a
  [[tipping-point]] exists.

Reasoning about the distribution is not the same as taking its mean. Week 3 supplies the
counterexample: repeated runs of an identical SIR configuration produce a
[[bimodal-distribution]] of final sizes, because roughly 45% of runs fade out before the
outbreak establishes ([[stochastic-fadeout]]). The mean of that distribution falls between
the two modes and describes no run that occurred, so replication has to be followed by
inspecting the shape of the results before compressing them ([[summary-statistic]]).

## Why it matters

Stochasticity is what makes results from an [[agent-based-model]] a statistical claim
rather than a deterministic prediction. Ignoring it is the fastest way to over-read a
single striking run. Sensitivity and uncertainty analysis occupy weeks 10–12 of the
subject; the tutorials introduce replication and confidence levels earlier.

The reason to accept that cost is that tail events matter. A stochastic model can produce
rare, high-impact outcomes that an averaged treatment of the same system never generates —
the Week 3b lecture raised black swans in exactly these terms. Where those outcomes are not
what the decision turns on, a [[deterministic-model]] gives the typical trajectory more
cheaply and is tractable analytically; the choice between the two follows the question.

## Relationships

- [[simulation]] — where the randomness is realised
- [[agent-based-model]] — the models concerned
- [[tipping-point]] — replication is required to establish thresholds
- [[modelling-cycle]] — verification of a stochastic model means comparing distributions
- [[sir-model]] — both transitions are random draws against a threshold
- [[scheduling]] — the order of actions determines which draws apply to which agents
- [[reproducibility]] — a stochastic result is reproducible only with the seed or enough
  replicates
- [[deterministic-model]] — the alternative, and what it trades away
- [[stochastic-fadeout]], [[bimodal-distribution]] — what run-to-run variation looks like in
  the SIR model
- [[summary-statistic]] — how to compress a distribution without misrepresenting it

## Sources

- [[w01a-introduction]] — flagged in response to a student question on confidence levels;
  replication and sensitivity analysis named as the handling strategies.
- [[w02a-describing-models]] — named as one of the ten ODD design concepts.
- [[w02b-modelling-disease-spread]] — the SIR implementation, where infection and recovery
  are both decided by drawing a random number and comparing it against $q$ or $\gamma$;
  the traced run is explicitly one sample of a stochastic system.
- [[w03a-analysing-models]] — the bimodal output distributions from repeated runs, and the
  demonstration that population size damps trajectory variability without removing the
  fadeout mode.
- [[w03b-reproduction-number]] — the argument for wanting stochasticity (tail events) set
  against the argument for deterministic models (the typical case, and tractability).
