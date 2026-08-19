---
title: Explanation vs Prediction
type: concept
tags: [methodology, modelling-philosophy, epistemology]
date: 2026-08-19
---

# Explanation vs Prediction

Explaining a phenomenon and predicting it are separate achievements. A model can account for
why something happens without being able to say when or where the next instance will occur,
and the reverse also happens — a purely statistical model can forecast well while explaining
nothing.

## How it works

The standard examples are physical. Plate tectonics explains earthquakes; it does not
predict the time and place of the next one. Electrostatics explains lightning; nobody knows
where the next bolt lands. Evolution explains speciation without predicting the next
species. In each case the mechanism is understood and the specific outcome is not
forecastable, because the outcome depends on initial conditions nobody can measure at the
required resolution, or on chance ([[stochasticity]]).

The conflation matters because prediction is the goal an outside critic assumes by default.
[[joshua-epstein]] lists sixteen goals other than prediction — explaining, guiding data
collection, bounding outcomes to plausible ranges, exposing tradeoffs, challenging a
prevailing theory by perturbing it, training practitioners, disciplining a policy debate —
and most modelling work in this subject targets one of those
([[epstein-2008-why-model]]).

Where prediction is the goal, it is usually prediction of a distribution rather than a
trajectory. Epidemic models predict the shape of an outbreak and the plausible range of its
final size, not which individual gets infected on day 12
([[outbreak-summary-measures]], [[stochastic-fadeout]]).

## Why it matters

The distinction sets what counts as success. A model built to explain is judged on whether
the mechanism reproduces the qualitative pattern ([[pattern-oriented-modelling]]); a model
built to predict is judged against data it has not seen. Applying the wrong standard either
rejects a good explanatory model for failing a test it was never designed to pass, or
accepts a forecast whose mechanism is nonsense.

It also decides what to tell a stakeholder. "This model shows the mechanism that produces
the second wave" and "this model says the second wave peaks in March" are different claims
with different liabilities ([[modelling-for-policy]], [[counterfactual]]).

## Relationships

- [[generative-explanation]] — what explanation means for an agent-based model
- [[modelling-for-science]], [[modelling-for-policy]] — the two goal families
- [[pattern-oriented-modelling]] — the evaluation standard for explanatory models
- [[model-analysis]] — deciding which standard applies is part of analysis
- [[occams-razor]] — explanatory value does not require realism

## Sources

- [[epstein-2008-why-model]] — the essay this distinction comes from, with the tectonics and
  electrostatics examples and the sixteen alternative goals.
