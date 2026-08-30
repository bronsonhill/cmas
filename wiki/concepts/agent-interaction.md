---
title: Agent Interaction
type: concept
tags: [abm, agent-behaviour, odd]
date: 2026-08-30
---

# Agent Interaction

Interaction, as an ODD design concept, is how agents affect one another. The first
question to answer is whether the interaction is **direct** or **indirect**.

## How it works

**Direct** interaction is one agent acting on another: a predator eating prey, an agent
transmitting infection, an agent passing information along a network link.

**Indirect** interaction is mediated by a shared resource or environment, with the agents
never touching. Competition is the archetype. In the
[[business-investment-model]] agents interact only indirectly: an opportunity holds at
most one investor, so occupying a patch denies it to everyone else. Nobody communicates,
but every agent's options depend on where the others went. Stigmergy — ants following
pheromone trails left in the environment — is the other standard case.

Whether interaction is direct or indirect interacts with [[scheduling]]. If several
agents can claim the same resource in one tick, the model has a race condition, and the
resolution is a modelling decision rather than an implementation detail: lock the
resource, randomise the update order, or update synchronously and arbitrate afterwards.
The business investment model randomises order, so wealthier agents get no first-mover
advantage — a deliberate choice to keep the wealth distribution from compounding an
artefact of the loop.

Adding a communication [[agent-neighbourhood|network]] turns indirect interaction into
direct information sharing. The Week 5b experiment did exactly that and found no
improvement in agent outcomes, because the underlying landscape was unstructured: shared
information about *how well* others were doing carried no signal about *where* to go.

## Relationships

- [[agent-neighbourhood]] — who can interact with whom
- [[collectives]] — interaction that persists into group structure
- [[scheduling]] — resolving simultaneous interactions
- [[agent-sensing]] — sensing another agent is itself an interaction
- [[odd-protocol]]

## Sources

- [[w05a-sensing]] — interaction as a design concept; the race-condition discussion in
  the predator-prey recap
- [[w05b-adaptation-and-objectives]] — indirect competition in the investment model and
  the network experiment
