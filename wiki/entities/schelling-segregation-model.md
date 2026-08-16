---
title: Schelling Segregation Model
type: entity
entity_type: model
tags: [abm, social-science, emergence, netlogo]
date: 2026-08-16
---

# Schelling Segregation Model

An agent-based model of residential segregation in which households relocate when too few of
their neighbours are of the same type. It shows that mild individual preferences are
sufficient to produce strongly segregated neighbourhoods, without anyone holding a
preference for segregation.

## Key facts

- Devised by [[thomas-schelling]]; available as a standard model in the [[netlogo]] Models
  Library and used for live demonstration in the Week 3a lecture.
- The world is a grid representing a geographical area. Each occupied cell holds a household
  of one of two types; empty cells are the vacancies that make movement possible.
- One parameter governs behaviour: a similarity threshold, the percentage of same-type
  neighbours a household requires to be content. Discontented households relocate to a
  vacant cell.
- The reported outputs are the percentage of unhappy agents (which falls to zero at
  convergence) and the average percentage of similar neighbours.
- At a 30% threshold the model converges quickly to roughly 73% average similarity, with
  clearly defined clusters — well above what any individual demanded.
- At a 90% threshold the model does not converge at all: too few households can be satisfied
  simultaneously for the system to settle.
- Convergence breaks down somewhere around a 70% threshold, a [[tipping-point]] the subject
  returns to.

## Relevance

The model is the subject's worked example of [[modelling-for-science]] — an observed
population-level pattern explained by a hypothesised individual-level rule, tested by varying
the rule's strength and measuring the pattern. It is also a clean case of [[emergence]]: the
aggregate outcome (73% homogeneity) is not present in, and considerably exceeds, the
individual rule (30% tolerance) that produces it.

The failure to converge at high thresholds is the second lesson, and the one that connects
forward. It shows that pushing a parameter further does not simply intensify the same
behaviour — past a critical value the system's qualitative behaviour changes, which is the
same structure as an epidemic's threshold at $R = 1$ ([[reproduction-number]]).

## Sources

- [[w03a-analysing-models]] — demonstrated live in NetLogo, worked through the six steps of
  the inductive approach, with the 30%, 70% and 90% threshold results.
