---
title: Business Investment Model
type: entity
entity_type: model
tags: [netlogo, abm, agent-behaviour, comp90083]
date: 2026-08-30
---

# Business Investment Model

The NetLogo model used across Week 5 as the running example for
[[agent-sensing|sensing]], [[adaptive-behaviour|adaptation]] and
[[objective-function|objectives]]. Investor agents choose which business opportunity to
back, trading annual profit against risk of failure.

## Key facts

**Purpose.** To explore the effect of sensing on the emergent behaviour of a model whose
agents decide on acquired information.

**Entities.** Investor agents, characterised by wealth $W$. Business opportunities,
characterised by annual profit $P$ and annual probability of failure $F$. Opportunities
are NetLogo patches — a spatial representation used for convenience, with no claim that
adjacent opportunities are related in any real sense.

**Scales.** One tick is one year; runs last 25 years.

**Schedule.** Each tick, in order:

1. *Repositioning* — an agent evaluates its own patch and the unoccupied patches within
   its sensing radius, and moves to the best. At most one agent per opportunity.
2. *Accounting* — with probability $F$ the business fails and $W$ resets to zero;
   otherwise $W$ increases by $P$.

**Objective.** Maximise utility over a horizon $T$:

$$U = (W + TP)(1 - F)^{T}$$

**Initialisation.** Profit drawn uniformly from $[1000, 10000]$, risk uniformly from
$[0.01, 0.1]$, independently — no correlation between profit and risk, and none between
adjacent patches. 100 agents placed at random, one per patch, with zero wealth.

**Input data.** None. **Learning and collectives.** Not used.

## Assumptions worth naming

- $P$ and $F$ are static, so [[agent-prediction|prediction]] is exact. Real returns and
  failure risks move.
- Sensing is error-free. Real investors read opportunities and rivals through bias.
- Profit and risk are uncorrelated, which contradicts the usual finance intuition that
  higher returns carry higher risk, and removes the portfolio-construction problem.
- The landscape is uniform random, so there is no gradient to climb and local optima are
  everywhere.
- Failure is catastrophic and total — wealth resets to zero, no partial loss.
- [[scheduling|Update order]] is randomised, so wealthier agents get no first-mover
  advantage.

## Results from the lecture experiments

- Mean profit rises steeply on the first tick and then flattens: on a uniform random
  landscape, roughly half the neighbouring patches beat the current one, so the first move
  almost always improves things and later moves have less headroom.
- Mean risk declines and then plateaus. The $(1-F)^T$ term weights survival more heavily
  as the horizon shortens, so agents become risk-averse late in the run, settle on a local
  optimum and stop moving.
- Sensing radius 1 → 2 → 5 improves final mean wealth; radius 8 degrades it. See
  [[imperfect-information]].
- A fully connected communication network did not beat the radius-1 baseline: on an
  unstructured landscape, knowing how well others are doing carries no directional signal.

## Relevance

The model is the subject's worked example of a full [[odd-protocol|ODD]] description of an
agent-behaviour model, and the vehicle for the Week 5 argument that more information does
not automatically produce better decisions.

## Sources

- [[w05a-sensing]] — ODD description and first demo
- [[w05b-adaptation-and-objectives]] — the sensing-radius and network experiments, and the
  proposed satisficing variant
