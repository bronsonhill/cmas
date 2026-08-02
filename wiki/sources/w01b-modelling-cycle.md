---
title: "Week 1b: A First Model & the Modelling Cycle"
type: source
source_type: lecture
link: https://canvas.lms.unimelb.edu.au/courses/239814
tags: [comp90083, week-01, lecture, modelling-cycle, model-design]
date: 2026-08-01
---

# Week 1b: A First Model & the Modelling Cycle

## Overview

The second Week 1 lecture, delivered by [[andres-munoz]]. It has three stated objectives:
restate the key definitions, walk through designing a model from scratch, and set out the
[[modelling-cycle]] as a methodology. Where [[w01a-introduction]] established *what* a
[[model]] is, this lecture is about *how you build one* — and its through-line is
[[abstraction]]: a model is necessarily simpler than the system it represents, and purpose
is what decides which simplifications are legitimate.

The definitional half is carried by four models of the Earth, each correct for a different
purpose. A **Mercator world map** ([[mercator-projection]]) represents landmass, altitude
and ocean depth well enough to locate yourself, at the cost of severe area distortion near
the poles — Greenland appears comparable in size to Africa. A **cut-away of the Earth's
interior** is explicitly labelled "not to scale": the crust is exaggerated because the
crust is where we live and mine, so the distortion serves the purpose. The
**geocentric-versus-heliocentric** pair ([[heliocentric-model]]) makes the sharpest point:
both were built for the same purpose — explaining planetary motion — but the geocentric
model needed epicycles, complicated inner orbits, to account for planets appearing to
reverse direction. Moving the Sun to the centre made that machinery vanish. This is
[[occams-razor]] in action, and the lecture's argument for simplicity is grounded here
rather than asserted.

The lecture then designs a model live: **what is an efficient strategy for foraging
mushrooms in a forest?** Students proposed strategies and the lecturer used them to force
out the modelling decisions — see [[truffle-foraging-model-design]] for the worked
reconstruction. The pivotal move was narrowing the question from "mushrooms" to
"truffles": truffles grow underground and don't cluster, which immediately invalidates a
greedy [[search-strategy]] and demands a smell-based [[agent-sensing]] mechanism with a
detection radius. A vaguer question would not have constrained the design at all. This is
the lecture's central pedagogical claim — that specificity in the research question is
what makes the rest of the design tractable.

The final section presents the six-step [[modelling-cycle]] (formulate the question,
assemble hypotheses, choose model structure, implement, analyse/test/revise, communicate),
with the caveat that the diagram's clean loop is misleading: any step can send you back to
any earlier one, including discovering at implementation time that the question itself was
wrong. Two steps get particular emphasis — formulating the question is named the hardest
part and the one students struggled with most last year, and communication is flagged as a
deliberate emphasis of the subject, because these are real-world questions whose audience
includes policymakers and domain experts, not just peers.

## Key concepts

- [[modelling-cycle]]
- [[abstraction]]
- [[occams-razor]]
- [[research-question]]
- [[model-structure]]
- [[search-strategy]]
- [[agent-sensing]]
- [[counterfactual]]
- [[model-communication]]
- [[pattern-oriented-modelling]]
- [[model]], [[simulation]], [[agent-based-model]] (revisited)

## Key entities

- [[andres-munoz]] — lecturer
- [[mercator-projection]] — worked example of purposeful distortion
- [[heliocentric-model]] — worked example of Occam's razor
- [[oroville-dam-model]] — physical scale model, revisited from Week 1a
- [[nasa-black-hole-simulation]] — worked example of simulation designed to guide instrumentation

## Topics covered (revision checklist)

- Restated definitions: model (purposeful representation), simulation (behaviour over
  time), agent-based model (autonomous agents and interactions)
- Models abstract away detail — they are **simpler** than the system they represent
- Model types: physical (maquettes), visual/verbal description (illustrations, mental
  maps), mathematical equations (differential equations, Navier–Stokes), computer programs
- Models of the Earth as purpose-relative representations:
  - Mercator map — landmass, altitude, ocean depth; area distortion at the poles
  - Earth interior cut-away — "not to scale"; crust exaggerated because it is what matters
  - Geocentric vs heliocentric — same purpose, different complexity; epicycles eliminated
