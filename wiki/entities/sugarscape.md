---
title: Sugarscape
type: entity
entity_type: model
tags: [abm, social-simulation, emergence]
date: 2026-08-19
---

# Sugarscape

An agent-based model of an artificial society built by [[joshua-epstein]] and Robert Axtell,
published in *Growing Artificial Societies* (1996). Agents with vision, metabolism and a
lifespan move over a grid of renewable "sugar", and social regularities — wealth
distributions, migration, trade, epidemics — emerge from those local rules.

## Key facts

- The agents follow simple local rules; none of the aggregate regularities is programmed in
  ([[emergence]]).
- Sugarscape is the reference implementation of [[generative-explanation]]: the model grows
  a macroscopic pattern from agent behaviour.
- Epstein and colleagues drew a "computational analogy" between Sugarscape and the real
  landscape of the Kayenta Anasazi, which led to the data-driven Long House Valley
  reconstruction (PNAS, 2002).
- Frequently rebuilt as a teaching model; implementations ship with several ABM platforms
  including [[netlogo]] and [[mesa]].

## Relevance

Alongside [[schelling-segregation-model]] and [[boids]], it is one of the canonical
demonstrations that simple agent rules produce structured collective behaviour, and it is the
one that extends the claim to a whole artificial economy rather than a single phenomenon.

## Sources

- [[epstein-2008-why-model]] — cited as the author's own example of formal analogy and as the
  basis for the Anasazi work.
