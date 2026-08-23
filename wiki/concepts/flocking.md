---
title: Flocking
type: concept
tags: [abm, complexity, netlogo]
date: 2026-08-01
---

# Flocking

Flocking is the collective coordinated movement of a group of individuals — birds,
fish, herds — produced by each individual following simple rules based only on its nearby
neighbours.

## How it works

Each individual (a [[boids|boid]], in the model) perceives only the neighbours within a
**vision** radius, and adjusts its heading and position according to a small set of local
rules:

- **Separation** — maintain at least a minimum distance from the nearest neighbour.
- **Alignment** — steer towards the heading of nearby neighbours.
- **Cohesion** — move towards the local group.

Bounded by a maximum turn rate and a speed, these rules produce clustering and a shared
direction of travel across the population, without any rule stating either outcome —
a textbook case of [[emergence]].

Parameters matter qualitatively, not just quantitatively. Raising vision or turn rate can
drive the flock into a rigid steady state; other combinations produce no coherent flock at
all. Locating those boundaries is exactly the [[tipping-point]] analysis the subject
returns to.

## Why it matters

Flocking is the reference example for the whole subject: minimal local rules, no global
coordination, no agent with global information, and a rich collective pattern as output.
It is also the concrete demonstration that an [[agent-based-model]] models the individual
in order to observe the population.

## From simulator to science

[[w04a-complex-systems-and-emergence]] reframes flocking as a route to testable science:
once a research question is posed (what individual-movement assumptions explain the
emergent characteristics of real flocks?), the model needs outputs comparable to real
flock/school data — the number of agents with flock-mates, the mean number of flock-mates
per agent, the mean nearest-neighbour distance, and the standard deviation of heading
across the population.

## Relationships

- [[boids]] — the specific model and its origin
- [[emergence]], [[complex-system]] — what flocking demonstrates
- [[netlogo]] — the Flocking model ships with NetLogo's model library
- [[agent-based-model]]
- [[craig-reynolds]] — the model's author

## Sources

- [[w01a-introduction]] — starling murmuration video plus a live run of the NetLogo
  Flocking model, with parameters varied in class.
- [[w04a-complex-systems-and-emergence]] — formalises the boids sensing model and
  separation/cohesion/alignment rules, and frames flocking outputs as testable model
  predictions.
