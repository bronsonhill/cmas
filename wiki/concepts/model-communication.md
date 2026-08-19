---
title: Model Communication
type: concept
tags: [methodology, communication]
date: 2026-08-01
---

# Model Communication

Model communication is the final step of the [[modelling-cycle]]: conveying what the model
shows, and why it matters, to the stakeholders who need it.

## How it works

Once a model has been refined to the point where its behaviour gives genuine insight into
the real system, that insight has to reach someone. Stakeholders may include the lecturer,
colleagues, a funding agency, a policymaker, or a client — and most of them are not
modellers.

Two distinct communication moments matter:

- **During design.** A plain-language description of the model (step 3 of the cycle, see
  [[model-structure]]) can be handed to a domain expert — a zoologist, a botanist, an
  epidemiologist — who can judge whether the mechanisms are plausible even though they
  cannot read the code. This is the cheapest available check on structural error, and it
  depends on the description being written for a non-programmer.
- **After analysis.** Explaining what the model found and what should be done about it.
  Modelling is a multidisciplinary activity — practitioners work with people from health,
  transport, ecology — and the questions are usually real-world questions whose audience
  extends to the public and to politicians.

This is why the subject makes communication an explicit emphasis rather than an
afterthought, and why it is assessed: Project 2 includes a presentation and defence, and
reports must explain *why* choices were made, not just what they were.

## Why it matters

A model that cannot be explained cannot be acted on, and cannot be checked. The COVID
scenario modelling ([[covid-19-abm-australia]]) shaped national policy only because its
results were communicated in a form decision-makers could use.

## Relationships

- [[modelling-cycle]] — step 6
- [[model-structure]] — the plain-language outline that enables expert review
- [[covid-19-abm-australia]] — modelling communicated into policy
- [[research-question]] — a clear question makes for a communicable answer
- [[odd-protocol]] — the standardised template for the plain-language description
- [[reproducibility]] — why publishing code is not a substitute

## Sources

- [[w01b-modelling-cycle]] — the sixth step, with stakeholder management and the
  multidisciplinary argument for plain-language description.
- [[w02a-describing-models]] — the ODD protocol as the standard form; the argument that
  code cannot be handed to a non-programming multidisciplinary audience.
- [[a1-project-specification]] — names the audience explicitly (technical but
  non-specialist) and allocates marks to it as criterion C5.
- [[grimm-2020-odd-second-update]] — why ODDs fail as communication in practice: length,
  descriptions of the modeller's mental model rather than the program, and no route from the
  description to the code.
