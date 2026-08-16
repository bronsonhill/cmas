---
title: Summary Statistic
type: concept
tags: [model-analysis, statistics, simulation]
date: 2026-08-16
---

# Summary Statistic

A summary statistic is a number computed from simulation output that stands in for the
output itself. Choosing summary statistics is how the analysis of a simulation model becomes
tractable, and choosing them badly is how it becomes wrong.

## How it works

An agent-based model can emit the full trajectory of every agent and every environment
variable at every step. The lecture's arithmetic makes the scale clear: 100 agents over 100
steps over 100 runs over 100 scenarios is already a hundred million observations, and none
of it is interpretable as raw output. So you record observations of interest instead, chosen
from the question the model was built to answer ([[research-question]]).

Statistical analysis of a simulation model then does four things: quantify outputs as
summary statistics, use those statistics to compare alternative scenarios, quantify how
model parameters relate to the statistics, and compare the statistics against observed data.
Each requires the statistic to be a faithful compression, and the last requires it to be
something the real world also reports.

For an outbreak the standard choices are final size, peak size and peak timing
([[outbreak-summary-measures]]), each of which corresponds to a decision someone has to
make. That correspondence is the test of a good summary measure: if no decision changes when
the number changes, it is not worth recording.

## Why it matters

The trap is that summarising a stochastic model means summarising a *distribution*, and the
mean is only informative for distributions shaped a certain way. The lecture's SIR runs
produce a bimodal final-size distribution — roughly 45% of runs near zero, the rest around
5,200 of 10,000 agents ([[stochastic-fadeout]]). The mean falls near 3,000, in the empty
valley between the modes, and describes no run that occurred. Reported on its own it implies
a moderate outbreak is typical when in fact moderate outbreaks essentially never happen.

The order of operations that avoids this is: choose what to measure, run the model many
times, look at the *distribution* of the measurement, and only then decide how to compress
it. A bimodal distribution needs a mixture description — the probability of each mode and a
summary within each — rather than a single number ([[bimodal-distribution]]). The lecture's
stated takeaway was exactly this: once you have determined which data points you care about,
do not compress them blindly.

This is a specific instance of a general failure mode. Any summary discards information, and
the question is always whether it discarded the part that mattered for the decision at hand.

## Relationships

- [[outbreak-summary-measures]] — the specific statistics used for epidemics
- [[bimodal-distribution]] — the shape that breaks the mean
- [[stochastic-fadeout]] — the mechanism producing that shape here
- [[stochasticity]] — why a single run cannot be the summary
- [[model-analysis]] — the activity summary statistics serve
- [[research-question]] — what determines which observations are worth recording
- [[pattern-oriented-modelling]] — comparing model summaries against observed patterns

## Sources

- [[w03a-analysing-models]] — the four purposes of statistical analysis of simulation
  models, the output-volume argument, the choice of outbreak observations, and the worked
  demonstration that the mean of a bimodal final-size distribution is uninformative.
