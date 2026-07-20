---
title: NetLogo User Manual
type: source
tags: [netlogo, abm, tooling]
date: 2026-07-20
link: https://docs.netlogo.org/
---

# NetLogo User Manual

The official documentation for [[netlogo]], the agent-based modelling environment
used throughout CMAS.

## Summary

The manual is in three parts. The **tutorials** walk through running a model from
the Models Library, changing its parameters, and then writing one from scratch —
enough to get a working simulation without reading any reference material first.
The **interface guide** covers the building blocks of a model's front end (sliders,
switches, plots, the view) and how they bind to variables in the code. The
**dictionary** is the per-primitive reference: every built-in command and reporter,
grouped by what it operates on (turtles, patches, links, the observer).

Two ideas from the manual carry the most weight for CMAS. First, NetLogo's world
is a grid of *patches* with *turtles* moving over it — which makes it a natural
host for both [[cellular-automaton]] models (patches only) and richer
[[agent-based-model|agent-based models]] (turtles with state and behaviour).
Second, `ask` is the core control structure: agents run their code
concurrently-in-appearance but sequentially in fact, in a random order per tick.
That ordering detail is a common source of surprise when a model's results don't
match the intuition behind its rules.

The bundled Models Library is worth browsing early — most classic simulations
(Game of Life, Schelling segregation, predator–prey) ship as readable, runnable
models.

## Relationships

- [[netlogo]] — the tool this manual documents
- [[cellular-automaton]] — implemented in NetLogo with patches
- [[agent-based-model]] — implemented with turtles
