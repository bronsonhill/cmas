---
title: Fast-and-Frugal Heuristics
type: concept
tags: [cognition, agent-behaviour, decision-making, abm]
date: 2026-08-30
---

# Fast-and-Frugal Heuristics

Fast-and-frugal decision trees are short sequences of yes/no questions on environmental
variables that reproduce expert human decisions. The framework is
[[gerd-gigerenzer|Gigerenzer's]] (2007), derived by analysing what decisions people
actually made rather than by theorising about what they should.

## How it works

The trees are built empirically. Gigerenzer analysed how intensive care units decided
whether a patient was having a heart attack, and how two UK magistrates decided whether to
grant bail. In both cases three sequential questions, answerable from available
environmental variables, captured the decision.

The design goal is not to identify every variable that justifies an action. It is to
identify the few that suffice, which is what distinguishes a fast-and-frugal tree from an
[[objective-function]] over many parameters.

## Why it matters

Two results make this attractive for ABMs. First, accuracy: the medical tree outperformed
both the heart disease predictive instrument and the physicians themselves, and the bail
tree explained 92% of the magistrates' decisions. A three-question rule beat the
sophisticated alternatives. Second, cost: the trees are computationally trivial and scale
to large agent populations, which the [[cognitive-architecture|cognitive architectures]]
do not.

Together these make fast-and-frugal trees close to the ideal shape for an agent decision
rule — empirically grounded, cheap, and interpretable. The constraint is that building one
requires data on real decisions, which for most behaviours of interest does not exist.

## Relationships

- [[threshold-rule]] — the individual tests in a tree
- [[bounded-rationality]] — heuristics as competent decision-making under limits
- [[satisficing]] — the same rejection of exhaustive evaluation
- [[cognitive-architecture]] — the expensive alternative
- [[gerd-gigerenzer]]

## Sources

- [[kennedy-2012-modelling-human-behaviour]] — the ICU and magistrate studies, the
  performance figures, and the scaling argument
