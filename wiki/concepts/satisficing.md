---
title: Satisficing
type: concept
tags: [agent-behaviour, decision-making]
date: 2026-08-01
---

# Satisficing

Satisficing is the decision criterion of accepting a **good enough** solution rather than
searching for the best one — the counterpart to [[optimisation]].

## How it works

A satisficing agent sets an aspiration level and takes the first option that meets it,
stopping the search there. It does not enumerate alternatives or guarantee that a better
option does not exist.

For agent-based modelling this is often the more defensible assumption. Real people,
firms and animals act under limited information, limited time and limited computation;
modelling them as perfect optimisers imports a rationality the system does not have — see
[[bounded-rationality]]. Satisficing rules are also usually simpler to specify and cheaper
to run.

The concrete implementation is a **satisficing threshold**: keep doing what you are doing
while performance clears an aspiration level, switch when it does not. Week 5b's proposed
revision to the [[business-investment-model]] is exactly this — hold the current
investment while it returns at least 5% a year, otherwise move to a randomly chosen
available opportunity, with no ability to evaluate alternatives first. The threshold turns
a search problem into a stay-or-go test, which is why it is cheap.

That framing also names the underlying asymmetry: we typically know far more about our
current situation than about the alternatives, so a decision to switch is usually made
without being able to predict its consequences.

## Why it matters

The optimising/satisficing choice is one of the substantive modelling decisions in
designing agent behaviour, and it can change the emergent outcome. It belongs to the
weeks 4–9 material on modelling agent behaviour and interaction, alongside game theory and
bargaining.

## Why satisficing can beat optimising

The Week 5b result is worth holding onto: satisficing agents often end up *closer* to the
optimum than greedy optimisers. The optimising agents in the business investment model
settle onto the best patch they can see, become risk-averse as the horizon shortens, and
stagnate on a local optimum. Satisficing agents keep moving while they are below
aspiration, accept short-term losses, and explore more of the landscape. Greedy strategies
tend to be suboptimal — a familiar result from search, arriving here through decision
theory.

There is no guarantee attached. In a model with irreducible failure risk, more exploration
also means more exposure.

## Relationships

- [[optimisation]] — the contrast
- [[bounded-rationality]] — why optimisation is unavailable
- [[threshold-rule]] — how a satisficing rule is written
- [[objective-function]] — what the aspiration level is defined on
- [[agent-based-model]] — where the choice is made
- [[complex-system]] — collective outcomes depend on which criterion agents use

## Sources

- [[w01a-introduction]] — defined in contrast to optimisation ("finding a good enough
  solution") as part of the subject outline.
- [[w05b-adaptation-and-objectives]] — attributed to [[herbert-simon]]; satisficing
  thresholds, the 5%-return example, and the claim that satisficing gets closer to optimal
  than greedy search.
- [[kennedy-2012-modelling-human-behaviour]] — bounded rationality as the root, and
  fast-and-frugal trees as an empirically derived form of the same idea.
