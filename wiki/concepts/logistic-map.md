---
title: Logistic Map
type: concept
tags: [chaos, dynamical-systems]
date: 2026-08-23
---

# Logistic Map

A single deterministic difference equation, $x_{n+1} = rx_n(1-x_n)$, used as the
simplest available demonstration that chaos does not require randomness or many
interacting components.

## How it works

$x_n \in [0,1]$ represents a normalised population fraction and $r$ is a growth-rate
parameter. Iterating the map from a starting value $x_0$ produces a sequence whose
long-run behaviour depends entirely on $r$: for small $r$ the sequence converges to a
single fixed point; past a threshold it settles into a 2-cycle, then a 4-cycle, and so
on — a period-doubling bifurcation cascade — until, past a further critical $r$, the
sequence becomes aperiodic and exhibits sensitive dependence on initial conditions
([[chaos]]). No term in the equation is stochastic; the unpredictability comes purely
from the nonlinearity of $rx_n(1-x_n)$ amplifying tiny differences in $x_0$ under
repeated iteration.

## Formula

$$x_{n+1} = r x_n (1 - x_n)$$

## Why it matters

It is the minimal case for the claim that complexity does not require many components:
one variable, one parameter, one equation, no interaction between separate agents or
cells, and yet the system's behaviour ranges from fixed-point convergence to full
chaos as $r$ varies. [[w04a-complex-systems-and-emergence]] uses it alongside the
three-body problem to make the same point from two different directions — one adds a
component to a solvable system and gets chaos, the other adds nothing but a parameter
change to a single equation and gets the same qualitative outcome.

## Relationships

Illustrates [[chaos]] without invoking a [[complex-system|complex system]] in the
many-interacting-components sense; contrasts with the three-body problem, which
reaches chaos by adding a component rather than tuning a parameter.

## Sources

- [[sources/w04a-complex-systems-and-emergence]] — used as the lecture's minimal,
  component-free example of deterministic chaos
