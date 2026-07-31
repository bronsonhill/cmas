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

## Why it matters

Stochasticity is what makes results from an [[agent-based-model]] a statistical claim
rather than a deterministic prediction. Ignoring it is the fastest way to over-read a
single striking run. Sensitivity and uncertainty analysis occupy weeks 10–12 of the
subject; the tutorials introduce replication and confidence levels earlier.

## Relationships

- [[simulation]] — where the randomness is realised
- [[agent-based-model]] — the models concerned
- [[tipping-point]] — replication is required to establish thresholds
- [[modelling-cycle]] — verification of a stochastic model means comparing distributions

## Sources

- [[w01a-introduction]] — flagged in response to a student question on confidence levels;
  replication and sensitivity analysis named as the handling strategies.
