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

## Why it matters

Tipping points are where models earn their keep for decision-making. If system response
were smooth and monotonic, intuition or interpolation would suffice; because it is not,
identifying thresholds is often the whole point of building the model.

## Relationships

- [[emergence]], [[complex-system]] — the setting in which tipping points arise
- [[flocking]] — in-class demonstration of parameter-dependent regimes
- [[stochasticity]] — replication needed to distinguish a threshold from noise

## Sources

- [[w01a-introduction]] — flags tipping points / phase transitions as a recurring theme of
  the Thursday model-exploration lectures.
