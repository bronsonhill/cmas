---
title: Model
type: concept
tags: [foundations, definitions]
date: 2026-08-01
---

# Model

A model is a **purposeful representation of some real system** — not just a
representation *of* something, but a representation *for* something. The purpose is part
of the definition, not an afterthought.

## How it works

Every model discards most of the real system. What makes a discard legitimate is the
model's purpose: the question you are trying to answer determines which features must be
represented and which can be ignored.

A disease-transmission model illustrates this cleanly. Does it need to represent how many
items a person buys at the supermarket? No — that has no bearing on transmission. Does it
need to represent how many people live in a household? Yes — household size shapes contact
structure, which is exactly the mechanism being modelled.

This cuts against a common instinct. The goal is not the most detailed or most complex
model; it is the simplest model that answers the question. Extra detail costs effort,
compute, and interpretability while often adding nothing.

Models come in several forms:

- **Physical** — a scale model, e.g. the Oroville Dam spillway model, built to locate
  points of failure rather than to reproduce flow exactly.
- **Visual or verbal description** — a diagram or written account of how a system works.
- **Mathematical equations** — e.g. the Navier–Stokes equations describing fluid motion.
- **Computer program** — the form this subject is concerned with, and the basis of a
  [[simulation]].

## Why it matters

"Purposeful" is the criterion by which modelling decisions are justified and defended.
When designing an [[agent-based-model]], every choice about which agent attributes,
behaviours and environmental features to include should trace back to the research
question. It is also the standard by which a model is assessed — a model is not "right"
or "wrong" in the abstract, only adequate or inadequate for its purpose.

## Relationships

- [[simulation]] — a computational implementation of a model, run over time
- [[agent-based-model]] — a particular kind of simulation model
- [[complex-system]] — the class of systems this subject models
- [[modelling-cycle]] — the iterative process by which models are built and refined

## Sources

- [[w01a-introduction]] — introduces the definition and the "purposeful" qualifier, with
  the disease-model and Oroville Dam examples.
