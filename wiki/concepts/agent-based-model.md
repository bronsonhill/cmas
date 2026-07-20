---
title: Agent-Based Model
type: concept
tags: [abm, emergence, simulation]
date: 2026-07-20
---

# Agent-Based Model

An agent-based model (ABM) simulates a system as a population of autonomous
agents, each following its own rules, so that system-level behaviour emerges from
their interactions rather than being specified directly.

## How it works

An ABM has three ingredients:

- **Agents** — each with internal state (position, wealth, infection status, …)
  and a behaviour rule mapping what it perceives to what it does.
- **Environment** — the space agents occupy and modify; often a grid, sometimes a
  network or continuous space.
- **Schedule** — how time advances. Each *tick*, some or all agents act; the
  order they act in is part of the model, not an implementation detail.

The defining move is that the modeller specifies only local behaviour. Aggregate
quantities — segregation, epidemic curves, price series — are *measured* from
runs, never written into the rules. Because agents are heterogeneous and
interactions are typically stochastic, a single run tells you little: results are
read from distributions across many runs with different random seeds.

## Formula

Agent $a$ at time $t$ has state $x_a^t$ and perceives a neighbourhood
$N(a, t)$ of other agents and the environment $E^t$. Its behaviour rule $g$
gives:

$$
x_a^{t+1} = g\left( x_a^t, \; \{ x_b^t : b \in N(a, t) \}, \; E^t \right)
$$

The macro-observable is a function of the whole population, e.g. a mean over
$n$ agents:

$$
Y^t = \frac{1}{n} \sum_{a=1}^{n} \phi(x_a^t)
$$

Compare this with the [[cellular-automaton]] update: the rule has the same shape,
but $N(a, t)$ depends on $t$ (agents move, so neighbours change), $g$ may differ
between agents, and it may be stochastic.

## Why it matters

ABMs let you model systems where the interesting behaviour comes from
*interaction* — traffic jams forming with no accident, crowds evacuating a
building, disease spread through a contact network. Equation-based approaches
(e.g. compartmental ODE models) describe a population in aggregate and assume
everyone in a compartment is interchangeable; an ABM keeps individuals distinct,
so heterogeneity and network structure can change the outcome.

The cost is that ABMs are expensive to run, have many parameters, and are hard to
validate — you can nearly always fit a plausible-looking curve, which is why
sensitivity analysis and calibration against real data matter so much.

## Relationships

- [[cellular-automaton]] — the special case of immobile, identical, uniformly
  ruled agents
- [[netlogo]] — the environment used to build ABMs in CMAS

## Sources

- [[netlogo-users-manual]] — turtle-based modelling, the `ask` primitive, and
  scheduling
