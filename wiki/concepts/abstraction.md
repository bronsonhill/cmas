---
title: Abstraction
type: concept
tags: [foundations, model-design]
date: 2026-08-01
---

# Abstraction

Abstraction is the deliberate stripping away of detail so that a [[model]] retains only
the elements essential to its purpose. A model is, by definition, **simpler** than the
system it represents.

## How it works

Abstraction is not an unfortunate compromise forced by limited compute — it is what makes
a model usable. The question is never "how much detail can I include?" but "which details
does my purpose require?"

Three models of the Earth make the point, each abstracting differently and each correct
for its own purpose:

- The **Mercator world map** ([[mercator-projection]]) keeps landmass positions, altitude
  and ocean depth, and discards accurate area — enough to locate yourself, at the cost of
  Greenland appearing nearly the size of Africa.
- The **cut-away of the Earth's interior** is explicitly labelled "not to scale". The crust
  is a thin sliver in reality but drawn thick, because the crust is where we live and mine.
  The distortion serves the purpose.
- The **heliocentric model** ([[heliocentric-model]]) abstracts away the epicycles the
  geocentric model needed, explaining the same observations with less machinery.

A useful diagnostic when designing: for each candidate element, ask whether the answer to
your question would change if you left it out. In a disease model, household size changes
the answer; supermarket basket size does not.

## Why it matters

Abstraction is where the modeller's judgement lives, and it is the skill the subject's
projects assess. The common failure mode is over-inclusion — building the most detailed
model possible rather than the simplest adequate one, which costs time, invites bugs, and
obscures the mechanism you were trying to isolate.

## Relationships

- [[model]] — abstraction is intrinsic to the definition
- [[occams-razor]] — the principle favouring the simpler adequate model
- [[research-question]] — what determines which abstractions are legitimate
- [[modelling-cycle]] — abstraction decisions are made at steps 2 and 3
- [[mercator-projection]], [[heliocentric-model]] — worked examples

## Sources

- [[w01b-modelling-cycle]] — "models abstract away detail, i.e. they are simpler than the
  system they represent", developed through the models-of-the-Earth sequence.
