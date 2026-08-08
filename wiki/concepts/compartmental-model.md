---
title: Compartmental Model
type: concept
tags: [epidemiology, model-design, abm]
date: 2026-08-06
---

# Compartmental Model

A compartmental model partitions a population into a small number of mutually exclusive
states, or compartments, and describes the system by the flows between them. The
[[sir-model]] is the canonical example.

## How it works

In the original mathematical formulation, each compartment holds a *fraction* of the
population and the arrows between compartments are flow rates, giving a system of coupled
differential equations describing the population in aggregate. No individual is
represented; the model tracks how much of the population sits in each state over time.

The agent-based reinterpretation reuses the same box-and-arrow diagram for a different
purpose. Each agent holds one state at a time, and the diagram describes the sequence of
transitions a single individual can undergo — closer to a state machine than to a system of
equations. Population-level counts then emerge from summing over agents rather than being
the modelled quantity.

The distinction matters when extending the model. Adding a compartment to the aggregate
version means adding an equation and a rate; adding one to the agent-based version means
adding a state and the rules governing entry and exit, which can depend on an individual
agent's history, location or attributes in ways an aggregate rate cannot express. The
zombie exercise made this concrete by splitting "removed" into two compartments — died of
natural causes, and destroyed after reanimating — because they behave differently: one can
still become a zombie and the other cannot ([[zombie-apocalypse-model-design]]).

## Why it matters

Compartmental structure is the vocabulary for talking about disease-model extensions. SEIR
adds an exposed-but-not-yet-infectious state, SIRS returns recovered individuals to
susceptible, and adding a dead state distinguishes recovery from mortality. Each is a
change to the compartment diagram before it is a change to any code, which is exactly the
level at which the [[odd-protocol]] wants the model described.

## Relationships

- [[sir-model]] — the specific instance taught
- [[agent-based-model]] — the reinterpretation of compartments as individual states
- [[model-extension]] — adding compartments as the standard extension route
- [[model-structure]] — compartments are state-variable values
- [[compartmental-vs-agent-based]] — the two readings of the diagram compared in full

## Sources

- [[w02b-modelling-disease-spread]] — notes that the compartments originated as population
  fractions with flows between them, and that the same diagram serves for an individual
  agent's state sequence in an ABM.
