---
title: Initial Conditions
type: concept
tags: [methodology, model-design, odd, reproducibility]
date: 2026-08-06
---

# Initial Conditions

The initial conditions of a model are its complete state at $t = 0$: where the agents are,
what values their state variables hold, and what state the environment is in. Specifying
them is the Initialisation section of the [[odd-protocol]].

## How it works

Initialisation answers three questions. Where are the agents located — scattered uniformly,
clustered, placed by data? What are the values of their state variables — carrying
capacity, disease state, wealth? What values do environmental variables take — how many
mushrooms exist in the forest, how much moisture is in each patch?

Models divide on how much this matters. In some, long-run behaviour converges to the same
attractor regardless of where it starts. In others — and agent-based models are dynamical
systems, so this is common — the trajectory depends on the starting state, and two runs
from different initial conditions never become comparable.

The choice of initial condition is itself a modelling assumption that needs defending. The
subject's scaffolding SIR model distributes agents uniformly across an unstructured space
because a uniform distribution is the least informative one and therefore introduces no
positional bias, making it a [[null-model]] baseline. It starts with exactly one infectious
agent because real outbreaks begin with a patient zero rather than a cluster. Changing
either is not a neutral act — it adds an assumption that then has to be justified and
explained.

## Why it matters

Initial conditions are a precondition for [[reproducibility]]. A described model that omits
its starting state cannot be re-run by anyone else, because a stochastic dynamical system
started from a different configuration produces different output even when every rule and
parameter matches. This is why ODD gives initialisation its own section rather than folding
it into the process description.

## Relationships

- [[odd-protocol]] — the Initialisation section
- [[reproducibility]] — the main reason to record them
- [[null-model]] — the justification for the uniform, single-patient-zero default
- [[stochasticity]] — why identical initial conditions still give varying runs
- [[sir-model]] — the worked example

## Sources

- [[w02a-describing-models]] — defines initialisation, and notes that some models' long-term
  behaviour depends on initial conditions while others converge regardless.
- [[w02b-modelling-disease-spread]] — the uniform distribution and patient-zero assumptions
  in the supplied SIR scaffolding model.
