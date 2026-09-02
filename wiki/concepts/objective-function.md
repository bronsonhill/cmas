---
title: Objective Function
type: concept
tags: [abm, agent-behaviour, odd, decision-making]
date: 2026-08-30
---

# Objective Function

An objective function is the criterion an agent uses to rank alternative actions. It goes
by different names by field — **fitness** in ecological models, **utility** in economic
ones, **cost** or **loss** when the quantity is minimised rather than maximised.

## How it works

The function maps a candidate action, or the state it would lead to, onto a scalar. The
agent's [[adaptive-behaviour|adaptation]] rule then either maximises it
([[optimisation]]) or accepts the first option clearing a threshold
([[satisficing]]).

The [[business-investment-model]] uses a two-term utility over a time horizon $T$:

$$U = (W + TP)(1 - F)^T$$

The first factor is projected wealth — current wealth $W$ plus $T$ years of annual profit
$P$. The second is the probability of surviving $T$ years given an annual failure
probability $F$. The terms are multiplied rather than optimised separately, which
conflates them deliberately: an opportunity is worth what it pays *times* the chance it
survives to pay it. The $(1-F)^T$ factor is also what makes the model's agents grow more
risk-averse as the run proceeds — with the horizon shortening there is no time left to
recover from a failure, so agents settle onto low-risk patches and stop moving.

Choosing the function is a substantive modelling decision, not a technicality. Suppose
opportunities in the same model could post *negative* profit. Agents could then plausibly
maximise profit and ignore risk entirely, or ignore wealth and profit and simply avoid
ruin. Each gives a different model, and each is defensible for a different research
question. Different subsets of agents can also carry different objective functions in the
same run — the standard way to introduce heterogeneous risk appetite into an ABM.

Kennedy ([[kennedy-2012-modelling-human-behaviour]]) is sceptical of multi-parameter
objective functions as models of people: available data does not validate humans as pure
optimisers. His cheaper alternative is a [[threshold-rule]], and his structural point is
that thresholds and comparisons are the same thing — comparing two functions is comparing
their difference against zero.

## Why it matters

Different objective functions produce different agent decisions and therefore different
model behaviour. Two ABMs with identical entities, environment and schedule can produce
opposite conclusions if the objective differs. It belongs in the ODD **objectives** design
concept ([[odd-protocol]]) and should be stated explicitly, with its units and horizon.

The related caution from the lectures: the goal in agent-based modelling is not to
optimise the *system's* performance. The objective function belongs to the agents; the
modeller's interest is in what their pursuit of it produces collectively.

## Relationships

- [[adaptive-behaviour]] — the rule that consumes the objective
- [[optimisation]] / [[satisficing]] — maximise it, or clear a threshold on it
- [[agent-prediction]] — a horizon-based objective requires a prediction of future state
- [[threshold-rule]] — the cheapest form of an objective
- [[business-investment-model]]

## Sources

- [[w05a-sensing]] — objectives as an ODD design concept; the utility function introduced
- [[w05b-adaptation-and-objectives]] — fitness/utility/cost naming, alternative and
  heterogeneous objective functions
- [[kennedy-2012-modelling-human-behaviour]] — why multi-parameter utilities overstate
  human rationality