- Occam's razor: prefer the simpler explanation when both account for the observations
- Physical simulation infrastructure (wind tunnels, dam scale models) is expensive and
  space-hungry; computational modelling is cheap enough to run on a laptop
- Simulation concerns *dynamics* — how the system changes over time; static models are of
  limited interest
- The NASA black-hole collision simulation: elements required (gravity, mass, initial
  conditions, 3D space), and its purpose — predicting emitted radiation so that sensors and
  instruments can be designed and calibrated to detect the real event
- ABMs permit counterfactual experiments ("what if there were no pests?", "no villages?")
- ABMs are heavily used in social science because they allow behavioural interventions to
  be tested without experimenting on real people — an ethical advantage
- Worked design exercise: efficient strategy for foraging mushrooms in a forest
  - Search strategies proposed: greedy, random, spiral, zigzag, cluster-based,
    multi-agent search
  - Greedy search requires clustering to work; truffles don't cluster, so it fails
  - Zero-information starting point: random start with a large step size
  - Sensing mechanism: the pig's sense of smell, with detection radius as a model variable
  - Multi-agent search covers more ground per unit time, at higher cost
  - Other proposed elements: topography, climate/moisture, leaf litter, proximity to trees,
    host-tree identification, a model of truffle spread, historical search data
- "Questions to ask yourself": what strategies exist, which is best, do we need a model at
  all, what is its purpose, what to include, what to leave out
- The six-step modelling cycle:
  1. **Formulate the question** — clear, specific, non-trivial, answerable by a model;
     defines scope and hardest step
  2. **Assemble hypotheses** for essential processes and structures — open-ended research
     and brainstorming, then filtering; start simple
  3. **Choose model structure** — scales, entities, state variables, processes, parameters;
     produce a written outline before code
  4. **Implement the model** — translate the written design into a runnable simulation;
     reveals the consequences of assumptions
  5. **Analyse, test and revise** — the most time-consuming step; often forces
     reformulation of the question
  6. **Communicate the model** — convey insight to stakeholders
- "Patterns!" appears twice on the cycle diagram: between hypotheses and structure, and
  between analysis and communication
- The cycle is not strictly sequential — any step can send you back to any other
- Plain-language model descriptions enable review by non-programmers (zoologists,
  botanists) in multidisciplinary teams
- Stakeholder management: lecturer, colleagues, funding agency, policymaker, clients
- Next week: the ODD protocol and infectious disease transmission models

## Notable claims / results

- Models are, by definition, **simpler** than the systems they represent; abstraction is
  not a defect but the mechanism by which a model becomes usable.
- A distortion is acceptable when it serves the purpose — the "not to scale" Earth
  cut-away exaggerates the crust precisely because the crust is the part of interest.
- The heliocentric model displaced the geocentric one not by explaining *more* but by
  explaining the same observations with far less machinery (no epicycles) — the lecture's
  concrete grounding for [[occams-razor]].
- Purpose can be instrumental rather than explanatory: the NASA black-hole simulation's
  value was in predicting what radiation to expect, so that detection instruments could be
  designed and calibrated.
- Narrowing "mushrooms" to "truffles" changed which search strategies were viable — greedy
  search depends on clustering, which truffles lack. Specificity in the question does real
  work in constraining the model.
- Starting simple is defended on practical grounds: a simple behaviour may be 2–3 lines of
  code, whereas implementing everything at once produces a mass of bugs.
- Formulating a clear research question is named the hardest step of the cycle, and the one
  students most struggled with in previous years' assignments.
- Pattern-oriented modelling aims to reproduce real-world *patterns* — cycles, spikes —
  rather than matching exact numerical values ([[pattern-oriented-modelling]]).

## Connections

- Directly extends [[w01a-introduction]]: same definitions, now with the design methodology
  and richer worked examples. The Oroville Dam model appears in both.
- [[modelling-cycle]] is substantially expanded by this source — Week 1a sketched a
  four-stage loop; this gives the canonical six steps.
- [[truffle-foraging-model-design]] is the worked example derived from this lecture.
- [[occams-razor]] and [[abstraction]] supply the justification for the simplicity
  principle asserted in Week 1a.
- [[pattern-oriented-modelling]] is named here but deferred to the end of the subject
  (weeks 10–12), alongside calibration.
- Forward reference: the ODD protocol and disease-transmission models in Week 2.
