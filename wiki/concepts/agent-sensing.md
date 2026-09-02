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

Week 5a splits this into three questions, which is the version to use when writing an
[[odd-protocol|ODD]] description:

1. **What information** — which state variables does the agent use?
2. **Which entities** — which other agents and which parts of the environment can it
   obtain them from? See [[agent-neighbourhood]].
3. **How** — is the information perfect, or subject to error or bias? See
   [[imperfect-information]].

The first question is organised by variable **scope**:

| Scope | Varies over | Example |
|---|---|---|
| Global variables | Time only | Interest rate, weather, prices |
| Local environmental variables | Space | A NetLogo patch's elevation or resources |
| Agent variables | Per agent | Own or another agent's wealth, bearing, type |
| Model parameters | Fixed per run | Interface sliders; what BehaviorSpace sweeps |

Muñoz worked the whole taxonomy through house-hunting: the cash rate is a global
variable, school catchments and flood risk are local environmental variables, and the
apparent seriousness of a rival bidder at an inspection is a very noisy reading of another
agent's state.

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

The change need not be monotonic. In the [[business-investment-model]], widening the
sensing radius improved mean investor wealth up to about radius 5 and then made it worse
at radius 8. More information is not automatically better information.

## Relationships

- [[model-structure]] — sensing is specified as a process, its range as a parameter
- [[search-strategy]] — sensing radius constrains viable search geometry
- [[flocking]] — vision radius as a sensing parameter
- [[complex-system]] — local information as a defining feature
- [[agent-based-model]]
- [[agent-neighbourhood]] — the formal specification of what an agent can reach
- [[imperfect-information]] — range, coverage, error and bias
- [[adaptive-behaviour]] — what the sensed information feeds

## Sources

- [[w01b-modelling-cycle]] — drawn out in the truffle exercise ("what is the pig
  detecting? how far can it smell?") and echoed in the black-hole instrumentation example.
- [[w05a-sensing]] — the three sensing questions, variable scope, neighbourhood types, and
  sensing as an ODD design concept.
- [[w05b-adaptation-and-objectives]] — the sensing-radius sweep and the network
  experiment on the business investment model.
