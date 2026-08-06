---
title: Model Extension
type: concept
tags: [methodology, model-design, heuristic]
date: 2026-08-06
---

# Model Extension

Model extension is the design heuristic of starting from a basic model and incorporating
more structure and behaviour incrementally, rather than building the complicated version
from the outset. It was stated as the design lesson of the disease-spread lecture.

## How it works

The procedure is to build a minimal or [[null-model]] baseline, establish what it does, then
add one element at a time and observe what changes. The critique that identifies the next
element to add is the substance of the method — for the [[sir-model]] the class produced a
list by asking what is unrealistic:

- No death state, so mortality cannot be distinguished from recovery.
- Permanent immunity, so reinfection and waning immunity are impossible.
- Too few states for asymptomatic carriers or severity gradations.
- Well-mixed contact, which fails at realistic population sizes ([[contact-rate]]).
- No representation of interventions ([[epidemic-intervention]]).
- Parameters that are hard to ground empirically.

Each of these is a candidate extension, and each is also a candidate
[[research-question]] — which is how Assignment 1 is framed, as one added element motivated
by a policy or scientific question.

The discipline is adding one at a time. Adding everything simultaneously produces a model
whose behaviour cannot be attributed to any particular component, since the components
interact. This is the same reasoning as ablation in machine learning, and the same reasoning
that motivates preferring simple models generally: fewer elements means the driver of the
observed signal is identifiable.

## Why it matters

Extension is the practical form of the simplicity principle. "Prefer simple models" is not
an instruction to stop at the toy version; it is an instruction about the order of
construction. It also keeps the model tied to its purpose, since each addition has to be
justified by a question rather than by realism for its own sake — the assignment briefing
is explicit that comprehensiveness is not the target ([[w02a-describing-models]]).

## Relationships

- [[null-model]] — the baseline extensions start from
- [[sir-model]] — the model being extended, and the source of the critique list
- [[occams-razor]] — the justification for preferring the smaller model
- [[modelling-cycle]] — extension is iteration through steps 2–5
- [[research-question]] — each extension should answer one

## Sources

- [[w02b-modelling-disease-spread]] — the summary slide's design heuristic, and the
  discussion identifying SIR's weaknesses as extension candidates.
- [[w02a-describing-models]] — the Assignment 1 framing of one extension motivated by a
  research question.
