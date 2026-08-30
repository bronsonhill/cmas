---
title: Cognitive Architecture
type: concept
tags: [cognition, agent-behaviour, abm]
date: 2026-08-30
---

# Cognitive Architecture

A cognitive architecture is the fixed structure and functionality within which cognitive
models are written — the part that stays constant while task-specific models come and go.
The term is Newell's (1990). [[soar]] and [[act-r]] are the two with real communities
behind them.

## How it works

Kennedy ([[kennedy-2012-modelling-human-behaviour]]) puts cognitive architectures at the
top of a three-tier ladder of ways to drive an agent's behaviour, ordered by fidelity and
cost:

1. **Mathematical approaches** — random draws, [[threshold-rule|threshold rules]],
   multi-parameter [[objective-function|objective functions]], stock-and-flow dynamic
   models. Coded directly in the simulation's own language.
2. **Conceptual frameworks** — [[bdi-architecture|BDI]], [[pecs-framework|PECS]],
   [[fast-and-frugal-heuristics|fast-and-frugal trees]]. Reason in beliefs, motives and
   cues rather than parameter arithmetic.
3. **Cognitive architectures** — Soar, ACT-R. Research-grade models of an individual
   mind, some operating at millisecond resolution.

An architecture supplies memory, knowledge representation, a decision cycle and usually
learning; the modeller writes rules and facts on top. A model built inside one can then be
embedded in an ABM as the agent's decision procedure.

## Why it matters

The catch is that these tools were built for a different purpose. Soar's goal is matching
or exceeding human performance on problem-solving tasks; ACT-R's is matching human
performance data on low-level cognition over very short periods. Neither was designed to
run inside a simulation of ten thousand agents, and ACT-R does not represent beliefs,
desires or intentions explicitly at all. Borrowing them buys psychological fidelity at a
computational cost, and the fidelity is at a timescale most ABMs do not care about.

For most agent-based models the right tier is the first or second. Kennedy's own framing:
if the vast majority of an agent's human behaviour is irrelevant to the model's purpose,
and the relevant part can be specified, a mathematical approach is appropriate.

## Relationships

- [[soar]] / [[act-r]] — the two established architectures
- [[bdi-architecture]] / [[pecs-framework]] — the tier below
- [[threshold-rule]] — the tier below that
- [[agent-learning]] — architectures supply learning mechanisms off the shelf
- [[abstraction]] — choosing a tier is choosing how much detail serves the purpose

## Sources

- [[kennedy-2012-modelling-human-behaviour]] — the three-tier survey and the caveats on
  borrowing research tools
