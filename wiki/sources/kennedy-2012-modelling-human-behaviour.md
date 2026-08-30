---
title: "Kennedy (2012): Modelling Human Behaviour in Agent-Based Models"
type: source
source_type: reading
link: https://doi.org/10.1007/978-90-481-8927-4_9
tags: [comp90083, week-05, reading, agent-behaviour, cognition, human-behaviour]
date: 2026-08-30
---

# Kennedy (2012): Modelling Human Behaviour in Agent-Based Models

Chapter 9 of *Agent-Based Models of Geographical Systems* (Heppenstall, Crooks, See &
Batty, eds., Springer, 2012, pp. 167–179), by [[william-kennedy]].

## Overview

The chapter is a survey of how to put a person inside an agent, and it opens by saying
what not to do. Kennedy's demonstration is a one-line experiment: ask someone to pick a
number between one and four. Roughly half say "three", about 30% say "two", and the
remaining 10% split between "one" and "four" — and people feel compelled to justify the
choice. Ask for a number between 1 and 20 and "17" comes back about 40% of the time
against a uniform expectation of 5%. His point is that people cannot produce randomness
even when instructed to. Modelling a human choice as a uniform draw is therefore not a
neutral placeholder for ignorance; it is a strong empirical claim that all options are
equally likely, that agents have no preferences, no memory of past choices, and no regard
for consequences. Kennedy is blunt that this claim is usually false.

The middle of the chapter sets out principles of human behaviour worth encoding. Humans
are information processors with limited input bandwidth, limited memory and limited
processing, but language gives them very wide information sources and, in written form,
memory spanning centuries. Personality traits (the three-factor and five-factor
taxonomies, which share extraversion and neuroticism) are stable over a lifespan,
roughly normally distributed in large populations, and a large part of individual
difference. Motivation is ordered — Maslow's 1943 hierarchy running from physiological
needs through safety, social needs, esteem and self-actualisation — which Kennedy
recommends as a way to arbitrate between an agent's competing goals. Then
[[rational-choice-theory]], with [[bounded-rationality]] as its correction, and knowledge
split into declarative facts and procedural IF-THEN rules. Finally the non-rational side:
a common set of basic emotions, appraisal theory as the dominant account, and
Loewenstein and Lerner's observation that emotion's effect on decision-making cannot be
cleanly classed as improving or degrading it. Socially, humans run a
[[social-influence|theory of mind]] of each other, and Latané's law of social impact
gives conformity as a power law in the number of influencers.

The survey of approaches is the practically useful part, and it is organised as three
tiers of increasing fidelity and cost. **Mathematical approaches** — random draws (bad),
[[threshold-rule|threshold rules]], multi-dimensional utility functions, and stock-and-flow
dynamic models — are simplifications tuned to the model's purpose. **Conceptual
frameworks** — [[bdi-architecture|BDI]], [[pecs-framework|PECS]], and Gigerenzer's
[[fast-and-frugal-heuristics|fast-and-frugal trees]] — reason in terms of beliefs and
motives rather than parameter arithmetic. **[[cognitive-architecture|Cognitive
architectures]]** — [[soar]] and [[act-r]] — are research-grade models of individual
cognition at millisecond resolution, borrowed from a field with different goals.

Kennedy closes on three challenges: we still do not understand humans well; data on
specific behaviours often does not exist; and without data, validating a model of human
behaviour is difficult at best.

## Key concepts

- [[rational-choice-theory]]
- [[bounded-rationality]]
- [[threshold-rule]]
- [[cognitive-architecture]]
- [[bdi-architecture]]
- [[pecs-framework]]
- [[fast-and-frugal-heuristics]]
- [[social-influence]]
- [[stochasticity]]

## Key entities

- [[william-kennedy]]
- [[herbert-simon]]
- [[gerd-gigerenzer]]
- [[soar]]
- [[act-r]]

## Topics covered (revision checklist)

- Why humans are not random: the pick-a-number demonstration and its statistics
- What a uniform random draw actually asserts about the modelled human
- Levels of modelling: individual, small group (modelled as individuals), society
  (modelled statistically, with no decision process represented)
- Sociobiology: instinct-driven social insects vs mammals with a theory of mind
- The computational theory of mind, and the brain-as-computer metaphor's limits
- AI vs cognitive science as the two camps on replicating human behaviour
- Humans as limited information processors; the human senses and their thresholds
- Personality traits: three-factor and five-factor models; extraversion and neuroticism
- Maslow's hierarchy of needs as a goal-arbitration scheme for agents
- Rational choice theory and its assumptions; bounded rationality
- Declarative vs procedural knowledge; learning, retention, application
- Basic emotions; appraisal theory; emotion's ambiguous effect on decision quality
- Theory of mind; Latané's law of social impact; Friedkin and Johnsen on group
  convergence; Surowiecki on when crowds are wise
- Mathematical approaches: random draws, threshold rules, multi-parameter functions,
  dynamic (stock-and-flow) modelling
- Conceptual frameworks: BDI, PECS, fast-and-frugal decision trees
- Cognitive architectures: Soar, ACT-R, and their respective scopes
- Challenges: understanding humans, data availability, verification and validation

## Notable claims / results

- Reported response frequencies for "pick a number between one and four": ~50% "three",
  ~30% "two", ~10% each for "one" and "four". Kennedy notes these come from undocumented
  sources rather than a formal study. For 1–20, "17" is chosen about 40% of the time.
- Latané's law of social impact: $I = sN^t$, where $I$ is the percentage conforming, $s$ a
  constant of circumstance, $N$ the number of others, and $t$ a factor below one and often
  near one half. The same mechanism produces bystander inhibition by diffusing
  responsibility.
- Surowiecki's finding is that good collective results come from *differences* between
  members' independent evaluations, not from compromise or consensus; social influence,
  by producing conformity, degrades them.
- Gigerenzer's fast-and-frugal trees, built from three sequential questions, outperformed
  both a heart-disease predictive instrument and physicians in a US hospital, and
  explained 92% of two UK magistrates' bail decisions.
- Threshold rules and value comparisons are interchangeable: comparing `function1` with
  `function2` is comparing `(function1 - function2)` against a threshold of 0.
- The major weakness of multi-parameter objective functions is that the available data
  does not support treating humans as pure optimisers.
- ACT-R models low-level cognition over very short periods and does not represent beliefs,
  desires or intentions explicitly; Soar can be read as a BDI implementation.

## Connections

- [[w05a-sensing]] and [[w05b-adaptation-and-objectives]] — the lectures this reading
  accompanies; Kennedy supplies the content of the adaptation rule the lectures leave open
- [[satisficing]] — Simon's bounded rationality is the shared root
- [[stochasticity]] — Kennedy's argument narrows where a random draw is defensible in a
  model of people
- [[odd-protocol]] — the design concepts (adaptation, objectives, learning, prediction)
  are the slots these frameworks fill
