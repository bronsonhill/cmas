---
title: Collectives
type: concept
tags: [abm, agent-behaviour, odd]
date: 2026-08-30
---

# Collectives

Collectives, as an ODD design concept, are aggregations of agents that themselves affect
the state or behaviour of their members — groups, households, firms, flocks treated as
entities rather than as a by-product of counting.

## How it works

The test is whether the group has any causal standing in the model. A flock in a
[[flocking]] model is *not* a collective in this sense: it is an
[[emergence|emergent]] pattern an observer names, and no boid holds a reference to it.
A household in a demographic ABM usually *is*: agents belong to it, it holds a shared
budget, and its state feeds back into individual decisions.

Two implementations recur. The collective can be an entity in its own right, with its own
state variables and its own place in the [[scheduling|schedule]]. Or it can exist only as
membership attributes on agents, with group-level quantities computed on demand.

Models often declare collectives *not used*, and should say so rather than staying silent.
The [[business-investment-model]] does: its agents compete but never form groups.

## Why it matters

Collectives are where an ABM can represent structure between the individual and the
system — the level at which a lot of social science actually operates. Kennedy's material
on [[social-influence]] is the behavioural content: group influence can converge members
on the group mean, on a compromise, or on a dominant member's position, and it can fail to
converge at all.

## Relationships

- [[agent-interaction]] — the interactions from which collectives are built
- [[social-influence]] — how membership changes a member's behaviour
- [[emergence]] — an emergent pattern is not automatically a collective
- [[odd-protocol]]

## Sources

- [[w05a-sensing]] — collectives named among the design concepts
- [[w05b-adaptation-and-objectives]] — declared unused in the investment model
- [[kennedy-2012-modelling-human-behaviour]] — group influence and its outcomes
