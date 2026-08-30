---
title: Adaptive Behaviour
type: concept
tags: [abm, agent-behaviour, odd]
date: 2026-08-30
---

# Adaptive Behaviour

Adaptive behaviour is a decision an agent makes **during** a simulation, in response to
information it has sensed about its own state and its environment, aimed at improving its
state with respect to some [[objective-function|objective]]. It is one of the ODD design
concepts ([[odd-protocol]]).

## How it works

Three pieces have to be in place before an agent can adapt: something it can perceive
([[agent-sensing]]), a criterion for ranking outcomes ([[objective-function]]), and a set
of actions it can take. The adaptation rule is the mapping from the first to the third
via the second.

The [[business-investment-model]] version is minimal: each year an agent evaluates the
utility of every opportunity within its sensing radius and relocates to the best one. In
an infectious-disease ABM the same slot might hold "if the proportion of infected agents
nearby exceeds a threshold, put on a mask, or move away". A predator with an energy
budget adapts by choosing when to hunt and when to rest.

Grimm's protocol distinguishes **direct** and **indirect** adaptive behaviour. Direct
adaptation evaluates the objective explicitly — compute utility for each option, pick the
maximum. Indirect adaptation encodes behaviour that merely tends to improve the objective
without ever computing it: a rule like "move towards greener patches" pursues fitness
without an explicit fitness calculation. Most simple ABM rules, including the boids
rules in [[flocking]], are indirect.

## Adaptation is not learning

The distinction that catches people out, and that the lectures flag as exam material:

- **Adaptation** operates *within* a simulation run. State at $t$ determines action at
  $t$; nothing survives the run.
- **[[agent-learning|Learning]]** operates *across* runs, or across repeated episodes
  inside one run. The agent carries experience forward and changes the rule itself.

An evacuation model where agents reroute around a blocked exit is adapting. One where
agents remember exit locations from a previous drill is learning.

## Why it matters

An interest in how individual decisions collectively shape system behaviour is the main
reason to reach for an [[agent-based-model]] at all. Adaptation is where that interest is
made concrete — it is the rule whose consequences the model exists to explore, and
changing it changes the [[emergence|emergent]] outcome more reliably than changing almost
any parameter.

## Relationships

- [[objective-function]] — the criterion adaptation optimises or approximates
- [[agent-sensing]] — the input side
- [[agent-learning]] — the across-run counterpart
- [[agent-prediction]] — adaptation over a time horizon needs a prediction
- [[satisficing]] / [[optimisation]] — two decision rules an adaptation can use
- [[odd-protocol]] — where adaptation is documented

## Sources

- [[w05a-sensing]] — adaptation named among the design concepts; the within-run vs
  across-run distinction against learning
- [[w05b-adaptation-and-objectives]] — full definition and the business investment model
  as the worked case
