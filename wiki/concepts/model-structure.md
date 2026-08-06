---
title: Model Structure
type: concept
tags: [methodology, model-design, abm]
date: 2026-08-01
---

# Model Structure

Model structure is the concrete specification of a model: its scales, entities, state
variables, processes and parameters. Choosing it is step 3 of the [[modelling-cycle]] —
the point at which hypotheses become rules and algorithms.

## How it works

Five things must be pinned down:

- **Scales.** How big is the simulated world, and over what time span? For a truffle
  search this might be a grid of a few kilometres — as far as a forager can walk in a day.
  You would not build an Australia-sized world to model foraging in one forest.
- **Entities.** What exists in the model? The agents (foragers, pigs), and any other
  objects the question requires. Being explicit here also means being explicit about what
  is *not* included.
- **State variables.** What does each entity need to remember? For a searching agent: its
  current search mode — is it moving randomly, or has it found something and switched to
  local search?
- **Processes.** The tasks entities perform: sensing, moving, consuming, reproducing.
- **Parameters.** The adjustable quantities — detection radius, step size, number of
  agents — which are what you later sweep, calibrate and analyse for sensitivity.

The deliverable at this stage is a **written outline, not code**. Sketch the entities,
their characteristics, the environment they occupy and their behaviour in plain language.
This is deliberate: a plain-language description can be reviewed by domain experts who are
not programmers — a zoologist or botanist can read it and say "this looks reasonable, but
you should add X" — which is exactly the multidisciplinary check that catches structural
errors before they are expensive. See [[model-communication]].

## Why it matters

This is where a vague intention becomes something implementable, and where most silent
mistakes are made — an omitted state variable or a badly chosen scale is far cheaper to
fix on paper than after implementation. It also maps directly onto the [[odd-protocol]],
which is the formal template for writing exactly this specification down: purpose,
entities and state variables, [[model-scales]], processes and [[scheduling]], then the
details of [[initial-conditions]], input data and submodels.

## Relationships

- [[odd-protocol]] — the formalisation of this specification
- [[modelling-cycle]] — step 3
- [[research-question]] — determines what the structure must contain
- [[abstraction]] — the judgement applied when selecting elements
- [[agent-sensing]] — a commonly required process
- [[agent-based-model]] — the kind of model being structured
- [[truffle-foraging-model-design]] — worked example

## Sources

- [[w01b-modelling-cycle]] — "choose scales, entities, state variables, processes, and
  parameters", with the emphasis on producing a written outline before writing code.
- [[w02a-describing-models]] — the ODD protocol as the standardised form of this outline.
