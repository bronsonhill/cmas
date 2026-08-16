---
title: Model Analysis
type: concept
tags: [modelling-cycle, model-design, simulation]
date: 2026-08-16
---

# Model Analysis

Analysing a model means two things at once: studying it to understand how it behaves and to
establish that it is correct, and using it to solve the problem it was built for. It is the
fifth step of the [[modelling-cycle]], and the point at which a model stops being an artefact
and starts being an instrument.

## How it works

The case for analysing a simulation rather than the real system is about access. Real-world
study is limited to the data you can collect, and collecting more may be expensive, slow,
unethical or impossible — paying survey participants, travelling to wherever the animals you
study live, or deliberately infecting people to observe transmission. A simulation can be
manipulated freely and observed as often as you like, including in states the real system
would never let you reach.

That freedom has to be used systematically. The lecture draws a line between *playing* with
a model — moving sliders and watching what happens, which is how the subject has engaged
with models up to this point — and designing controlled experiments. The transition is
governed by two questions asked before touching anything:

1. What do I want to know about the model's behaviour?
2. How can I design experiments to learn it?

An experiment then varies parameters, initial conditions and random seeds from a stated
baseline in a structured way — a seed value and systematic variations up and down — rather
than opportunistically. What is varied and what is held fixed follows from the question
([[research-question]]).

The other half of analysis is deciding what to record. A model can produce far more output
than can be interpreted, so the analysis design includes choosing summary measures
([[summary-statistic]]) and, for stochastic models, running enough replicates to see the
distribution of those measures rather than a single sample.

## Why it matters

Analysis is where two distinct failures get caught. The first is that the model is not an
adequate abstraction of the system — it does not reproduce the patterns it was supposed to
explain, which sends you back around the [[modelling-cycle]] to revise hypotheses or
structure ([[pattern-oriented-modelling]]). The second is that the model is correct but the
analysis of it is wrong, which is the failure the Week 3 lecture spends most of its time on:
compressing bimodal output into a mean produces a confident answer that is not true of any
run the model performed ([[bimodal-distribution]]).

What analysis is *for* depends on the model's purpose. Under [[modelling-for-science]] the
goal is to test whether hypothesised individual behaviours reproduce an observed
population-level pattern. Under [[modelling-for-policy]] the model is assumed already
validated and analysis produces projections comparing interventions. The same model can serve
both, but the experiments and the summary measures differ.

## Relationships

- [[modelling-cycle]] — analysis is the step preceding communication
- [[modelling-for-science]], [[modelling-for-policy]] — the two purposes shaping it
- [[summary-statistic]], [[outbreak-summary-measures]] — deciding what to record
- [[bimodal-distribution]], [[stochastic-fadeout]] — the failure modes it must avoid
- [[research-question]] — what determines the experiment design
- [[initial-conditions]], [[stochasticity]] — among the things an experiment varies
- [[pattern-oriented-modelling]] — patterns as the criterion for adequacy
- [[reproducibility]] — seed management as part of experiment design

## Sources

- [[w03a-analysing-models]] — defines what it means to analyse a model, gives the argument
  from data cost and feasibility, and sets out the move from playing to controlled
  experiments.
