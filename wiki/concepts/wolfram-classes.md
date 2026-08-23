---
title: Wolfram Classes
type: concept
tags: [complexity, cellular-automata]
date: 2026-08-23
---

# Wolfram Classes

The Wolfram classes are [[stephen-wolfram|Stephen Wolfram]]'s 1984 four-way classification
of the long-run behaviour of [[cellular-automaton|cellular automata]].

## How it works

- **Class 1** — evolves to a fixed homogeneous state; the system freezes into a single
  uniform configuration after a short transient.
- **Class 2** — evolves to a fixed inhomogeneous state; the system develops periodic, or
  limit-cycle, behaviour.
- **Class 3** — evolves to [[chaos|chaotic]] or aperiodic behaviour; the system continuously
  changes in unpredictable ways and, in some cases, shows sensitive dependence on initial
  conditions.
- **Class 4** — evolves to complex, localised structures; the system develops highly
  patterned but unstable behaviour, with complex interactions between local structures.
  Class 4 has drawn the most study for its computational properties, since it contains
  [[turing-completeness|Turing complete]] rules such as rule 110.

## Why it matters

Wolfram's classification gives a coarse but useful vocabulary for what "complex" means at
the level of a single, minimal rule table: not every rule produces interesting behaviour
(most fall into Class 1 or 2), and the qualitative jump from Class 2 to Class 3 mirrors the
jump from regular to chaotic dynamics seen elsewhere in nonlinear systems — Sayama's point
that even a system with no continuous state at all can traverse the same regular-to-chaotic
spectrum as continuous dynamical systems.

## Relationships

- [[cellular-automaton]] — the systems being classified
- [[chaos]] — Class 3 is CA-native chaos
- [[turing-completeness]] — concentrated in Class 4
- [[game-of-life]] — spans several classes depending on initial configuration

## Sources

- [[w04b-2d-cellular-automata]] — states and illustrates the four classes with rule
  examples (rule 160, 108, 126, 110).
