---
title: Agent Neighbourhood
type: concept
tags: [abm, agent-behaviour, sensing, networks]
date: 2026-08-30
---

# Agent Neighbourhood

An agent's neighbourhood is the set of entities it can sense and interact with. It is the
formal answer to "which other agents and which parts of the environment does this agent
have access to".

## How it works

Two constructions cover most models.

**Spatial.** The neighbourhood is defined by a radius, or by grid positions. On a NetLogo
patch grid a radius of 1 is the eight surrounding cells (a Moore neighbourhood — see
[[cellular-automaton]]); radius 2 adds the next ring, giving 24; radius 8 gives 288. The
count grows as $(2r+1)^2 - 1$, so widening the radius escalates an agent's option set
fast. In a continuous space with headings, the neighbourhood can also be angular — the
boids in [[flocking]] see within a bounded field of view, not a full circle.

**Network.** The agent communicates with a nominated set of others who need not be
spatially close. A real-estate agent who calls you about an off-market listing is a
network neighbour; the neighbours you chat to about the street are a spatial one. Networks
are what let information reach an agent that no amount of local sensing would deliver.

The two can coexist. The [[business-investment-model]] has a sensing radius for evaluating
opportunities and an optional communication network layered on top.

## Why it matters

The neighbourhood is what makes agents *local*, and locality is the defining structural
feature of a [[complex-system]] — parts act on partial information about their
surroundings, and global behaviour follows from that. Neighbourhood size is usually a
model parameter, and usually a consequential one: the Week 5b radius sweep changed the
model's outcome non-monotonically, improving mean wealth up to radius 5 and degrading it
at 8. See [[imperfect-information]].

## Relationships

- [[agent-sensing]] — the neighbourhood bounds what can be sensed
- [[agent-interaction]] — and who can be interacted with
- [[imperfect-information]] — a bounded neighbourhood is one form of imperfection
- [[cellular-automaton]] — Von Neumann and Moore neighbourhoods, the discrete case
- [[decentralisation]] — bounded knowledge as a property of complex systems

## Sources

- [[w05a-sensing]] — radius vs network neighbourhoods, with the house-hunting example
- [[w05b-adaptation-and-objectives]] — the radius sweep and the network experiment
