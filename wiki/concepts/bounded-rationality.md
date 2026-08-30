---
title: Bounded Rationality
type: concept
tags: [decision-making, agent-behaviour, cognition]
date: 2026-08-30
---

# Bounded Rationality

Bounded rationality is [[herbert-simon]]'s correction to
[[rational-choice-theory]]: agents still try to decide well, but they do so with limited
information, limited cognitive capacity and limited time.

## How it works

Rational choice theory assumes an agent knows all available actions, has perfect knowledge
of the environment, and holds preferences that are complete and transitive. Each of those
fails for real decision-makers, and the failures are structural rather than incidental:

- **Information is incomplete.** You cannot enumerate the alternatives you never heard of.
- **Information is costly.** A Bloomberg terminal seat runs to roughly $30{,}000$ per
  year — professional-grade information is a capital expense, not a free good.
- **Cognition is limited.** There is a ceiling on how many variables a person can weigh
  and how mathematically involved that weighing can be.
- **Time is limited.** The house you are still evaluating gets sold to someone else.

The behavioural consequence is [[satisficing]] — take an option that is good enough — and
[[fast-and-frugal-heuristics|fast-and-frugal heuristics]], which reach decisions on a
handful of cues.

## Why it matters

For agent-based modelling this is not a caveat but a design instruction. An agent
specified as a perfect optimiser imports a rationality the modelled system does not have,
and any conclusion the model draws about collective outcomes inherits it. The Week 5
lectures make the point concretely: the business investment model's agents optimise over
everything they can see, and the lecture's proposed revision replaces that with a
satisficing threshold precisely because the optimising version is not a defensible model
of an investor.

Bounded rationality also cuts the other way. Simpler rules are cheaper to run and easier
to justify, which matters when scaling to many agents.

## Relationships

- [[rational-choice-theory]] — what it bounds
- [[satisficing]] — the decision rule it implies
- [[imperfect-information]] — the sensing-side counterpart
- [[fast-and-frugal-heuristics]] — decision procedures built for these limits
- [[herbert-simon]]

## Sources

- [[kennedy-2012-modelling-human-behaviour]] — bounded rationality as the tempering of
  rational choice theory, citing Simon (1996)
- [[w05b-adaptation-and-objectives]] — why agents cannot optimise, with the information
  cost example
