---
title: BDI (Beliefs, Desires, Intentions)
type: concept
tags: [cognition, agent-behaviour, abm]
date: 2026-08-30
---

# BDI (Beliefs, Desires, Intentions)

BDI is a framework for modelling an agent's decision-making in terms of three components,
due to Rao and Georgeff (1995):

- **Beliefs** — what the agent knows about the world, meaning the world *as it perceives
  it to be*, not as it is.
- **Desires** — its motivations, its goals.
- **Intentions** — its deliberative states, the commitments it has settled on.

## How it works

A BDI implementation builds a decision tree from beliefs and desires, converts it into a
possible-worlds model, and runs a deliberation process to choose a course of action.

The belief/reality gap is the part worth carrying across to ABM design generally: beliefs
are the agent's model of the world, which makes them the natural home for
[[imperfect-information|sensing error and bias]]. An agent whose beliefs are stale or
wrong will act coherently on them.

## Why it matters

Kennedy's assessment is unflattering. BDI is so general that it amounts to little more
than a way of *thinking* about modelling cognition — it does not tell you how to implement
anything. [[pecs-framework|PECS]] was proposed explicitly to replace it with something more
specific. [[soar]] can be read as a BDI implementation, since it maintains an internal
world representation, always works towards a goal, and exposes internal state variables.

The framework earns its place as vocabulary. Separating what an agent believes from what
it wants from what it has committed to is a useful discipline when writing an
[[adaptive-behaviour|adaptation]] rule, even in a model that never uses BDI machinery.

## Relationships

- [[cognitive-architecture]] — the tier above
- [[pecs-framework]] — the intended replacement
- [[soar]] — arguably a BDI implementation
- [[imperfect-information]] — beliefs as the locus of sensing error

## Sources

- [[kennedy-2012-modelling-human-behaviour]] — definition, the possible-worlds
  deliberation, and the generality critique
