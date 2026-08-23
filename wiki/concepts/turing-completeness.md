---
title: Turing Completeness
type: concept
tags: [complexity, cellular-automata, computation]
date: 2026-08-23
---

# Turing Completeness

A system is Turing complete if it is capable of universal computation: given the right
initial configuration, it can simulate any computation a Turing machine can perform.

## How it works

Turing completeness in a [[cellular-automaton]] is established by showing that
information-carrying signals and logical operations on those signals (AND, OR, NOT gates,
or their equivalent) can be constructed from the CA's own local rule. Elementary 1D rule
110 is Turing complete despite operating on nothing more than a binary array and a
$K=3$ lookup table. [[game-of-life|Conway's Game of Life]] is Turing complete via
constructions such as Gosper's glider gun, which emits a periodic stream of gliders that
can be used as information-carrying signals; more elaborate Life patterns implement full
logic gates and, ultimately, a working universal Turing machine built from Life cells.

## Why it matters

Turing completeness is the strongest possible statement about a simple rule's power: it is
not merely that rule 110 or Life *look* complex, it is that they can compute anything
computable, given a large enough grid and the right starting pattern. That a handful of
local rules — four counting conditions, in Life's case — can reach full computational
universality is one of the sharpest illustrations in the subject of how much is generated
by [[emergence]] from purely local interaction, with no rule anywhere stating "compute
this".

## Relationships

- [[cellular-automaton]], [[game-of-life]] — the systems shown to be Turing complete
- [[wolfram-classes]] — Turing complete rules are concentrated in Class 4
- [[emergence]] — computational universality as an extreme case of emergent capability

## Sources

- [[w04b-2d-cellular-automata]] — rule 110 and Conway's Game of Life as Turing complete
  systems, including Gosper's glider gun and signal/logic constructions.
