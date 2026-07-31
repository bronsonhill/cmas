---
title: NASA Black Hole Collision Simulation
type: entity
entity_type: model
tags: [case-study, simulation, physics]
date: 2026-08-01
---

# NASA Black Hole Collision Simulation

A NASA-produced simulation and visualisation of two black holes orbiting and colliding,
used in lecture as a worked example of identifying what a model must contain and what its
purpose actually is.

## Key facts

- Elements the class identified as necessary: **gravity** (the primary mechanism), **mass**,
  **initial conditions**, and a genuinely **three-dimensional** spatial representation —
  the interaction is spatial, so a 2D model would not make sense.
- Elements judged derivable rather than fundamental: movement and inter-body distance, both
  consequences of gravity rather than separate inputs.
- The system cannot be observed directly, and cannot be experimented on. It is only
  detectable through emitted radiation.
- **The model's purpose is instrumental.** Existing theory predicts the radiation such a
  collision would emit; simulating it indicates what to expect, which in turn tells
  physicists what **sensors** to build and how to calibrate instruments — where to point a
  radio telescope and which X-rays to look for.
- The result need not be perfectly accurate to be useful: it provides a starting point for
  where to concentrate detection effort.

## Relevance to CMAS

The clearest example in Week 1 that a model's purpose need not be explanation or
prediction — here it is **instrument design**. It also demonstrates the reasoning of
[[abstraction]]: separating what must be modelled (gravity, mass, initial state, 3D space)
from what falls out of the mechanism (motion, distance). Compare [[agent-sensing]], which
is the same design question at agent scale.

## Sources

- [[w01b-modelling-cycle]] — shown as a video, with the class working out required elements
  and the purpose interactively.
