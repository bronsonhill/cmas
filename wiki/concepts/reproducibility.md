---
title: Reproducibility
type: concept
tags: [methodology, scientific-practice, odd]
date: 2026-08-06
---

# Reproducibility

Reproducibility is the ability of someone other than the original author to rebuild a model
or experiment from its description and obtain the same results. It is one of the two stated
motivations for the [[odd-protocol]], alongside model interpretation.

## How it works

For a simulation model, reproducing a result requires the full specification: the entities
and their state variables, the processes, the schedule, the parameter values, and the
[[initial-conditions]]. Omitting any of these makes the description unreproducible even
when the reported results are correct. Stochastic models add a further requirement — the
random seed, or enough replicate runs to characterise the distribution rather than one
sample from it ([[stochasticity]]).

The lecture placed this against the replication crisis. A large proportion of published
medical results failed to replicate when other groups repeated the experiments; the failures
were traced to gaps in how the procedures were described, not to the results being hidden.
Computing has a version of the same problem: in optimisation research, algorithms are
frequently evaluated so poorly that the comparisons cannot be repeated, which has prompted
the development of explicit lab protocols specifying how data is collected and how software
is released.

Publishing the code is a partial answer and not a sufficient one. Code can be long, its
style idiosyncratic, and its audience often does not read the language it is written in.
A plain-language description survives the translation to a multidisciplinary team in a way
that a repository does not — see [[model-communication]].

## Why it matters

A model that cannot be reproduced cannot be built on, and a model that informs policy that
cannot be reproduced cannot be audited. Reproducibility is also self-serving on a shorter
horizon: a documented model can be picked up by a colleague, or by you, after the original
author has left.

## Relationships

- [[odd-protocol]] — the protocol exists partly to serve this
- [[initial-conditions]] — a necessary component of a reproducible description
- [[stochasticity]] — why single runs are not reproducible results
- [[model-communication]] — why code alone does not suffice

## Sources

- [[w02a-describing-models]] — the replication crisis in medicine, poor experimental practice
  in optimisation research, and the argument that code is not a substitute for description.
