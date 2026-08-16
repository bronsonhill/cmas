---
title: Stochastic Fadeout
type: concept
tags: [epidemiology, stochasticity, sir-model]
date: 2026-08-16
---

# Stochastic Fadeout

Stochastic fadeout is the extinction of an outbreak by chance in its early stages, before
transmission has established, even when the [[reproduction-number]] is well above one. It is
a property of stochastic epidemic models that their deterministic counterparts cannot
produce.

## How it works

$R_0$ is an *average*. Early in an outbreak the number of infectious individuals is tiny, so
the realised number of onward infections is a small sample from a distribution whose mean is
$R_0$, and small samples can come out at zero. If the first case recovers before infecting
anyone, the chain terminates regardless of how transmissible the disease is in aggregate. A
few unlucky draws in the first handful of generations end the outbreak permanently.

Once the infectious pool is large enough, the law of large numbers takes over and the
realised growth rate tracks $R_0$ closely. Fadeout is therefore concentrated in the earliest
generations, which is why the failed runs in the lecture's peak-timing histogram cluster
near $t = 0$ — they never got going.

The lecture's stochastic SIR runs at $N = 10{,}000$, $\beta = 2.5$, $\gamma = 0.4$ give
$R_0 = 6.25$, which is high. Roughly 45% of runs still produced essentially no infections.
This is the single most common outcome at those settings, and it is the reason the
final-size distribution is bimodal ([[bimodal-distribution]]) rather than clustered around a
mean.

Raising the population to a million smooths the individual trajectories — the curves become
less jagged and the peak height becomes predictable — but the fadeout mode does not
disappear. Population size damps variability *within* an established outbreak; it does not
change what happens in the first few generations, which still involve a handful of cases
whatever the population size.

Fadeout also explains the behaviour below the threshold. At $\beta = 0.25$, $\gamma = 0.4$
($R_0 = 0.625$), every run dies out, and seeding with 100 initial infectious agents instead
of one does not change that. The lecturer's real-world analogue was H5N1 influenza, which
spreads from birds to humans but does not sustain human-to-human transmission — repeated
introductions, each of which fades.

## Why it matters

Fadeout is the clearest case in the subject where a summary statistic misleads. Reporting
the mean final size of these runs gives roughly 3,000 infections, a number that describes
neither the failed runs nor the established ones ([[summary-statistic]]). The honest summary
is two numbers and a probability: about 45% of the time almost nobody is infected, and the
rest of the time around 5,200 people are.

For policy this is the difference between a point forecast and a risk assessment. A model
that only reports the average outbreak understates both the chance of getting away with it
and the severity when you do not.

It is also the sharpest argument for choosing a stochastic model over a
[[deterministic-model]]. The deterministic SIR model with $R_0 = 6.25$ produces an outbreak
every time, because it propagates the expected flow rather than sampling from it. The entire
fadeout mode is invisible to it.

## Relationships

- [[stochasticity]] — the property that makes fadeout possible
- [[reproduction-number]] — why $R_0 > 1$ means "may take off" rather than "will"
- [[bimodal-distribution]] — the shape fadeout produces in output distributions
- [[deterministic-model]] — cannot represent this behaviour
- [[summary-statistic]] — why the mean is the wrong compression here
- [[initial-conditions]] — seeding more infectious agents does not overcome $R_0 < 1$
- [[sir-model]] — the model in which it was demonstrated

## Sources

- [[w03a-analysing-models]] — the bimodal final-size, peak-size and peak-timing histograms
  at $R_0 = 6.25$, the ~45% fadeout proportion, and the persistence of the mode at
  $N = 1{,}000{,}000$.
- [[w03b-reproduction-number]] — the sub-threshold runs from 1 and from 100 initial
  infectious agents, and the H5N1 analogue.
