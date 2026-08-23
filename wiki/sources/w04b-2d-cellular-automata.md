---
title: "Week 4b: 2D Cellular Automata"
type: source
source_type: lecture
link: https://canvas.lms.unimelb.edu.au/courses/239814
tags: [comp90083, week-04, lecture, cellular-automata, game-of-life, lotka-volterra]
date: 2026-08-23
---

# Week 4b: 2D Cellular Automata

## Overview

The second Week 4 lecture, delivered by [[andres-munoz]], follows directly from Week 4a's
survey of complex systems and works through [[cellular-automaton|cellular automata]] as a
concrete, minimal modelling framework — deliberately simpler than an
[[agent-based-model|ABM]], but expressive enough to demonstrate emergence, self-
organisation, and even universal computation from purely local rules.

The lecture opens with history: [[john-von-neumann]] and [[stanislaw-ulam]] developed CA
at Los Alamos in the 1940s, von Neumann pursuing self-replicating machines and Ulam
studying crystal growth. A CA is defined by extending the general notion of an
**automaton** — a theoretical machine updating its internal state from external inputs and
its own previous state — into an array of automata (cells) whose "external inputs" are the
current states of nearby cells. Formally: entities are cells, each holding a single state
variable from a finite set (e.g. off/on); time is discrete; space is discrete, typically a
1D or 2D grid (though higher dimensions and networks are possible); and update rules are
local and, in the classical formulation, deterministic and synchronous.

**1D elementary CA** are used to make the rule mechanism concrete: a ring of two-state
cells, each updated from a neighbourhood of itself plus its two adjacent cells ($K=3$),
gives $2^{2^3} = 256$ possible rule tables, each of which can be numbered by reading its
eight output bits as a binary integer (worked example: rule 90). Many of the 256 are
trivially equivalent under mirroring or complementing 0/1, leaving 88 essentially distinct
rules — yet even this tiny rule space produces a striking range of behaviour. Rule 30
generates an irregular, seemingly patternless triangle strikingly similar to the pigment
pattern on the shell of the cone snail *Conus textile*; [[stephen-wolfram|Wolfram]]'s 1984
classification sorts CA behaviour into four classes — Class 1 (freezes to a fixed
homogeneous state), Class 2 (settles into periodic/limit-cycle behaviour), Class 3
(chaotic, aperiodic, sensitive to initial conditions), and Class 4 (complex, unstable,
interacting local structures) — and rule 110, a Class 4 rule, is Turing complete: capable
of universal computation from nothing but a 1D binary array and a lookup table. CA
applications named beyond seashells include tumour growth, bushfire spread, and urban
growth models.

