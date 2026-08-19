---
title: ODD Protocol
type: concept
tags: [methodology, model-description, abm, odd]
date: 2026-08-06
---

# ODD Protocol

The ODD protocol — **O**verview, **D**esign concepts, **D**etails — is a standardised
plain-language template for describing agent-based models. It was formulated by
[[volker-grimm]] in 2006 and revised in 2010 and 2020. It is not universal, but it is
widely used in ecology and social science.

## How it works

ODD has seven sections in three groups.

**Overview**

1. **Purpose.** What is the model *of*, and what is the model *for*? Two distinct
   questions: the first names the system, the second names the question being answered.
   The purpose is the filter that decides what belongs in the model — a foraging model
   only needs soil moisture if the purpose makes moisture relevant.
2. **Entities, state variables and scales.** The entities are the agents and the
   environment, local and global. State variables are the attributes characterising them —
   a forager's carrying capacity and stamina, a patch's moisture and light level. Scales
   cover both time and space; see [[model-scales]].
3. **Process overview and scheduling.** What behaviours the agents exhibit, how their state
   and the environment change as a result, and the order in which those actions occur.
   Pseudo-code is a useful representation here. See [[scheduling]].

**Design concepts**

A checklist of ten agent-based modelling principles, each of which the description should
address: basic principles, [[emergence]], adaptation, objectives, learning/prediction,
sensing ([[agent-sensing]]), interaction, [[stochasticity]], collectives, and observation.
Observation means the data extracted from the model — which signals you intend to measure.

**Details**

5. **Initialisation.** The state of the model at $t = 0$. See [[initial-conditions]].
6. **Input data.** External data driving the model as it runs — a temperature series, a
   tide calendar, commodity prices. Many models are self-contained and require none.
7. **Submodels.** Processes complex enough to need separate treatment: equations, rules,
   algorithms, or an embedded machine-learning model. Submodels are often independent of
   each other.

## Why it matters

Writing the description down serves three purposes, and the third is easy to underrate:

- It forces you to confront every part of the model. Discussion tolerates ambiguity;
  writing does not.
- It communicates the model to people who cannot read your code. A modeller is often the
  only computing person on a team of epidemiologists, ecologists or clinicians, and
  handing them Python does not transfer understanding. See [[model-communication]].
- It is the specification you implement against, which bounds scope in the same way a
  software-engineering spec does.

Two further motivations sit underneath. **Interpretation**: making sense of simulation
output requires knowing the mechanistic design, assumptions and data that produced it, and
a written ODD gives you an expectation to compare results against. **Reproducibility**:
others need to be able to rebuild and verify the model — see [[reproducibility]].

The protocol also sits at a specific point in the [[modelling-cycle]], between step 2
(assemble hypotheses) and step 3 (choose model structure). It is the mechanism that turns
unstructured brainstorming into a formal representation.

## Relationships

- [[model-structure]] — the informal version of what ODD formalises
- [[model-scales]], [[scheduling]], [[initial-conditions]] — individual ODD sections
- [[reproducibility]], [[model-communication]] — the motivations
- [[modelling-cycle]] — ODD spans the step 2 → step 3 transition
- [[volker-grimm]], [[grimm-odd-2010]] — origin and assigned reading
- [[zombie-apocalypse-model-design]] — worked example of the Overview section
- [[truffle-foraging-model-design]] — the running example used to introduce it

## Sources

- [[w02a-describing-models]] — introduces the protocol, walks all seven sections using the
  truffle-foraging model, and argues for standardised description.
- [[w02b-modelling-disease-spread]] — applies the Overview section to the zombie apocalypse
  design exercise.
- [[a1-project-specification]] — required as the organising structure of the assignment
  report, for a technical but non-specialist audience.
