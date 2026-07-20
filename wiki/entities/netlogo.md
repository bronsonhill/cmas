---
title: NetLogo
type: entity
tags: [netlogo, tooling, abm]
date: 2026-07-20
---

# NetLogo

A free, open-source modelling environment for building and running agent-based
simulations, and the primary tool used in CMAS.

## Key facts

- Created by Uri Wilensky in 1999 at Northwestern University's Center for
  Connected Learning; still actively maintained there.
- Descends from the Logo language — the "turtle" is inherited directly from it.
- Four agent types: **turtles** (mobile agents), **patches** (fixed grid cells),
  **links** (connections between turtles), and the **observer** (a single global
  controller).
- Ships with a large Models Library of runnable classic simulations across
  biology, social science, physics, and mathematics.
- Includes BehaviorSpace, a built-in tool for sweeping parameters across many
  runs — the practical way to get results out of a stochastic model.

## Relevance to CMAS

NetLogo makes the mapping from concept to code unusually direct: a
[[cellular-automaton]] is a rule over patches, an [[agent-based-model]] is a rule
over turtles, and both are expressed with the same `ask` primitive. That means
model-building effort goes into the rules themselves rather than simulation
plumbing.

The catch worth remembering: `ask` runs agents sequentially in a random order
each tick, not simultaneously. Writing a CA in NetLogo therefore needs care — the
synchronous update has to be built explicitly (compute next states for all
patches, then commit them), or the model silently becomes an asynchronous one
with different dynamics.

## Sources

- [[netlogo-users-manual]] — official documentation
