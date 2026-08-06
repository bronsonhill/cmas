---
title: Null Model
type: concept
tags: [methodology, model-design, assumptions]
date: 2026-08-06
---

# Null Model

A null model is a baseline built to contain as little structure as possible, so that any
pattern the full model produces can be attributed to the mechanism under study rather than
to an assumption smuggled in through the setup.

## How it works

The subject's scaffolding [[sir-model]] is the worked case. Agents are scattered uniformly
across a plain, unstructured space with no terrain, no buildings and no neighbourhoods. The
justification is informational: the uniform distribution assigns equal probability to every
position, so it introduces no positional bias. Any clustering or spatial pattern in the
results must then come from the transmission dynamics, because nothing in the initial layout
could have produced it.

The alternative is a confound. If agents started clustered and an outbreak turned out to be
localised, there would be no way to tell whether the locality came from transmission or
from the starting arrangement.

The same reasoning gives the single patient zero. One initially infectious agent is both the
minimal seeding and the realistic one — outbreaks begin with an index case, not a cohort.
Starting with 20 infected agents is not a neutral variation; it adds an assumption about how
the disease arrived, which then has to be justified and which changes the early dynamics for
reasons unrelated to the mechanism being studied.

## Why it matters

Null models are how you tell mechanism from artefact. They are also the natural starting
point of the "start simple, then extend" heuristic ([[model-extension]]): each element
added to a null baseline can be evaluated for what it contributes, in the same way ablation
isolates a component's effect in machine learning. Building the structured version first
leaves you with a model whose behaviour you cannot decompose.

## Relationships

- [[initial-conditions]] — where the null assumption is expressed
- [[sir-model]] — the model whose scaffolding uses one
- [[model-extension]] — the null model is the baseline extensions are measured against
- [[abstraction]] — the null model is the maximally abstracted case
- [[stochasticity]] — the uniform distribution as the least-informative random choice

## Sources

- [[w02b-modelling-disease-spread]] — the Ed board answer explaining why the scaffolding
  model uses a uniform agent distribution over an unstructured space and a single initially
  infected agent.
