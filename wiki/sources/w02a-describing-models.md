---
title: "Week 2a: Describing Models"
type: source
source_type: lecture
link: https://canvas.lms.unimelb.edu.au/courses/239814
tags: [comp90083, week-02, lecture, odd-protocol, model-description, reproducibility]
date: 2026-08-06
---

# Week 2a: Describing Models

## Overview

The first Week 2 lecture, delivered by [[andres-munoz]]. Week 1 ended at step 3 of the
[[modelling-cycle]] — choose the model structure — and this lecture supplies the vehicle
for doing that step properly: the [[odd-protocol]], a standardised plain-language template
for describing agent-based models, formulated by [[volker-grimm]] in 2006 and revised in
2010 and 2020. The stated objectives are to describe ODD, write one for an existing model,
and write one for a new model.

The argument for a protocol is made on three grounds. Writing the structure down forces
you to confront every part of the model rather than leaving parts vague; it makes the model
communicable to collaborators who are not programmers; and it becomes the specification you
implement against. The lecturer leaned hard on the multidisciplinary case: a computing
student working with epidemiologists, ecologists or clinicians cannot hand them a block of
Python and expect understanding, so the description has to survive translation out of code.
Two further motivations sit underneath — **model interpretation**, since making sense of
simulation output requires knowing the mechanistic design, assumptions and data that
produced it, and **model reproducibility**, which the lecture connected to the replication
crisis in the medical literature and to the poorly reported experiments common in
optimisation research ([[reproducibility]]).

The bulk of the lecture walks the ODD sections in order, using the Week 1 truffle-foraging
model as the running example ([[truffle-foraging-model-design]]). *Purpose* answers what
the model is **of** and what it is **for**, and acts as the filter deciding what goes in
and what stays out. *Entities, state variables and scales* names the agents and the
environment, the attributes characterising them, and the [[model-scales]] — temporal extent
and resolution, whether the model is spatially explicit, and whether space is continuous or
discretised. The lecturer pressed the scale question concretely: an afternoon foraging
excursion modelled in one-second steps is wrong, because the agent cannot displace
meaningfully in a second, so resolution has to be chosen against agent movement and map
size. *Process overview and scheduling* covers agent behaviours, how state and environment
change, and the ordered sequence of actions — [[scheduling]] — for which pseudo-code is
recommended. *Design concepts* is a list of ten (basic principles, emergence, adaptation,
objectives, learning/prediction, sensing, interaction, stochasticity, collectives,
observation) that later lectures unpack. *Details* holds [[initial-conditions]], input data,
and submodels.

The lecture opened with three quiz questions restating Week 1 material: simple models are
preferred because they are easier to implement and understand and quicker to run — not
because detail is unimportant, but because with fewer interacting components you can tell
which one drives the signal, the same reasoning as ablation in machine learning. The
[[modelling-cycle]] is iterative because the question may need reformulating and because
implementations contain errors or fail to produce the behaviour of interest. And the
[[research-question]] comes first because it bounds the scope; without it the model
accumulates elements indefinitely, which the lecturer named as scope creep.

The first quarter of the session was spent on the Assignment 1 briefing: extend the
supplied SIR disease-transmission model with one additional element motivated by a policy
or scientific question, and report in about 1200 words on a provided LaTeX template.
Assessment weights the problem framing, the modelling choices, evaluation of assumptions
and limitations, the experiments, and the communication — not realism or comprehensiveness.
Generative AI is permitted but the lecturer warned that uncritically following its output
produces a report that teaches the author nothing.

## Key concepts

- [[odd-protocol]]
- [[model-scales]]
- [[scheduling]]
- [[initial-conditions]]
- [[reproducibility]]
- [[model-structure]] (the ODD is its formalisation)
- [[model-communication]]
- [[research-question]]
- [[modelling-cycle]]
- [[stochasticity]], [[emergence]], [[agent-sensing]] (named as ODD design concepts)

## Key entities

- [[andres-munoz]] — lecturer
- [[volker-grimm]] — formulated the ODD protocol
- [[grimm-odd-2010]] — the assigned reading describing the protocol
- [[netlogo]] — the implementation environment assignments require

## Topics covered (revision checklist)

