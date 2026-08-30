---
title: Threshold Rule
type: concept
tags: [abm, agent-behaviour, decision-making]
date: 2026-08-30
---

# Threshold Rule

A threshold rule fires a specific behaviour when a variable crosses a stated value. It is
the cheapest usable representation of a decision, and Kennedy's recommended replacement
for a random draw.

## How it works

The form is an IF-THEN rule comparing a value to a threshold:

```
IF <hunger> is below <hungerThreshold1>                        THEN agent-dies.
IF <hunger> is above <hungerThreshold2>                        THEN address-another-goal.
IF <hunger> is between <hungerThreshold1> and <hungerThreshold2> THEN search-for-food.
```

Two extensions follow immediately. The variable can be a **transformation** of raw inputs,
so the rule triggers on a derived quantity. And the input can be **multi-dimensional** —
a function combining hunger and thirst, compared against one threshold — which is where a
threshold rule shades into an [[objective-function]].

Kennedy's structural observation: comparison and thresholding are the same operation.
Comparing `function1` with `function2` is comparing `(function1 - function2)` against a
threshold of zero. Every rule can therefore be written in threshold form, which is why he
uses it as the common notation.

A [[satisficing]] threshold is the same construct applied to switching: stay put while
performance clears an aspiration level, move when it does not. The Week 5b proposal for
the [[business-investment-model]] is exactly this — hold the investment while it returns
at least 5% a year, otherwise relocate.

## Why it matters

Threshold rules are explainable, cheap to evaluate, and scale to large agent populations.
They approximate human behaviour crudely but honestly, and unlike a uniform random draw
they make a claim the modeller can defend and a reader can criticise. The cost is
brittleness at the boundary: behaviour flips discontinuously, which can produce artefacts
that look like [[tipping-point|tipping points]] but are properties of the rule rather than
of the system.

## Relationships

- [[objective-function]] — a threshold is its simplest form
- [[satisficing]] — the aspiration-level threshold
- [[adaptive-behaviour]] — where the rule lives
- [[fast-and-frugal-heuristics]] — trees built from sequential threshold tests

## Sources

- [[kennedy-2012-modelling-human-behaviour]] — the hunger example, the transformation and
  multi-dimensional extensions, and the comparison/threshold equivalence
- [[w05b-adaptation-and-objectives]] — the 5% satisficing threshold proposal
