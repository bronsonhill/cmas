---
title: Sensitivity Analysis
type: concept
tags: [methodology, model-analysis, experiments]
date: 2026-08-19
---

# Sensitivity Analysis

Sensitivity analysis is re-running a model across a range of values for a parameter to see
how much the results depend on that parameter. It separates conclusions driven by the
system's structure from conclusions that are artefacts of a number someone chose.

## How it works

Hold everything else fixed, vary one parameter, and compare the outputs. For a stochastic
model each value needs a set of runs rather than a single run, since run-to-run variation
would otherwise be mistaken for a parameter effect ([[stochasticity]],
[[stochastic-fadeout]]). Compare distributions of a [[summary-statistic]] — for epidemic
models usually one of the [[outbreak-summary-measures]].

Two outcomes are informative in different ways. If the result barely moves, the conclusion
is robust to that choice and the parameter need not be pinned down precisely. If it moves a
lot, the parameter is doing the work, and any claim from the model is only as good as the
evidence for that value.

The parameters most worth varying are the ones introduced by a
[[model-extension]], because those are the least empirically grounded — they exist because a
modeller added a mechanism, not because a field study measured something. Assignment 1
requires exactly this: vary one key parameter of the extension across a couple of values and
report how the behaviour changes ([[a1-project-specification]]).

## Why it matters

Model parameters are usually estimated, borrowed from another study, or guessed. Reporting a
result at one parameter setting hides how contingent it is. It also connects to
[[model-analysis]] more generally — understanding what the model does is a precondition for
using it, and the response to a parameter change is one of the cheapest ways to learn that.

## Relationships

- [[model-analysis]] — sensitivity analysis is one of its standard tools
- [[model-extension]] — the new parameters an extension introduces are the priority targets
- [[summary-statistic]] — what gets compared across parameter values
- [[initial-conditions]] — varying starting state rather than parameters, same logic
- [[reproducibility]] — reporting the swept range is part of a reproducible experiment

## Sources

- [[a1-project-specification]] — requires a comparison across two values of one key parameter
  of the model extension, framed as checking how sensitive results are to design choices.
- [[epstein-2008-why-model]] — names parameter sweeps as a decisive advantage of explicit
  over implicit models: they identify salient uncertainties, regions of robustness and
  important thresholds.
