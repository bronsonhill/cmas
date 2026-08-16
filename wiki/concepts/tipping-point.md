---
title: Tipping Point
type: concept
tags: [complexity, analysis]
date: 2026-08-01
---

# Tipping Point

A tipping point (or phase transition) is a region of a model's parameter space where the
system's qualitative behaviour changes abruptly rather than gradually — a small parameter
change producing a large, categorical difference in outcome.

## How it works

Emergent behaviour is not uniform across parameter settings. In the [[flocking]] model,
one combination of vision, turn rate and speed produces lively coherent flocks; nudge the
parameters and the population locks into an inert steady state, or fails to form flocks at
all. The interesting values are the ones at the boundary.

Locating these boundaries is a core analytical activity: it means sweeping parameters
rather than examining a single run, and — because these models are stochastic — replicating
at each setting (see [[stochasticity]]).

The COVID-19 compliance results are a policy-relevant instance: 70% compliance with
physical distancing left the epidemic growing, while 80% flattened the curve
([[covid-19-abm-australia]]). The consequential fact is not the shape of either curve but
that a threshold sits between them.

Week 3 supplies two more instances and a name for them: critical points, or phase
transitions. In the [[schelling-segregation-model]], raising the similarity threshold from
30% to 70% does not intensify segregation smoothly — past roughly 70% the model stops
converging altogether, because too few households can be satisfied at once. And in epidemic
models the [[reproduction-number]] crossing one separates extinction from potential
outbreak, which is the subject's cleanest example: below the threshold the outbreak dies out
regardless of how many infectious individuals it starts with, and above it exponential
growth becomes possible.

Thresholds also leave a signature in output. When runs land in one of two regimes rather
than spreading across the range, the distribution of a summary measure comes out bimodal
([[bimodal-distribution]]), so finding bimodality is often the first evidence that a
threshold exists.

## Why it matters

Tipping points are where models earn their keep for decision-making. If system response
were smooth and monotonic, intuition or interpolation would suffice; because it is not,
identifying thresholds is often the whole point of building the model.

## Relationships

- [[emergence]], [[complex-system]] — the setting in which tipping points arise
- [[flocking]] — in-class demonstration of parameter-dependent regimes
- [[stochasticity]] — replication needed to distinguish a threshold from noise
- [[reproduction-number]] — the threshold at $R = 1$
- [[schelling-segregation-model]] — convergence failure above a ~70% similarity threshold
- [[bimodal-distribution]] — the output signature of a two-regime system

## Sources

- [[w01a-introduction]] — flags tipping points / phase transitions as a recurring theme of
  the Thursday model-exploration lectures.
- [[w03a-analysing-models]] — the segregation model's convergence breakdown at high
  similarity thresholds.
- [[w03b-reproduction-number]] — names critical points and phase transitions as the general
  phenomenon, with $R = 1$ as the epidemic instance.
