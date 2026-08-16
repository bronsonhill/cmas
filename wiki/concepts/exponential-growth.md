---
title: Exponential Growth
type: concept
tags: [epidemiology, dynamics]
date: 2026-08-06
---

# Exponential Growth

Exponential growth is the regime in which the increase in a quantity is proportional to its
current size, so that the quantity multiplies by a constant factor each period. In an
epidemic it is the early-phase behaviour of case counts when each infectious person infects
more than one other before recovering.

## How it works

In the [[sir-model]], growth is exponential while the susceptible pool is effectively
unlimited and each infectious agent produces more than one secondary infection during its
infectious period. That product is set by the per-contact infection probability $q$, the
[[contact-rate]] $c$, and the infectious duration implied by $\gamma$. High $q$ with low
$\gamma$ — easily transmitted, slow to recover — is the parameter combination the lecture
identified as producing exponential growth and a large simultaneous infectious pool.

Week 3 gives that product a name and a formula. The [[reproduction-number]] $R_0 =
\beta/\gamma$ is the average number of secondary infections per case in a fully susceptible
population, and $R > 1$ is precisely the condition for exponential growth to be possible.
Below one the outbreak dies out. Above one it *may* take off, because early transmission is
stochastic and a chain can fail by chance before establishing
([[stochastic-fadeout]]) — which is why the growth regime is a possibility rather than a
guarantee.

Growth stops being exponential for one of two reasons. The susceptible pool depletes, since
the model is finite and each infection removes a potential future host, which is what bends
the cumulative curve into its characteristic flattening shape. Or an
[[epidemic-intervention]] changes the parameters mid-run, which is what the lecture read off
the 2003 SARS curve: the case increments dropped sharply after an intervention around May,
and the cumulative curve flattened.

The contrast between the two outbreaks discussed is the pedagogical point.
[[sars-2003-outbreak]] was contained in the thousands of cases; [[covid-19-pandemic]] grew
exponentially in cumulative cases through the first half of 2020. Same model class, very
different outcomes, driven by transmission parameters and by how quickly the contact
structure was changed.

## Why it matters

Recognising the growth regime is what makes early intervention urgent: under exponential
growth, delay does not add cases linearly. It is also a pattern to validate a model against
— an implementation whose case curve grows linearly when the real system grew exponentially
has a structural problem, not a calibration problem
([[pattern-oriented-modelling]]).

## Relationships

- [[sir-model]] — where the regime arises
- [[contact-rate]] — one of the factors setting the growth rate
- [[epidemic-intervention]] — the mechanism for breaking out of the regime
- [[tipping-point]] — a related qualitative change in system behaviour
- [[sars-2003-outbreak]], [[covid-19-pandemic]] — the contrasting cases
- [[reproduction-number]] — the threshold condition for the regime
- [[stochastic-fadeout]] — why $R > 1$ does not guarantee growth
- [[difference-equation]] — the equations from which the growth condition is derived

## Sources

- [[w02b-modelling-disease-spread]] — the SARS-versus-COVID curve comparison and the
  high-$q$, low-$\gamma$ parameter reasoning.
- [[w03b-reproduction-number]] — $R_0 = \beta/\gamma$ as the condition separating growth
  from extinction, and the generation diagrams showing the branching cascade.
