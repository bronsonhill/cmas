---
title: Cellular Automaton
type: concept
tags: [cellular-automata, discrete-models, emergence]
date: 2026-07-20
---

# Cellular Automaton

A cellular automaton (CA) is a grid of cells, each in one of finitely many states,
that all update simultaneously according to the same rule applied to a cell's own
state and its neighbours'.

## How it works

A CA is defined by four things:

1. **Lattice** — the grid of cells (1D line, 2D square grid, hexagonal, …).
2. **States** — the finite set $S$ a cell can be in; often $S = \{0, 1\}$.
3. **Neighbourhood** — which nearby cells a rule can see. On a 2D grid the two
   standard choices are the *von Neumann* neighbourhood (4 orthogonal neighbours)
   and the *Moore* neighbourhood (all 8 surrounding cells).
4. **Transition rule** — a function from a cell's neighbourhood configuration to
   its next state, applied to every cell at once (*synchronous update*).

The synchrony matters: every cell's next state is computed from the *current*
configuration, then the whole grid is swapped over. Updating cells one at a time
in place gives a different — and usually wrong — model.

## Formula

Let $s_i^t \in S$ be the state of cell $i$ at time $t$, and $N(i)$ its
neighbourhood. The whole model is one function $f$ applied everywhere:

$$
s_i^{t+1} = f\left( s_i^t, \; \{ s_j^t : j \in N(i) \} \right)
$$

Conway's Game of Life is the case $S = \{0, 1\}$ with the Moore neighbourhood,
where the rule depends only on the count of live neighbours
$n_i^t = \sum_{j \in N(i)} s_j^t$:

$$
s_i^{t+1} =
\begin{cases}
1 & \text{if } s_i^t = 1 \text{ and } n_i^t \in \{2, 3\} \\
1 & \text{if } s_i^t = 0 \text{ and } n_i^t = 3 \\
0 & \text{otherwise}
\end{cases}
$$

## Why it matters

CAs are the cleanest demonstration that **complex global behaviour does not
require complex local rules**. Game of Life's four-line rule produces stable
structures, oscillators, and gliders that travel across the grid — none of which
appear anywhere in the rule itself. That gap between local specification and
global outcome is the thing computational modelling exists to explore, and a CA
is the smallest system where you can see it happen.

They are also the natural starting point for [[agent-based-model|agent-based
models]]: a CA is roughly an ABM whose agents are immobile, identical, and see
only their immediate neighbours. Relaxing any of those assumptions moves you
toward a full ABM.

## Relationships

- [[agent-based-model]] — generalises the CA by giving agents mobility and
  individual state
- [[netlogo]] — models CAs directly as patch update rules

## Sources

- [[netlogo-users-manual]] — patch-based modelling and the Game of Life model in
  the Models Library
