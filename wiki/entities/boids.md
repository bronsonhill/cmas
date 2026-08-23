---
title: Boids
type: entity
entity_type: model
tags: [abm, complexity, flocking]
date: 2026-08-01
---

# Boids

Boids is the classic agent-based flocking model, in which each simulated bird — a "boid" —
follows a handful of local rules and realistic flock behaviour emerges from the population.

## Key facts

- Developed around 1987, during the period of cheap high-powered computing that made
  early [[agent-based-model|ABM]] work practical.
- Each boid is rendered as a triangle carrying a heading; the rules depend only on nearby
  neighbours.
- Governing parameters demonstrated in class: minimum separation from the nearest
  neighbour, vision radius, maximum turn rate, and speed.
- Observed emergent outcomes: boids clump into clusters and converge on a shared direction
  of travel, neither of which is specified as a rule (see [[emergence]]).
- Parameter changes produce qualitatively different regimes, including frozen steady
  states — an accessible example of a [[tipping-point]].
- Available as the Flocking model in the [[netlogo]] model library.

## Relevance to CMAS

Boids is the subject's reference demonstration that modelling the individual is sufficient
to produce collective structure — the founding intuition for agent-based modelling.

## Sources

- [[w01a-introduction]] — run live in the lecture, with parameters varied and student
  observations of clustering and common heading drawn out.
- [[w04a-complex-systems-and-emergence]] — formalises the model: attributed to
  [[craig-reynolds]] (1986/87), with sensing defined by angle and distance, and the three
  rules — separation, cohesion, alignment — named explicitly.
