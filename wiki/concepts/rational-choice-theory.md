---
title: Rational Choice Theory
type: concept
tags: [decision-making, agent-behaviour, cognition]
date: 2026-08-30
---

# Rational Choice Theory

Rational choice theory holds that people act to maximise benefit or minimise cost, by
logical process. It is the default model of human decision-making that agent-based
modellers inherit from economics, and the one most in need of qualification.

## How it works

The theory as Kennedy states it (citing Coleman 1990) carries three assumptions:

1. All possible actions are known to the agent.
2. Agents have perfect knowledge of the environment.
3. Preferences are well behaved — complete ordering, transitivity.

Given those, the agent computes and takes the best action. Implemented in an ABM, this is
an explicit [[objective-function]] evaluated over an enumerated option set — exactly what
the [[business-investment-model]] does.

Knowledge in a rational agent is conventionally represented in two forms: **declarative**
knowledge of facts, and **procedural** knowledge as IF-THEN rules. A rational agent that
also [[agent-learning|learns]] needs to acquire, retain and apply both.

[[bounded-rationality]] is the standard correction, and [[fast-and-frugal-heuristics]] and
[[satisficing]] are what agents do instead.

## Why it matters

Rational choice is a reasonable first cut and a poor final answer. Kennedy's blunter
version of the same complaint targets the *other* default: modelling human choice as a
uniform random draw is a stronger and worse claim than modelling it as rational, because
it asserts that people have no preferences, no memory of past choices, and no regard for
consequences. His demonstration is that people cannot even produce randomness on demand —
asked for a number between one and four, roughly half say "three".

The practical position for a modeller sits between the two: rational choice as the
skeleton, bounded by realistic limits on information, cognition and time.

## Relationships

- [[bounded-rationality]] — the correction
- [[objective-function]] — how rationality is implemented in an ABM
- [[satisficing]] — the behavioural alternative
- [[stochasticity]] — why a random draw is not a neutral substitute

## Sources

- [[kennedy-2012-modelling-human-behaviour]] — the assumptions, the knowledge
  representations, and the argument against random substitutes
