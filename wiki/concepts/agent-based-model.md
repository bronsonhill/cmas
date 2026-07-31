---
title: Agent-Based Model
type: concept
tags: [abm, foundations, definitions]
date: 2026-08-01
---

# Agent-Based Model

An agent-based model (ABM) is a particular type of [[simulation]] model that focuses on
the **actions and interactions of autonomous agents** in order to understand the behaviour
of a system as a whole.

## How it works

An ABM is built bottom-up. Rather than writing an equation for the aggregate behaviour of
the system, you specify what one individual does — a person, a company, an animal, a
vehicle — and then instantiate many of them and let them interact. The system-level
behaviour is an *output* of the model, not an input to it.

Three ingredients recur:

- **Agents** — autonomous entities with attributes and behavioural rules.
- **Interactions** — agents are not modelled in isolation; the interactions are the point.
- **Environment** — the space or landscape agents act in, which may itself carry state.
  In the JASSS agricultural pest model shown in Week 1, GIS environmental data
  (temperature, crops, precipitation) and GIS social data (village locations, population)
  combined with a cellular automaton for pest dynamics and a population of farmer agents
  with differing pest-control knowledge.

Agents typically have only **local** information, mirroring reality: a bird sees its
neighbours, not the flock; a person in a crowd feels those next to them, not the exits.
See [[flocking]] for the canonical demonstration.

ABMs answer three kinds of question:

1. **Understand** — what happens if contact rates fall, or masks are worn?
2. **Control** — what policy, and of what duration, flattens the curve?
3. **Design** — how should NPCs in a game behave, or a road network be laid out?

This is a different epistemology from machine learning. An ML model is fitted from
training data; an ABM encodes hypothesised *rules* governing the system and is then tested
against observed patterns.

## Why it matters

ABMs are the right tool whenever heterogeneity, local interaction, and adaptation matter —
that is, whenever averaging over the population would destroy the mechanism you care
about. They also produce policy-relevant counterfactuals: see
[[covid-19-abm-australia]], where scenario simulations directly informed Australian
lockdown decisions.

## History

- **1940s–1970s** — conceptual foundations laid
- **1980s–1990s** — cheap, high-powered computing; [[boids]] (c. 1987)
- **2000s–2010s** — modelling-specific languages and libraries ([[netlogo]], [[mesa]])
- **Today** — million-agent models, allowing whole cities and countries to be simulated

Now applied in biology, economics, ecology, epidemiology, finance and marketing, social
science, transportation, and the military.

## Relationships

- [[simulation]], [[model]] — the broader categories ABM sits inside
- [[complex-system]], [[emergence]] — what ABMs are built to study
- [[flocking]], [[boids]] — worked example
- [[modelling-cycle]] — how ABMs are developed
- [[counterfactual]] — alternate-scenario experiments
- [[agent-sensing]], [[search-strategy]] — common agent processes
- [[netlogo]], [[mesa]] — implementation tools

## Sources

- [[w01a-introduction]] — defines ABM, situates it against other model types, gives the
  understand/control/design framing and the historical arc.
- [[w01b-modelling-cycle]] — adds [[counterfactual]] experimentation and the ethical case
  for testing social interventions on simulated rather than real people.
