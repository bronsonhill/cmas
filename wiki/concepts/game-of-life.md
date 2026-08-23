---
title: Conway's Game of Life
type: concept
tags: [complexity, cellular-automata]
date: 2026-08-23
---

# Conway's Game of Life

Conway's Game of Life is a 2D [[cellular-automaton]] in which each cell is alive or dead,
updated synchronously each generation by four rules based on its eight-cell (Moore)
neighbourhood.

## How it works

The rules: a live cell with fewer than two live neighbours dies ("loneliness"); a live cell
with more than three live neighbours dies ("overcrowding"); a live cell with exactly two or
three live neighbours survives; a dead cell with exactly three live neighbours becomes
alive ("reproduction"). All cells update simultaneously from the previous generation's
state, then the process repeats.

From this handful of rules, three qualitative pattern classes emerge: **stable**
still-lifes that never change once reached; **periodic** oscillators that cycle between a
small set of configurations; and **mobile** patterns such as gliders that translate across
the grid over successive generations while repeating their shape. Gosper's glider gun
periodically emits gliders, and constructions built from Life patterns can implement
information-carrying signals and logical operations on those signals — the basis for
proving Life [[turing-completeness|Turing complete]], alongside a working universal Turing
machine built entirely from Life cells.

## Why it matters

Life is the standard demonstration that [[emergence]] and [[self-organisation]] do not
require anything beyond a grid, two states, and four local counting rules: organised,
structured behaviour (still-lifes, oscillators, travelling gliders) appears from rules that
say nothing about global pattern. Its Turing completeness is a stronger claim still — Life
is not just complex-looking, it is computationally universal, which places an upper bound
on how far the model's simplicity limits its power, even as its update assumptions
(synchronous, deterministic) remain unrealistic for most real complex systems.

## Relationships

- [[cellular-automaton]] — the general framework Life instantiates
- [[wolfram-classes]] — Life's behaviour spans several Wolfram classes depending on
  configuration
- [[turing-completeness]] — proved via glider-based signal/logic constructions
- [[emergence]], [[self-organisation]] — canonical demonstration case

## Sources

- [[w04b-2d-cellular-automata]] — full rule set, pattern classes (stable/periodic/mobile),
  Gosper's glider gun, and Turing completeness via signal-carrying constructions.
