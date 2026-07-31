---
title: Pattern-Oriented Modelling
type: concept
tags: [methodology, analysis, calibration]
date: 2026-08-01
---

# Pattern-Oriented Modelling

Pattern-oriented modelling is the practice of judging a model by whether it reproduces the
*patterns* observed in the real system, rather than by whether it matches exact numerical
values.

## How it works

Given real-world data, the target is qualitative structure: does the model produce cycles
where the data shows cycles? Spikes where the data shows spikes? Does it show the same
threshold behaviour? Matching the precise numbers is usually neither achievable nor the
point — an ABM of a stochastic system will not reproduce a particular trajectory, and
should not be tuned until it does.

This is why "Patterns!" appears twice on the [[modelling-cycle]] diagram: once between
assembling hypotheses and choosing model structure — patterns tell you what mechanisms the
model needs — and once between analysing the model and communicating it, where they are
the criterion for whether the model has succeeded.

The converse is diagnostic. If a model fails to reproduce a pattern known to exist, some
mechanism is wrong or missing. As raised in class: if a simulation doesn't produce the
expected behaviour, either that genuinely is how the system behaves, or something in the
model is uncontrolled — and either way it is information worth having.

Pattern-oriented modelling is developed in weeks 10–12 alongside calibration, sensitivity
and uncertainty analysis.

## Why it matters

It sets a realistic and honest standard for model validation. Chasing exact numerical
agreement encourages overfitting — adding parameters until the curve matches — which
produces a model that reproduces one dataset and explains nothing. Patterns are the level
at which a [[complex-system]] model can genuinely be right.

## Relationships

- [[modelling-cycle]] — the "Patterns!" checkpoints
- [[stochasticity]] — why exact trajectories are not the target
- [[complex-system]], [[emergence]] — patterns are the emergent signatures being matched
- [[tipping-point]] — threshold behaviour as a pattern to reproduce

## Sources

- [[w01b-modelling-cycle]] — named in response to a student suggestion about using
  historical data; flagged as end-of-subject material, with "cycles with spikes" as the
  illustration of pattern rather than value matching.
