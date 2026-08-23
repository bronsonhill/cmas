---
title: "Week 4a: Complex Systems & Emergence"
type: source
source_type: lecture
link: https://canvas.lms.unimelb.edu.au/courses/239814
tags: [comp90083, week-04, lecture, complex-systems, emergence, flocking, boids]
date: 2026-08-23
---

# Week 4a: Complex Systems & Emergence

## Overview

The first Week 4 lecture, delivered by [[andres-munoz]], opens the second block of the
subject — "Designing agent-based models" (Weeks 4–9) — and starts by naming the property
that made everything in Weeks 1–3 worth simulating rather than solving on paper:
**complexity**. Where Weeks 1–3 treated the modelling cycle, ODD, and analysis as generic
tools, this lecture asks what kind of system actually needs an [[agent-based-model|ABM]]
in the first place.

The lecture builds up to a working definition of [[complex-system|complex system]] by
walking through a 2×2 space of "how many parts, how simple the rules, how predictable the
outcome". A single planet orbiting a star is few parts, simple rules, simple (regular,
analytically solvable) behaviour; adding one more body — the three-body problem — keeps the
rules just as simple but the trajectories become chaotic, with no closed-form solution.
The same jump appears with a single equation: the [[logistic-map|logistic map]]
$x_{n+1} = rx_n(1-x_n)$ produces a bifurcation cascade into deterministic chaos as $r$
increases, despite having no stochastic element at all. Many simple parts obeying simple rules can go either way —
crystals are highly ordered, gases are highly disordered but statistically homogeneous —
while starling murmurations, cellular automata, and complex networks sit in between as the
subject's archetypal complex systems: many parts, simple rules, genuinely complex,
[[emergence|emergent]] behaviour. Many parts with complicated, heterogeneous rules
(biological development, termite colonies, markets) still produce complex but reproducible
and robust behaviour; many parts under classical-engineering-style design, or under a
single central authority (an orchestra, the military), instead produce deterministic or
centralised behaviour by construction — the contrast is the point, since it is exactly the
*absence* of central design or central control that makes complex systems interesting to
model computationally rather than engineer directly.

From that survey the lecture distils Sayama's working definition: complex systems are made
of several components that interact, typically nonlinearly; they may arise through
[[self-organisation]]; they sit between fully regular and fully random; and they exhibit
emergent behaviour at the macroscopic scale. Two further properties are drawn out.
**Decentralisation** has three components — distribution (each part carries only a subset
of global information), bounded knowledge (no part sees the whole), and parallelism (parts
act simultaneously) — illustrated with market prices: no central computer sets the price,
yet the aggregate signal of buying and selling produces price movements, including crashes
driven by panic. **Feedback** is positive (amplifies fluctuations, the same mechanism
behind exponential growth) or negative (dampens fluctuations, the mechanism behind a system
settling into a steady-state plateau) — tying back to the exponential and equilibrium
dynamics of the [[sir-model]] from Week 2.

The second half returns to [[flocking]] as the lecture's running example and introduces the
[[boids]] model formally: [[craig-reynolds|Craig Reynolds]]'s 1986 agent ("boid") senses
other boids within an angular, distance-bounded field of view and follows three local
rules — separation (avoid crowding), cohesion (steer toward the average position of nearby
boids), and alignment (steer toward the average heading of nearby boids). The lecture
reframes the model as a route "from simulator to science": once a scientific question is
posed ("what assumptions about individual movement explain the emergent characteristics of
real flocks?"), the model needs outputs comparable to real data — the number of agents with
flock-mates, mean flock-mates per agent, mean nearest-neighbour distance, and the standard
deviation of heading across the population — turning a demonstration into a testable model.

## Key concepts

- [[complex-system]]
- [[emergence]]
- [[self-organisation]]
- [[decentralisation]]
- [[feedback]]
- [[chaos]]
- [[logistic-map]]
- [[flocking]]

## Key entities

- [[andres-munoz]]
- [[boids]]
- [[craig-reynolds]]

## Topics covered (revision checklist)

- Subject structure: introduction to ABMs (Weeks 1–3), designing ABMs (Weeks 4–9),
  applying ABMs (Weeks 10–12)
- Definitions of "system" across disciplines (physiology, biology, computing, astronomy)
- The two-body problem (solvable, regular) vs the three-body problem (no closed-form
  solution, chaotic trajectories)
- Low-dimensional deterministic chaos via the logistic map and its bifurcation diagram
- Crystals and gases as ordered/disordered limits of "many parts, simple rules"
- Flocking, cellular automata, pattern formation, and complex networks as archetypal
  complex systems
- Biological development (*C. elegans*), termite mound structure, evolution, societies and
  markets as "many parts, complicated rules, complex but reproducible behaviour"
- Classical engineering systems and centrally-led groups (orchestra, military) as
  counter-examples: many parts, complicated rules, but deterministic/centralised outcomes
- Sayama's working definition of a complex system
- Emergence and self-organisation as properties of complex systems
- Decentralisation: distribution, bounded knowledge, parallelism
- Positive vs negative feedback, and their link to exponential growth and steady states
- The boids model: sensing (angle + distance), and the separation/cohesion/alignment rules
- Framing a model as science: defining comparable outputs (flock-mate counts, nearest-
  neighbour distance, heading variance) to test hypotheses about real flocks

## Notable claims / results

- The three-body problem has no exact analytical solution and produces chaotic
  trajectories, despite having only one more component than the exactly-solvable two-body
  problem.
- The logistic map $x_{n+1} = rx_n(1-x_n)$ demonstrates that a single deterministic
  equation with no randomness can produce chaotic behaviour as a parameter is varied.
- A working definition of complex systems (after Hiroki Sayama): systems of interacting,
  typically nonlinear components that may self-organise, sit between full regularity and
  full randomness, and exhibit macroscopic emergent behaviour.
- Positive feedback amplifies fluctuations (e.g. exponential growth); negative feedback
  dampens them (e.g. settling to a steady-state plateau).
- Reynolds's boids follow three local rules — separation, cohesion, alignment — sensed
  within a bounded angular/distance neighbourhood, with no rule specifying flock-level
  outcomes directly.

## Connections

Builds directly on [[flocking]] and [[emergence]] as introduced in [[w01a-introduction]],
and on the feedback dynamics implicit in the [[sir-model]]'s exponential growth phase
([[w02b-modelling-disease-spread]]). Sets up [[w04b-2d-cellular-automata]], which treats
cellular automata as the lecture's other archetypal complex system.

A layered digest of this lecture is available at
[[materials/w04a-complex-systems-and-emergence-digest]].
