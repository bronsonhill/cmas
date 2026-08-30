---
title: Optimisation
type: concept
tags: [methodology, decision-making]
date: 2026-08-01
---

# Optimisation

Optimisation is the search for the **best possible** solution to a problem, given an
objective and a set of constraints.

## How it works

In a modelling context optimisation appears at two distinct levels:

- **Within the model** — agents may be represented as optimisers, choosing the action that
  maximises some payoff. Contrast [[satisficing]], where agents settle for a good-enough
  option instead. The [[business-investment-model]] is the subject's worked case: agents
  enumerate every opportunity within their sensing radius, evaluate an
  [[objective-function|objective function]] for each, and take the maximum. Note the
  scope — the option set is bounded by what the agent can see, so this is optimisation
  over a local neighbourhood, not over the model.
- **On the model** — tuning the model itself: hyperparameter optimisation, calibration
  against observed data, and architecture/structure selection. This is the week 10–12
  material and is where the [[modelling-cycle]] meets formal search.

Applied to real systems, the pipeline is: take a real-world scenario, build a model that
yields insight, identify what can be changed, then search for changes that improve the
outcome. Traffic flow on a highway is the standard example — model it, find the levers,
evaluate interventions.

One caution the Week 5 lectures repeat: the goal in agent-based modelling is not to
optimise the performance of the *system*. Optimisation inside a model is a claim about how
agents behave, and it is a strong one — see [[bounded-rationality]].

## Why it matters

Modelling and optimisation are complementary: a model tells you what a system does, and
optimisation tells you what to do about it. Producing actionable answers — not just
descriptions — is what makes simulation useful to policy and design.

## Relationships

- [[satisficing]] — the contrasting decision criterion
- [[modelling-cycle]] — calibration and tuning as part of model development
- [[agent-based-model]] — the models being optimised, and the agents doing the optimising
- [[search-strategy]] — searching as a concrete optimisation problem

## Sources

- [[w01a-introduction]] — the lecturer's own research area; introduced alongside
  satisficing and listed as weeks 10–12 content.
- [[w05b-adaptation-and-objectives]] — optimising agents in the business investment model,
  why real agents cannot optimise, and why greedy strategies tend to be suboptimal.