**2D CA** redefine neighbourhood and update rule for a grid: the Von Neumann neighbourhood
(the four orthogonal neighbours) and the Moore neighbourhood (all eight surrounding cells)
are the two standard choices. The worked example is [[conways-game-of-life|Conway's Game
of Life]] (1970, inspired by von Neumann's self-replication work): each cell is alive or
dead; a live cell with fewer than two live neighbours dies (loneliness), with more than
three dies (overcrowding), with two or three survives; a dead cell with exactly three live
neighbours becomes alive (reproduction). All cells update simultaneously each generation.
Despite this handful of rules, Life produces stable still-lifes, periodic oscillators, and
mobile patterns (gliders); Gosper's glider gun and constructions built from Life patterns
implement information-carrying signals and logic gates, making Life — like rule 110 —
Turing complete. The lecture is explicit about the model's limiting assumptions:
synchronous and deterministic updates are strong assumptions that real systems rarely
satisfy, which bounds how directly CA can stand in as models of real-world systems.

The lecture closes with a worked motivating case for building a CA model of a real system:
90 years of hare and lynx population records from the Hudson Bay Company (1845–1935) show
sustained out-of-phase oscillation between predator and prey. The classical continuous-time
account is the **[[lotka-volterra-model|Lotka-Volterra model]]**, independently formulated
by [[alfred-lotka]] and [[vito-volterra]] in 1925–26 (both building on Verhulst's logistic
equation), given as coupled ODEs $\frac{dR}{dt} = \alpha R - \beta RF$ and
$\frac{dF}{dt} = \delta RF - \gamma F$ for rabbit population $R$ and fox population $F$,
under the assumptions that rabbits have unlimited food and grow exponentially absent foxes,
foxes eat only rabbits and decline exponentially absent rabbits, and the environment is
static. Recast as a discrete stochastic process — at each step a rabbit is born with
probability $\alpha$, a fox dies with probability $\gamma$, and each fox meets a rabbit
with a probability proportional to rabbit count, eating it with probability $\beta$ and
then breeding with probability $\delta$ — the same dynamics become expressible as a CA-style
local-interaction model, setting up predator-prey CA as a lab/assignment direction.

## Key concepts

- [[cellular-automaton]]
- [[game-of-life]]
- [[wolfram-classes]]
- [[turing-completeness]]
- [[lotka-volterra-model]]

## Key entities

- [[andres-munoz]]
- [[john-von-neumann]]
- [[stanislaw-ulam]]
- [[conways-game-of-life]]
- [[stephen-wolfram]]
- [[alfred-lotka]]
- [[vito-volterra]]

## Topics covered (revision checklist)

- Origins of cellular automata: von Neumann and Ulam at Los Alamos, 1940s
- Automaton vs cellular automaton (array of automata with local inputs)
- CA formal structure: entities/state variables (finite discrete states), discrete time,
  discrete space (1D/2D/higher-dimensional/network), local deterministic update rules
- Elementary 1D CA: neighbourhood ($K=3$), lookup tables, rule numbering (binary encoding),
  boundary handling via ring topology
- Rule 30 (Class 3, chaotic) and its resemblance to *Conus textile* shell pigmentation
- Counting distinct elementary rules: 256 total, 88 up to mirror/complement symmetry
- Wolfram's four behaviour classes (fixed homogeneous / periodic / chaotic / complex-
  localised)
- Rule 110 and Turing completeness of 1D CA
- CA applications: seashells, tumours, bushfires, cities
- 2D CA neighbourhoods: Von Neumann vs Moore
- Conway's Game of Life: rules (loneliness, overcrowding, survival, reproduction),
  synchronous update
- Life pattern classes: stable (still-life), periodic (oscillator), mobile (glider)
- Gosper's glider gun and Life's Turing completeness via signal/logic constructions
- Limiting assumptions of CA as models of real systems: synchronous, deterministic updates
- Hudson Bay hare/lynx population data (1845–1935) as motivation for predator-prey
  modelling
- The Lotka-Volterra ODE system and its assumptions
- A discrete, probabilistic (CA-compatible) reformulation of Lotka-Volterra dynamics

## Notable claims / results

- There are $2^{2^3} = 256$ possible elementary 1D CA rules (neighbourhood size $K=3$,
  2 states), of which 88 are essentially distinct once mirror and complement symmetries are
  factored out.
- Rule 110 is Turing complete: a 1D binary CA with a fixed local rule can perform universal
  computation.
- Conway's Game of Life, built from four simple neighbour-count rules, is also Turing
  complete — glider guns and related constructions implement signals and logic operations.
- The Lotka-Volterra model was independently derived by Alfred Lotka and Vito Volterra in
  1925–26, both drawing on Verhulst's logistic equation.
- Hudson Bay Company trapping records (1845–1935) show a ~90-year record of sustained,
  out-of-phase hare/lynx population cycles, the canonical empirical motivation for
  predator-prey models.

## Connections

Extends [[w04a-complex-systems-and-emergence]]'s survey of complex systems with a concrete,
minimal formalism. The predator-prey framing links back to the [[sir-model]]/
[[compartmental-model]] machinery from [[w02b-modelling-disease-spread]] — both are
population-level ODE systems that a discrete, agent- or cell-based model can reformulate
stochastically.

A layered digest of this lecture is available at
[[materials/w04b-2d-cellular-automata-digest]].
