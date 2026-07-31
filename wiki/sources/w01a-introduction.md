---
title: "Week 1 (Tuesday): Introduction"
type: source
source_type: lecture
link: https://canvas.lms.unimelb.edu.au/courses/239814
tags: [comp90083, week-01, lecture, introduction, definitions]
date: 2026-08-01
---

# Week 1 (Tuesday): Introduction

## Overview

The opening lecture of COMP90083 Computational Modelling and Simulation, delivered by
[[andres-munoz]]. It does two jobs: it sets out how the subject runs (staff, structure,
assessment, tools, AI policy), and it establishes the three definitions the rest of the
subject is built on — [[model]], [[simulation]], and [[agent-based-model]].

The conceptual thread is the idea of a [[complex-system]]: a system made of many
individual parts whose *local* interactions produce collective patterns nobody
programmed in. Two motivating examples anchor this. The first is a starling murmuration —
each bird perceives only its immediate neighbours, yet the flock as a whole shifts and
morphs as a single body. The lecturer then shows the NetLogo Flocking model, in which
[[boids]] follow only local separation, alignment and vision rules, and clustering and
common heading appear as [[emergence|emergent]] properties rather than as programmed
goals. The second is COVID-19: Australian lockdown policy was informed by [[agent-based-model|ABM]]
scenario modelling, where the object of interest is the network of individual
interactions (households, workplaces, supermarkets) rather than an aggregate curve.

On definitions, the lecture is careful about one point in particular: a model is a
representation *for a purpose*, not merely a representation *of* something. Purpose is
what licenses simplification — in a disease-transmission model, household size matters
because it shapes contact patterns, while shopping baskets do not. The instinct to build
the most detailed model possible is treated as a beginner's error; the target is the
simplest model that answers the question. Model types range across physical scale models
(the Oroville Dam spillway model, built only to locate failure points), verbal or visual
descriptions, mathematical equations (Navier–Stokes in fluid dynamics), and computer
programs — the last being this subject's concern.

Practically, the subject uses [[netlogo]] as its main modelling language (no prior
knowledge assumed) with [[mesa]] in Python as an optional path for larger models. Prior
coding skill is deliberately not assumed; the friction is expected to be NetLogo's
unfamiliarity rather than its difficulty.

## Key concepts

- [[model]]
- [[simulation]]
- [[agent-based-model]]
- [[complex-system]]
- [[emergence]]
- [[flocking]]
- [[modelling-cycle]]
- [[tipping-point]]
- [[optimisation]]
- [[satisficing]]
- [[stochasticity]]

## Key entities

- [[andres-munoz]] — subject coordinator and lecturer
- [[netlogo]] — primary modelling environment
- [[mesa]] — optional Python ABM framework
- [[boids]] — the flocking model shown in class
- [[wilensky-and-rand]] — set textbook
- [[covid-19-abm-australia]] — the policy modelling case study

## Topics covered (revision checklist)

- Definition of a model: a *purposeful* representation of a real system — "not just *of*
  something, but *for* something"
- Types of model: physical, visual/verbal description, mathematical equations, computer
  program
- Purpose determines the level of abstraction and what may be left out
- Definition of a simulation: an approximate imitation of the *operation* of a process or
  system, i.e. its behaviour over time; usually computational, occasionally physical
- Application domains of simulation: engineering, entertainment, education, science,
  decision-making
- Definition of an agent-based model: a simulation model focused on the actions and
  interactions of autonomous agents
- Complex systems: many parts, local interaction, emergent collective properties
- Agents perceive only local information (birds in a flock, people in a crowd)
- Flocking / [[boids]] rules: separation, alignment, vision radius, speed
- Emergent patterns: clustering, common heading — arising without any global rule
- Tipping points / phase transitions in parameter space
- Three question types ABMs answer: understand, control, design
- History of ABM: conceptual foundations 1940s–1970s; cheap computing 1980s–1990s (Boids
  1987); modelling languages and libraries 2000s–2010s; million-agent models today
- Current application fields: biology, economics, ecology, epidemiology, finance and
  marketing, social science, transportation, military
- Contrast with machine learning: rules specified from theory, not learned from training data
- The [[modelling-cycle]]: hypothesis → build → verify against expected patterns → refine
- ABMs are stochastic — requires replication and sensitivity analysis
- Subject structure: intro to ABM (wk 1–3, incl. ODD protocol, visualisation), designing
  ABMs (wk 4–9, incl. agent behaviour, game theory, networks), applying ABMs (wk 10–12,
  incl. pattern-oriented modelling, calibration, sensitivity/uncertainty, optimisation)
- [[optimisation]] vs [[satisficing]]
- Assessment: Project 1 (20%, individual, extend a model, released wk 2 / due wk 5);
  Project 2 (40%, pairs, own system — proposal wk 9, demonstration and defence wk 11,
  ~3000-word report + code wk 12); final exam (40%, hurdle 20/40)
- Tools: NetLogo (assumed unknown), Python + Mesa (optional, self-directed)
- GenAI policy: permitted for brainstorming, source identification, editing; not for
  paraphrasing, direct quotation, or code generation; declaration required; secure
  assessment via interview (Project 1) and mandatory defence (Project 2)

## Notable claims / results

- A model is a representation of a system **for a purpose**; the purpose determines what
  is included and excluded.
- A simulation is a computational implementation of a model that reproduces how a system
  behaves over time.
- Agent-based models are distinguished by focusing on individual autonomous agents and
  their *interactions* — agents in isolation are not the object of interest.
- Emergent collective behaviour can arise from purely local rules with no global
  coordination and no agent having global information.
- In the Australian COVID-19 scenario modelling, 70% compliance with physical distancing
  still produced sustained epidemic growth; 80% compliance flattened the curve; 90%
  produced sharp decline ([[covid-19-abm-australia]]). These simulations directly
  informed lockdown policy.
- The Oroville Dam scale model was built to identify points of failure, not to reproduce
  flow precisely — an illustration of purpose constraining fidelity and cost.
- Boids-style flocking models date to around 1987, coinciding with the arrival of cheap
  computing power.
- Modern frameworks such as [[mesa]] make models with millions of agents tractable,
  enabling city- and country-scale simulation.

## Connections

- The definitional chain [[model]] → [[simulation]] → [[agent-based-model]] is the
  narrowing hierarchy the whole subject sits inside.
- [[complex-system]] and [[emergence]] are the motivation for choosing ABM over
  aggregate/equation-based approaches.
- [[flocking]] and [[boids]] are the canonical worked demonstration of emergence.
- [[modelling-cycle]] is developed further in weeks 1–3, alongside the ODD protocol.
- [[optimisation]] and [[satisficing]] return in weeks 4–9 (agent decision-making) and
  week 12 (model-level optimisation).
- Required follow-up reading: [[wilensky-and-rand]], Chapter 1 (first half).
