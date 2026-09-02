---
title: Soar
type: entity
entity_type: software
tags: [cognition, ai, agent-behaviour]
date: 2026-08-30
---

# Soar

An artificial-intelligence system and [[cognitive-architecture]] originally built to match
human performance on problem-solving tasks at a symbolic level of granularity. It is the
basis of Newell's proposal for Unified Theories of Cognition (1990).

## Key facts

- As an AI system its goal is to *meet or exceed* human performance across a wide range of
  tasks — not to reproduce human error.
- Maintains an internal representation of the world, always works towards a goal, and
  exposes internal state variables, which makes it readable as a
  [[bdi-architecture|BDI]] implementation.
- A Soar model is a collection of text rules over environmental and internal variables;
  firing a rule changes internal state or acts on the environment.
- Long history of modelling human behaviour framed as problem solving, in research and
  commercial settings, including connections to games.
- Free, with an active community of 40–60 members meeting annually, plus a Java port
  (jSoar).

## Relevance

Soar and [[act-r]] are the two cognitive architectures Kennedy says have wide acceptance
and active communities. They mark the high-fidelity, high-cost end of the options for
driving agent behaviour — appropriate when the model's question *is* about individual
cognition, and overkill when it is about collective outcomes.

## Sources

- [[kennedy-2012-modelling-human-behaviour]] — description, BDI reading, and comparison
  with ACT-R
