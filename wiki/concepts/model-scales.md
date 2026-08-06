---
title: Model Scales
type: concept
tags: [methodology, model-design, odd]
date: 2026-08-06
---

# Model Scales

The scales of a model are its representations of time and space: how long the simulation
runs and in what increments, and whether and how the model represents physical location.
Together with entities and state variables they form section 2 of the [[odd-protocol]].

## How it works

**Temporal scale** splits into two choices:

- **Temporal extent** — how long the simulation runs. Mushrooms take a season to grow, so
  a model of mushroom availability runs over a year; a model of one forager's search runs
  over an afternoon. The extent follows from the process being represented.
- **Temporal resolution** — whether time is continuous or advances in discrete steps, and
  how large those steps are.

Resolution is not a free choice. It has to be consistent with how far an agent moves in one
step and with the size of the modelled space. Simulating a few hours of walking in
one-second steps means the agent covers almost no ground per step, which wastes computation
and misrepresents movement; minutes are the appropriate grain. A smaller map admits finer
steps, because the displacement per step is a larger fraction of the space.

**Spatial scale** also splits in two:

- Whether the model is **spatially explicit** at all. Foraging is inherently spatial — the
  agent is somewhere and moves towards somewhere else, and distance is what the behaviour
  is about. Other systems are not: traders in a stock market act from anywhere in the
  world, and information spreading through a social network depends on who is connected to
  whom, not on where anyone lives. Abstracting space away when it is irrelevant removes
  detail the model would otherwise have to specify and justify.
- Whether space is **continuous** or **discretised** into patches of a specified size — a
  room, a building, a street block, a square kilometre.

## Why it matters

Scale choices are among the easiest to make carelessly and among the most expensive to get
wrong, because they constrain what the model can express. A model discretised into
one-kilometre patches cannot represent behaviour that depends on metres. A model whose
temporal extent stops at one week cannot answer a question about long-run adaptation — a
point the zombie-apocalypse exercise made directly, where the purpose (design settlements
that survive, versus plan an escape in the first week) determined the extent
([[zombie-apocalypse-model-design]]).

## Relationships

- [[odd-protocol]] — scales are part of section 2
- [[model-structure]] — scales are one of its five elements
- [[abstraction]] — deciding a model need not be spatial is an abstraction judgement
- [[research-question]] — the purpose determines the appropriate extent

## Sources

- [[w02a-describing-models]] — defines temporal extent and resolution, spatial explicitness
  and discretisation; the one-second-steps-for-an-afternoon-walk counterexample and the
  stock-market and social-network examples of non-spatial models.
