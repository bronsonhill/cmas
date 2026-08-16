---
title: Reproduction Number
type: concept
tags: [epidemiology, sir-model, threshold, assignment-1]
date: 2026-08-16
---

# Reproduction Number

The reproduction number $R$ is the average number of secondary cases infected by a typical
primary case. The basic reproduction number $R_0$ is that quantity measured in a totally
susceptible population, and it acts as a threshold: an outbreak with $R < 1$ dies out, while
one with $R > 1$ may take off.

## How it works

Think of an outbreak as generations of infection. Generation zero is the first case,
generation one is everyone it infects, and so on. $R$ is the average branching factor of
that tree. If each case produces fewer than one further case on average, the tree shrinks
generation by generation and terminates. If it produces more than one, the tree grows, and
growth compounds ([[exponential-growth]]).

$R$ is a compound of transmission and duration. In the [[sir-model]] a case transmits at
rate $\beta$ for an average duration $1/\gamma$, so the expected number of onward
infections is $\beta/\gamma$. Two diseases can therefore share an $R_0$ while behaving
completely differently: the Week 3 lecture contrasted a chickenpox-like illness ($R_0 = 8$,
seven days infectious) with a mumps-like one ($R_0 = 8$, fourteen days infectious). Both
eventually infect a similar fraction of the population, but the mumps-like profile peaks
around day 18 rather than day 9 and declines much more slowly, which changes what a health
system has to prepare for.

The distinction between $R_0$ and $R$ matters as soon as anyone has immunity. $R_0$ assumes
every contact is with a susceptible person. Once a fraction of the population is immune —
through recovery or vaccination — the effective reproduction number falls proportionally,
which is the mechanism behind the [[herd-immunity-threshold]].

$R$ is not directly observable. Measuring it would require knowing how many people each
case actually contacted and which of those contacts transmitted, which is why published
values for the same disease differ between sources and get revised as data accumulates.

## Formula

For the SIR model,

$$R_0 = \frac{\beta}{\gamma}$$

where $\beta$ is the effective contact rate — average contacts per person per unit time
multiplied by the per-contact transmission probability $q$ — and $\gamma$ is the recovery
rate. Since $D = 1/\gamma$ is the average infectious period, this is equivalently
$R_0 = \beta D$.

The threshold condition is

$$R < 1 \implies \text{outbreak dies out}, \qquad R > 1 \implies \text{outbreak may take off}$$

Note the asymmetry. Below one, extinction is essentially assured. Above one, an outbreak is
only *possible*, because early transmission is stochastic and a chain can fail by chance
before it establishes ([[stochastic-fadeout]]).

## Why it matters

$R$ is the quantity that turns an epidemic model into a decision tool. It gives a single
number that says whether a disease can sustain itself, a target for interventions (drive
$R$ below one), and — through $v \ge 1 - 1/R_0$ — a vaccination coverage requirement.

It is also the subject's clearest example of a [[tipping-point]]: the behaviour of the
system changes qualitatively either side of $R = 1$ rather than degrading smoothly. The
segregation model's failure to converge above a roughly 70% similarity threshold is the same
phenomenon in a different system.

Its relationship to the final attack rate saturates rather than scaling. The fraction
eventually infected rises steeply between $R_0 = 1$ and $R_0 = 2$ and then flattens; above
roughly $R_0 = 4$, essentially the whole population is infected. Raising $R_0$ further
changes how fast and how sharply an outbreak arrives, not how many people it reaches.

Values from the lecture chart, for calibration: influenza roughly 1–2, SARS 2–4, COVID-19
ancestral strain 2.5–3 rising to 5–8 for delta, polio 5–8, chickenpox 10–12, measles 12–18.

## Relationships

- [[sir-model]] — where $R_0 = \beta/\gamma$ comes from
- [[herd-immunity-threshold]] — the vaccination coverage $R_0$ implies
- [[stochastic-fadeout]] — why $R_0 > 1$ does not guarantee an outbreak
- [[tipping-point]] — $R = 1$ as a critical point
- [[exponential-growth]] — the regime above the threshold
- [[epidemic-intervention]] — measured by whether it drives $R$ below one
- [[deterministic-model]] — the formulation from which $R_0$ is derived analytically
- [[contact-rate]] — the behavioural component of $\beta$

## Sources

- [[w03b-reproduction-number]] — defines $R$ and $R_0$, gives $R_0 = \beta/\gamma$, the
  threshold behaviour, the generation diagrams, the non-observability argument, the four
  worked disease profiles, and the attack-rate curve.
- [[w03a-analysing-models]] — lists explaining the significance of the reproduction number
  as a weekly objective, and supplies the stochastic runs at $R_0 = 6.25$.
