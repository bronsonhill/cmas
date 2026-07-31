---
title: Counterfactual
type: concept
tags: [abm, analysis, methodology]
date: 2026-08-01
---

# Counterfactual

A counterfactual is a scenario run in which some feature of the system is altered or
removed, in order to see how the outcome would differ — a "what if things had been
otherwise?" experiment.

## How it works

Once a [[simulation]] exists, its parameters and structure are yours to change, including
in ways the real world would never permit. In the agricultural pest ABM discussed in
lectures, one can ask: what if there were no pests at all? Would the crops then grow
without limit, or does something else constrain them? What if there were no villages?

Each such run is an alternate world, and the *difference* between it and the baseline is
the causal contribution of the thing you removed. This is a form of inference that
observation alone cannot supply, because the real system only ever ran one way.

Counterfactual runs are also how policy questions get answered: the COVID compliance
scenarios ([[covid-19-abm-australia]]) are counterfactuals — 70%, 80% and 90% compliance
are three worlds, only one of which happened.

Two cautions. Because these models are stochastic, a difference between two single runs is
not yet evidence — comparison must be across distributions (see [[stochasticity]]). And a
counterfactual is only as good as the model's mechanisms: removing pests tells you what
*the model* thinks happens, which is a claim about your assumptions as much as about the
world.

## Why it matters

Counterfactual experimentation is one of the strongest arguments for building an
[[agent-based-model]] at all. It is especially valuable in social science, where the ABM
lets behavioural interventions be tested on simulated people rather than real ones — an
ethical advantage as much as a practical one, letting you check whether an intervention is
likely to help before deploying it on a population.

## Relationships

- [[agent-based-model]] — the vehicle for counterfactual experiments
- [[covid-19-abm-australia]] — policy counterfactuals that informed real decisions
- [[stochasticity]] — why counterfactual comparisons need replication
- [[modelling-cycle]] — counterfactual runs belong to the analysis step

## Sources

- [[w01b-modelling-cycle]] — introduced via the pest ABM ("what if there were no pests?")
  and the ethical argument for simulated social experiments.
