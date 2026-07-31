---
title: Agent Sensing
type: concept
tags: [abm, agent-behaviour, model-design]
date: 2026-08-01
---

# Agent Sensing

Agent sensing is the mechanism by which an agent perceives its environment — what it can
detect, and within what range. It is one of the core processes specified when choosing
[[model-structure]].

## How it works

Every agent that acts on its surroundings needs an explicit answer to two questions: *what
can it detect*, and *how far away*. The second is almost always a model parameter, and
often one of the most consequential.

In the truffle-foraging design ([[truffle-foraging-model-design]]), the sensing mechanism
is the pig's sense of smell. Making this explicit forces the question "how many metres can
the pig smell a truffle?" — a variable of the system that governs how tightly a search
path must be packed to guarantee coverage. Sensing radius and search geometry are coupled:
there is no point spacing a spiral more widely than the sensing radius.

Sensing may be indirect. Foragers proposed searching for *trees* rather than mushrooms,
since some mushrooms grow near particular hosts — the agent senses a correlated cue rather
than the target itself. This is a general and often cheaper pattern.

The same idea scales up beyond agents. In the NASA black-hole simulation
([[nasa-black-hole-simulation]]), the model's purpose was to predict what radiation the
collision would emit so that real instruments could be designed to detect it — sensing
design driven by simulation output.

Sensing is also what makes agents *local*. Agents in a [[complex-system]] act on
neighbourhood information only; the sensing radius is the formal statement of how local
"local" is. See [[flocking]], where vision radius plays exactly this role.

## Why it matters

Sensing is where much of an ABM's behaviour is implicitly decided. Change the detection
radius and you often change the emergent outcome, not just its speed — which makes it a
prime candidate for sensitivity analysis.

## Relationships

- [[model-structure]] — sensing is specified as a process, its range as a parameter
- [[search-strategy]] — sensing radius constrains viable search geometry
- [[flocking]] — vision radius as a sensing parameter
- [[complex-system]] — local information as a defining feature
- [[agent-based-model]]

## Sources

- [[w01b-modelling-cycle]] — drawn out in the truffle exercise ("what is the pig
  detecting? how far can it smell?") and echoed in the black-hole instrumentation example.
