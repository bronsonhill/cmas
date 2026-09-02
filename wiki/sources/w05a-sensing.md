---
title: "Week 5a: Modelling Agent Behaviour — Sensing"
type: source
source_type: lecture
link: https://canvas.lms.unimelb.edu.au/courses/239814
tags: [comp90083, week-05, lecture, agent-behaviour, sensing, odd, netlogo]
date: 2026-08-30
---

# Week 5a: Modelling Agent Behaviour — Sensing

## Overview

The first Week 5 lecture, delivered by [[andres-munoz]], opens the run of lectures on
*modelling agent behaviour*. Weeks 1–3 gave the modelling cycle, the [[odd-protocol|ODD]]
description template, and the analysis machinery; Week 4 established what a
[[complex-system]] is and why local rules are worth simulating. Week 5 goes inside the
agent and asks what the rules themselves should look like — starting with the input side,
[[agent-sensing|sensing]].

The lecture is structured around the ODD **design concepts**, which it treats as a
checklist rather than a formality. Three are recapped from earlier weeks (basic
principles, [[emergence]], observation) and seven are named as the vocabulary for the
rest of the block: sensing, [[adaptive-behaviour|adaptation]],
[[objective-function|objectives]], [[agent-learning|learning]],
[[agent-prediction|prediction]], [[agent-interaction|interaction]], and
[[collectives]], with [[stochasticity]] alongside them. Muñoz drew one distinction
explicitly and flagged it as exam material: **adaptation happens within a simulation run,
learning happens across runs**. An evacuation model where agents react to a blocked exit
mid-run is adaptation; one where agents carry knowledge of the exits from drill to drill
is learning.

Sensing itself is broken into three questions — *what* state variables an agent uses,
*which* entities it can obtain them from, and *how* the information arrives, perfectly or
with error and bias. The "what" is organised by scope: global variables (interest rates,
weather — no spatial variation), local environmental variables (a NetLogo patch's
elevation or resources), agent variables (own or other agents' wealth, bearing, type),
and model parameters (the sliders on the Interface tab, the knobs BehaviorSpace sweeps).
The "how" is the point the lecture keeps returning to: agents in real systems have
[[imperfect-information|partial and imperfect information]] — bounded sensing distance,
access to only a subset of other agents, only some variables, and errors that may be
random noise or consistent bias. Muñoz worked the whole taxonomy through a house-hunting
example: interest rates as a global variable, school catchments and flood risk as local
environmental variables, other bidders' apparent seriousness at an inspection as a noisy
reading of another agent's state.

The [[agent-neighbourhood|neighbourhood]] is the formal answer to "which entities". Two
constructions are offered: a **radius** (or grid positions), and a **network**, where an
agent communicates with a nominated set of others who need not be spatially close. The
real-estate agent who tips you off about an off-market sale is a network neighbour; the
neighbours you chat to about the street are a radius neighbourhood.

The back half introduces the running example for the rest of the week, the
[[business-investment-model]] — investor agents on a NetLogo patch grid of business
opportunities, each opportunity carrying an annual profit $P$ and an annual failure risk
$F$, with agents maximising a utility that trades the two off over a 25-year horizon. The
lecture presents it as a full ODD description and then demos it, deferring the
experiments to Week 5b. One behaviour is previewed: agents grow *more* risk-averse as the
run proceeds, because failure is catastrophic (wealth resets to zero) and there is no
time left to recover.

## Key concepts

- [[agent-sensing]]
- [[imperfect-information]]
- [[agent-neighbourhood]]
- [[adaptive-behaviour]]
- [[objective-function]]
- [[agent-learning]]
- [[agent-prediction]]
- [[agent-interaction]]
- [[collectives]]
- [[odd-protocol]]

## Key entities

- [[andres-munoz]]
- [[business-investment-model]]
- [[netlogo]]

## Topics covered (revision checklist)

- ODD design concepts recap: basic principles, emergence, observation
- Design concepts governing agent behaviour: sensing, adaptation, objectives, learning,
  prediction, interaction, collectives, stochasticity
- Adaptation (within a run) vs learning (across runs) — flagged as an exam distinction
- Reinforcement learning framed against these concepts: reward as a utility signal
- The three sensing sub-questions: what information, from which entities, how obtained
- State variable scope: global, local environmental, agent, model parameters
- Sources of imperfection: limited range, limited set of agents, limited variables,
  random error, systematic bias
- Neighbourhood types: radius/grid vs network
- Business investment model as a worked ODD: purpose, entities, scheduling
  (repositioning then accounting), design concepts, initialisation, submodels
- Utility function $U = (W + TP)(1-F)^T$
- Warm-up revision from Week 4: what emergence is (and is not — self-similarity across
  scales is fractal structure, not emergence); self-organisation examples (zebra stripes,
  synchronised clapping, traffic jams) vs centrally designed ones (car assembly line,
  supermarket shelf layout); generalising the count of possible CA rules beyond binary
- Predator-prey recap: NetLogo Wolf Sheep Predation vs the Week 4 CA version, and why
  the CA version cannot grow exponentially

## Notable claims / results

- Adaptation is a within-simulation response; learning carries information across
  simulations. Muñoz said explicitly that this distinction appears in the exam.
- For a CA with $S$ states and $N$ cells in the neighbourhood, the number of possible
  rule tables is $S^{S^N}$ — the binary elementary case $2^{2^3} = 256$ is the smallest
  instance, and three states with three neighbours already gives $3^{27} \approx 7.6
  \times 10^{12}$. See [[cellular-automaton]].
- Sensing is the design concept that ties an ABM to reality: real decision-makers act on
  local, partial, noisy information, and an ABM is a framework for evaluating what that
  imperfection does to system behaviour.
- Randomising the update order means wealthier agents get no first-mover advantage in the
  business investment model — a [[scheduling]] decision with substantive consequences.
- In the NetLogo Wolf Sheep Predation model without grass, sheep grow exponentially
  because nothing starves them; only the wolves are resource-limited. Adding grass as a
  consumable resource restores the coupled oscillations seen in the Week 4 cellular
  automaton version, where the fixed grid already bounded the resource.

## Connections

- [[w05b-adaptation-and-objectives]] — the second half of the same lecture pair; runs the
  sensing-radius and network experiments on this model
- [[w02a-describing-models]] — where the ODD protocol and its design concepts were
  introduced
- [[w04b-2d-cellular-automata]] — the predator-prey CA and rule-counting recapped here
- [[kennedy-2012-modelling-human-behaviour]] — the prescribed reading on what should go
  *inside* the adaptation rule when the agent is a person

A layered digest of this lecture is available at [[materials/w05a-sensing-digest]].
