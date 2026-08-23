---
title: Chaos
type: concept
tags: [complexity, dynamical-systems, foundations]
date: 2026-08-23
---

# Chaos

Chaos is aperiodic, seemingly unpredictable long-term behaviour produced by a fully
deterministic nonlinear system, typically marked by extreme sensitivity to initial
conditions.

## How it works

Chaos requires no randomness at all. The logistic map $x_{n+1} = rx_n(1-x_n)$ is
deterministic — the same $x_n$ and $r$ always produce the same $x_{n+1}$ — yet as $r$
increases, its long-term behaviour undergoes a cascade of period-doubling bifurcations into
a regime where trajectories never settle into a repeating cycle. The three-body problem
gives the same story in continuous time: the two-body problem (a planet orbiting a star) is
exactly solvable and produces regular, closed orbits, but adding one more mutually
gravitating body — still simple Newtonian rules — removes any closed-form solution and
produces chaotic trajectories. Nonlinearity is the necessary ingredient in both cases;
linear systems cannot be chaotic.

## Why it matters

Chaos is one of the origins of the very idea of complexity: a chaotic system has no
available analytical solution, so understanding it requires simulation rather than direct
computation, and its output is sensitive enough to initial conditions that even a
simulated trajectory is only representative, not predictive, of any single real
realisation. This is part of why complex systems generally, and [[agent-based-model|ABMs]]
in particular, are studied by running many instances and summarising output rather than
solving for a single deterministic answer — the same reasoning behind treating
[[stochasticity]] with repeated runs in the [[sir-model]] context.

## Relationships

- [[complex-system]] — chaos as one route by which few simple rules produce complex
  behaviour
- [[cellular-automaton]] — Wolfram's Class 3 rules exhibit CA-native chaotic behaviour
- [[stochasticity]] — a distinct source of unpredictability (randomness rather than
  deterministic sensitivity)

## Sources

- [[w04a-complex-systems-and-emergence]] — the three-body problem and the logistic map's
  bifurcation diagram as worked examples of low-dimensional deterministic chaos.
- [[sayama-2015-modeling-and-analysis-of-complex-systems-ch1]] — names chaos as one of the
  historical origins of complexity, arising from nonlinear dynamics.
