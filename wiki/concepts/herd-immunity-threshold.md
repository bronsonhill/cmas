---
title: Herd Immunity Threshold
type: concept
tags: [epidemiology, vaccination, intervention, sir-model]
date: 2026-08-16
---

# Herd Immunity Threshold

The herd immunity threshold is the fraction of a population that must be immune for an
outbreak to be unable to establish. For the [[sir-model]] it is $1 - 1/R_0$, so the coverage
required rises with the [[reproduction-number]] and approaches complete coverage for highly
transmissible diseases.

## How it works

A case with basic reproduction number $R_0$ produces $R_0$ onward infections when every
contact is susceptible. If a fraction $v$ of the population is immune, only $(1-v)$ of those
contacts can be infected, so the effective reproduction number becomes $R_0(1-v)$. Setting
that below one and solving for $v$ gives the threshold.

The mechanism is indirect protection. Immune individuals do not merely avoid infection
themselves; they absorb transmission chains that would otherwise have continued, which
protects susceptible people who were never vaccinated. The lecture's generation diagram
makes this visible — vaccinating part of generation one breaks the branches below it, and
the cascade collapses even though some susceptible individuals remain.

In the simplest modelling treatment, vaccination is represented by moving individuals
directly from the $S$ compartment to $R$ before the outbreak starts. This is crude: it
assumes the vaccine is perfectly and immediately effective, and it cannot represent waning
immunity or partial protection. Representing an imperfect vaccine needs a separate state
with a reduced infection probability rather than a transfer to $R$
([[model-extension]]).

## Formula

$$v \ge 1 - \frac{1}{R_0}$$

Values from the lecture chart:

| $R_0$ | Threshold $v$ |
|---|---|
| 1 | 0% |
| 1.25 | 20% |
| 1.6 | 37.5% |
| 2 | 50% |
| 2.5 | 60% |
| 4 | 75% |
| 5 | 80% |
| 8 | 87.5% |
| 10 | 90% |
| 12.5 | 92% |
| 16 | 93.75% |
| 20 | 95% |

## Why it matters

The threshold converts an epidemiological parameter into a public health target, and its
shape explains a policy asymmetry. Because the curve is steep at low $R_0$ and flat at high
$R_0$, a disease with $R_0 = 2$ tolerates half the population being susceptible, while
measles at $R_0 = 16$ leaves under 7% of slack. Highly transmissible diseases are therefore
the first to return when coverage slips — the lecture cited the Texas measles outbreak,
attributed to coverage falling below the threshold.

It also gives [[epidemic-intervention]] a quantitative criterion. Any intervention that
reduces the effective reproduction number below one will contain an outbreak; vaccination is
one route to that, and reducing contact rates through distancing or lockdowns is another.

## Relationships

- [[reproduction-number]] — the input to the formula
- [[epidemic-intervention]] — vaccination as one intervention among several
- [[sir-model]] — where the $S \to R$ representation sits
- [[compartmental-model]] — vaccination as a change to the compartment diagram
- [[model-extension]] — representing imperfect vaccines needs a new state

## Sources

- [[w03b-reproduction-number]] — gives $v \ge 1 - 1/R_0$, the threshold chart, the
  generation diagram showing broken transmission chains, the $S \to R$ modelling treatment,
  and the Texas measles example.
