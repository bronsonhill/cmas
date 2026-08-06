---
title: COVID-19 ABM (Australia)
type: entity
entity_type: model
tags: [epidemiology, policy, abm, case-study]
date: 2026-08-01
---

# COVID-19 ABM (Australia)

An agent-based scenario model of COVID-19 transmission in Australia, developed at the
University of Sydney and used to inform the national physical-distancing and lockdown
response in early 2020.

## Key facts

- Modelled physical-distancing compliance as the key policy lever, comparing scenarios at
  70%, 80% and 90% compliance from a fixed intervention date (~day 50).
- Results: at **70%** compliance active cases continued to grow steeply; at **80%** the
  curve flattened and declined slowly; at **90%** cases fell sharply.
- The distance between the 70% and 80% curves is a [[tipping-point]] in the policy
  parameter — the difference is categorical, not proportional.
- The results were published widely (chart via ABC News Story Lab, March 2020) and fed
  directly into government decisions on lockdown.
- Slide reference: `https://ab.co/3iJ9AWA`.

## Relevance to CMAS

This is the subject's headline case for ABM as a decision-making instrument rather than an
academic exercise: a simulation of individual interactions producing a threshold that
shaped real policy affecting the whole population. It also illustrates why
[[model|purpose]] governs model detail — household composition matters to transmission,
shopping baskets do not.

## Sources

- [[w01a-introduction]] — presented as the motivating policy example for agent-based
  modelling.
- [[w02b-modelling-disease-spread]] — the [[doherty-institute]] context in which this
  class of model was built, and the [[sir-model]] it scales up from.