- Assignment 1 briefing: extend the supplied SIR model, ~1200 words (~5 pages) on the
  provided LaTeX template, five weeks to complete
  - Assessed on: problem framing, modelling choices, assumptions and limitations,
    experiments, communication
  - Realism and comprehensiveness are explicitly *not* the target
  - A stated research question is required; pre-filled template content must be left intact
  - Over-length reports lose marks, because marking is done by humans
  - Generative AI permitted, but critical evaluation of its output is the student's job
- Quiz recap: simple models are easier to implement and understand, and quicker to run
  - Fewer components means you can attribute the signal to a mechanism — cf. ablation
  - Minor details are excluded because the target is the bigger structural pattern
- The modelling cycle is iterative because the question may be wrong, the implementation
  may contain errors, and the model may not produce the behaviour of interest
- The research question comes first because it defines scope and prevents scope creep
- ODD = **O**verview, **D**esign concepts, **D**etails; Grimm 2006, revised 2010 and 2020
- Why a standard: standards are shared rules enabling interoperation (the USB analogy —
  connector shape, electrical signals, handshaking protocol)
- Rube Goldberg machine as the anti-pattern: a contraption too complicated for its purpose
- Plain-language description forces precision that verbal discussion leaves ambiguous
- Reproducibility crisis: a large share of medical results failed replication; in
  optimisation research, algorithms are commonly tested poorly, prompting lab protocols
- Why not just publish the code: code length, coding style, and above all a
  multidisciplinary audience that does not read Python
- ODD is not universal, but is widely used in ecology and social science
- **Overview → Purpose:** what is the model *of*, what is the model *for*; serves as the
  guide to inclusion and omission
- **Overview → Entities, state variables and scales:**
  - Entities: agents and the environment (local and global)
  - State variables: attributes characterising agents, environmental units and globals
    (foraging example — carrying capacity, stamina; moisture, temperature, light)
  - Temporal extent (how long it runs) and temporal resolution (continuous, or discrete
    steps of a given size); resolution must match agent displacement and map size
  - Spatial scale: whether the model is spatially explicit, and whether space is continuous
    or discretised into patches
  - Non-spatial examples raised: stock market trading, social networks / information spread
- **Overview → Process overview and scheduling:** agent behaviours, how state and
  environment change, the ordered sequence of actions; pseudo-code as a representation
- **Design concepts** (list only, unpacked in later lectures): basic principles, emergence,
  adaptation, objectives, learning/prediction, sensing, interaction, stochasticity,
  collectives, observation
- **Details → Initialisation:** the model state at $t = 0$; some models' long-term
  behaviour depends on it, others converge regardless; needed for reproduction
- **Details → Input data:** external data driving the model as it runs (temperature series,
  tide calendars, commodity prices); many models are self-contained and need none
- **Details → Submodels:** equations, rules or algorithms for processes too detailed to
  describe inline
- Summary: documentation serves clear thinking, communication, and implementation blueprint

## Notable claims / results

- The ODD protocol was formulated by Volker Grimm in 2006 and revised in 2010 and 2020;
  it is a framework for describing agent-based models in plain language.
- ODD occupies the transition from step 2 of the modelling cycle (assemble hypotheses) to
  step 3 (choose model structure) — it is the mechanism for making brainstorming formal.
- The purpose statement is the filter for model content: what needs to be included and what
  can be omitted follows from it.
- Temporal resolution is not a free choice — it is constrained by how far an agent moves
  per step and by the size of the modelled space.
- Providing code is not a substitute for a plain-language description, primarily because
  the audience for a model is often multidisciplinary and non-programming.
- Reproducibility failures in medicine came from gaps in the description of the process,
  not from the results being unavailable — which is precisely what a protocol addresses.
- Specifying initial conditions matters because agent-based models are dynamical systems;
  some converge independently of them and some do not.

## Connections

- Directly continues [[w01b-modelling-cycle]], which ended by naming the ODD protocol as
  the Week 2 topic; the truffle-foraging example is carried over.
- [[model-structure]] is the informal version of what [[odd-protocol]] formalises.
- [[w02b-modelling-disease-spread]] applies the Overview section of ODD to a new model in
  the zombie-apocalypse design exercise, and supplies the SIR model Assignment 1 extends.
- The ten ODD design concepts are forward references — emergence, adaptation, sensing,
  interaction, stochasticity and observation each get their own treatment later in the
  subject.
