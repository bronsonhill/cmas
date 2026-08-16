---
title: Outbreak Summary Measures
type: concept
tags: [epidemiology, model-analysis, statistics, assignment-1]
date: 2026-08-16
---

# Outbreak Summary Measures

The three standard summaries of a simulated epidemic are the final size, the size of the
peak, and the timing of the peak. Each maps onto a decision a health system has to make,
which is why these three and not others.

## How it works

**Final size** is the total number of people infected by the end of the outbreak. Expressed
as a proportion of the population it is the final attack rate. It answers the question of
total burden, and it is the quantity the [[reproduction-number]] predicts through the
saturating attack-rate relationship — steeply rising between $R_0 = 1$ and $R_0 = 2$, close
to complete above $R_0 = 4$.

**Peak size** is the greatest number infectious at any one time. It answers the question of
peak demand: how many hospital beds, ventilators or staff are needed simultaneously. A
disease can have a modest final size and still overwhelm a health system if it arrives all
at once.

**Peak timing** is when that maximum occurs. It answers the question of preparation time.
The lecture's smallpox-like profile ($R_0 = 4$, 14 days infectious) peaks around day 40
against the measles-like profile's day 5, and that difference is the window in which an
intervention can be organised. "Flattening the curve" is an intervention aimed at these last
two measures — lowering the peak and pushing it later — rather than at the final size.

Peak size and peak timing separate the effects of the two SIR parameters in a way $R_0$
alone does not. Chickenpox-like and mumps-like profiles in the lecture share $R_0 = 8$ and
reach a similar peak height near 620, but the mumps-like profile's fourteen-day infectious
period moves the peak from day 9 to day 18 and stretches the decline, so beds are occupied
far longer for the same number of cases.

## Why it matters

These measures are the worked example for why summarising a stochastic model needs care.
All three are bimodally distributed across repeated runs of the same configuration, because
roughly 45% of runs fade out before establishing ([[stochastic-fadeout]]). Peak timing is
the noisiest of the three: the failed runs pile up near $t = 0$ while the established ones
form a broad mode around $t = 45$. Taking the mean of any of them produces a number no run
produced ([[summary-statistic]], [[bimodal-distribution]]).

Scaling the population from ten thousand to a million changes the three unevenly. Peak size
becomes highly predictable, final size becomes predictable conditional on the outbreak
establishing, but peak timing stays variable — the early stochastic phase determines when
growth begins, and that phase involves few individuals whatever the population size.

When [[model-extension|extending the model]] these are also the natural candidates for what
to record. The measure to instrument is the one the stated question turns on, not all three
by default.

## Relationships

- [[summary-statistic]] — the general concept these instantiate
- [[stochastic-fadeout]] — why their distributions are bimodal
- [[bimodal-distribution]] — the resulting shape
- [[reproduction-number]] — predicts final size via the attack-rate relationship
- [[sir-model]] — the model producing them
- [[epidemic-intervention]] — targets peak size and peak timing
- [[research-question]] — determines which measure to record

## Sources

- [[w03a-analysing-models]] — names the three measures and their decision-relevance, gives
  the bimodal histograms for each, and shows how the distributions change at
  $N = 1{,}000{,}000$.
- [[w03b-reproduction-number]] — the four disease profiles separating peak height, peak
  timing and infectious duration, and the final attack rate against $R_0$.
