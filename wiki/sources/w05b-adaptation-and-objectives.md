---
title: "Week 5b: Modelling Agent Behaviour — Adaptation & Objectives"
type: source
source_type: lecture
link: https://canvas.lms.unimelb.edu.au/courses/239814
tags: [comp90083, week-05, lecture, agent-behaviour, adaptation, objectives, satisficing, netlogo]
date: 2026-08-30
---

# Week 5b: Modelling Agent Behaviour — Adaptation & Objectives

## Overview

The second Week 5 lecture picks up the [[business-investment-model]] from
[[w05a-sensing]] and uses it as a laboratory. Most of the session is a live NetLogo
experiment: vary the sensing radius, then switch on a communication network, and watch
what happens to mean investor wealth after 25 simulated years. The theory — adaptation,
objectives, [[satisficing]] — is drawn out of what the model does rather than presented
first.

The experiment produces the lecture's headline result, and it is a counterintuitive one.
Raising the sensing radius from 1 to 2 to 5 improves final mean wealth each time; raising
it to 8 makes it *worse*. Muñoz labelled this the **paradox of choice** — more available
options generate more opportunity for regret and, in the model, no better outcome — and
was careful to mark his mechanism for it as an untested hypothesis rather than a result.
The structural reason he did offer is that the investment landscape is uniformly random
with no correlation between adjacent patches, so a wider view reveals more options but no
*gradient* to follow. Switching on the network, so every agent can see what every other
agent is doing, likewise failed to beat the radius-1 baseline for the same reason:
knowing that a distant agent is doing well says nothing about which direction to move
when the landscape has no structure. He drew an explicit analogy to a machine-learning
learning rate — a bigger step reaches a local optimum faster and then stays stuck in it.

Two dynamics recur across every parameter setting. Mean profit rises steeply on the first
tick and then flattens: on a uniform random landscape roughly half the neighbouring
patches beat the current one, so the first move is almost always an improvement and later
moves have progressively less headroom. Mean risk falls monotonically and then plateaus,
because the $(1-F)^T$ term in the utility punishes failure risk more heavily as the
horizon shortens — agents late in the run will not trade safety for profit, find a local
optimum, and stop moving.

That stagnation motivates the theory. The model's agents are **optimisers**: they
enumerate every visible opportunity, evaluate $U$ for each, and take the best. Real
decision-makers usually cannot — the information is unavailable, or too costly to get
(Muñoz's example: a Bloomberg terminal seat at roughly $30{,}000$ per year). They
[[satisficing|satisfice]] instead, accepting an option that clears an aspiration level.
The proposed redesign of the model makes this concrete: replace "move to the best visible
patch" with a **satisficing threshold** — a minimum rate of return, say 5% a year — and
strip the agent's ability to see alternatives, so a dissatisfied agent moves to a random
available patch. Muñoz's prediction, to be tested next week: satisficing agents explore
more, accept short-term losses, and end up closer to optimal than the greedy optimisers.

The closing section is about the [[objective-function]] itself — the criterion, called
fitness in ecological models and utility in economic ones. Change it and the model
changes. If businesses could post negative profits, agents could plausibly maximise
profit while ignoring risk, or ignore wealth entirely and only avoid ruin. Different
subsets of agents could carry different objective functions in the same run, which is how
heterogeneous risk appetite enters an ABM.

## Key concepts

- [[adaptive-behaviour]]
- [[objective-function]]
- [[satisficing]]
- [[optimisation]]
- [[bounded-rationality]]
- [[agent-sensing]]
- [[imperfect-information]]

## Key entities

- [[andres-munoz]]
- [[business-investment-model]]
- [[herbert-simon]]
- [[netlogo]]

## Topics covered (revision checklist)

- Full ODD walkthrough of the business investment model, second pass with more detail
- Utility function $U = (W + TP)(1-F)^T$ and how its two terms interact
- Why $P$ and $F$ being static, and profit/risk being uncorrelated, are strong assumptions
- Sensing-radius sweep: 1 → 2 → 5 improves mean wealth; 8 degrades it
- Network communication as an alternative sensing channel, and why it did not help here
- Paradox of choice; more information is not automatically better information
- Landscape structure: uniform random means local optima everywhere and no gradient
- Why mean profit plateaus and mean risk declines then flattens
- Adaptive behaviour defined: a decision made in response to sensed information, to
  improve state with respect to an objective
- Objectives as fitness (ecology) vs utility (economics) vs cost (minimisation)
- Optimising vs satisficing, and why real agents satisfice
- Satisficing thresholds: switch only when performance falls below an aspiration level
- Alternative objective functions and heterogeneous objectives across agents
- Academic integrity and the subject's generative-AI disclosure policy (DOIs required on
  every citation so fabricated references can be checked)

## Notable claims / results

- Mean final wealth rose with sensing radius up to about 5 and then fell at radius 8.
  Muñoz put the optimum "around 5" and offered the paradox of choice as an explanation
  while stating it was his hypothesis, not a tested result.
- A fully connected communication network did not beat the radius-1 baseline. The
  landscape is uniformly random, so global information carries no directional signal.
- The first simulated year does most of the work: on a uniform random landscape each
  neighbouring patch has roughly a 50% chance of being better, so the first move almost
  always improves both profit and risk.
- Agents become risk-averse and stagnate late in the run because $(1-F)^T$ weights the
  survival term more heavily as the remaining horizon shortens.
- Greedy strategies tend to be suboptimal; satisficing agents, being willing to move
  sideways, often end up closer to the optimum.
- Every choice in the model is evaluated deterministically; the only stochastic elements
  are the initial landscape, the update order, and whether a business fails on a tick.

## Connections

- [[w05a-sensing]] — first half of the pair; introduces the model and the sensing taxonomy
- [[w01a-introduction]] — where optimisation and satisficing were first named
- [[w03a-analysing-models]] — the experimental discipline this live demo informally
  applies; a proper version of the radius sweep is a BehaviorSpace parameter sweep with
  replicates
- [[kennedy-2012-modelling-human-behaviour]] — what to put in an objective function when
  the agent is meant to be a person

A layered digest of this lecture is available at
[[materials/w05b-adaptation-and-objectives-digest]].
