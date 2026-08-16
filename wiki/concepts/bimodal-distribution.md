---
title: Bimodal Distribution
type: concept
tags: [statistics, model-analysis, stochasticity]
date: 2026-08-16
---

# Bimodal Distribution

A bimodal distribution has two distinct peaks separated by a region of low probability.
Simulation output from stochastic models is frequently bimodal, and the practical
consequence is that the mean of such a distribution can describe an outcome that never
occurs.

## How it works

Bimodality arises when a system has two qualitatively different regimes and the run lands in
one or the other rather than somewhere in between. The lecture's case is an epidemic: either
transmission establishes and sweeps a large fraction of the population, or it fades out in
the first few generations and infects almost nobody ([[stochastic-fadeout]]). There is no
mechanism that produces an outbreak of intermediate size, so the region between the modes is
nearly empty.

The final-size histogram from repeated SIR runs at $N = 10{,}000$, $\beta = 2.5$,
$\gamma = 0.4$ shows this directly: a spike at approximately zero holding about 45% of runs,
a gap across most of the range, and a roughly normal cluster centred near 5,200 infections.
The peak-size and peak-timing distributions have the same two-regime structure.

The mean falls between the modes, near 3,000 infections. That value is not merely imprecise;
it points at the part of the range where the model produces almost no outcomes. The median
is no better here — it depends entirely on which side of 50% the fadeout probability sits,
so it flips between "almost nobody infected" and "half the population infected" under small
parameter changes.

The correct description is a mixture: state the probability of each regime and summarise
within each. "About 45% of the time the outbreak fails; otherwise around 5,200 people are
infected" carries the information that "on average 3,000 people are infected" destroys.

## Why it matters

Detecting bimodality is the reason to plot the distribution of a summary measure before
compressing it ([[summary-statistic]]). The failure is silent — a mean is always computable
and always looks like an answer — so nothing in the output signals that the compression was
invalid.

The two-regime structure is also informative in its own right, not just an obstacle. It says
the system has a threshold in it. In the epidemic case that threshold is the
[[reproduction-number]] crossing one within a particular run's realised transmission, which
is the same critical-point phenomenon as the segregation model failing to converge above a
70% similarity threshold ([[tipping-point]]). Finding bimodality in output is often the
first sign that a model contains a qualitative transition worth investigating.

## Relationships

- [[summary-statistic]] — the choice bimodality constrains
- [[stochastic-fadeout]] — the mechanism producing it in epidemic models
- [[outbreak-summary-measures]] — all three are bimodally distributed
- [[stochasticity]] — bimodality is a property of the outcome distribution, so it requires a
  stochastic model to appear at all
- [[tipping-point]] — the threshold that separates the two regimes
- [[model-analysis]] — where the check belongs in the workflow

## Sources

- [[w03a-analysing-models]] — the bimodal final-size, peak-size and peak-timing histograms,
  and the argument that the mean of the final-size distribution is uninformative.
