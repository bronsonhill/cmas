---
title: Emergence
type: concept
tags: [complexity, foundations]
date: 2026-08-01
---

# Emergence

Emergence is the appearance of system-level patterns or properties that are not encoded in
the rules of any individual component, and that arise from the interactions between
components.

## How it works

The critical negative claim: nothing in the specification says "form a cluster" or "all
travel in the same direction". The rules are local — how far to stay from a neighbour, how
far one can see, how sharply one can turn — yet the population-level pattern appears
reliably. In the NetLogo Flocking model, [[boids]] were observed to clump into groups and
to settle onto a common heading, neither of which is a rule in the model.

Two consequences follow:

- Emergent properties are typically discovered by *running* the model, not by inspecting
  its code. This is why [[simulation]] rather than analysis is the method.
- Emergence is sensitive to parameters. Changing vision radius, turn rate or speed can
  move the model from a lively regime into a frozen steady state or into incoherence — see
  [[tipping-point]].

## Why it matters

Emergence is the reason [[agent-based-model|ABMs]] are worth building. If system behaviour
were a simple sum of component behaviour, you could compute it directly. It is the fact
that the whole is not readable off the parts that makes simulation necessary — and makes
the modeller's job partly one of *observation*: run the model and see what patterns appear.

## Relationships

- [[complex-system]] — where emergence occurs
- [[flocking]], [[boids]] — the canonical demonstration
- [[agent-based-model]] — the modelling method built around it
- [[tipping-point]] — where emergent regimes change

## Sources

- [[w01a-introduction]] — demonstrates emergence via murmurations and the NetLogo Flocking
  model; explicit that clustering and common heading were never specified as rules.
