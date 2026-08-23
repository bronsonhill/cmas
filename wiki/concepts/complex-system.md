---
title: Complex System
type: concept
tags: [complexity, foundations]
date: 2026-08-01
---

# Complex System

A complex system is a system composed of many individual parts that interact, and from
whose interactions collective properties arise that are not properties of any single part.

## How it works

Three features characterise the systems this subject models:

- **Many components.** A flock, a crowd, a population, a market.
- **Local interaction.** Each component acts on information from its immediate
  neighbourhood only. No component has a global view, and there is usually no central
  controller issuing instructions.
- **Emergent collective properties.** Structure at the system level appears without being
  specified at the component level — see [[emergence]].

The starling murmuration is the standard illustration: thousands of birds, each seeing
only those nearby, producing a shifting cloud that morphs coherently — and does so under
pressure from a hawk, with no bird coordinating the response. The same holds for a crowd:
you perceive the person in front of you and feel the person beside you, and the crowd's
movement is the aggregate of many such local reactions.

Disease spread is a complex system in the same sense. Transmission is a property of a
network of individual encounters — this room, then a supermarket, then a restaurant — and
the epidemic curve is what that network produces.

## Why it matters

Complex systems are precisely the systems that resist aggregate, top-down description,
because averaging destroys the local interaction structure that generates the behaviour.
That is the case for building an [[agent-based-model]] instead. Complex systems also
exhibit [[tipping-point|tipping points]]: regions of parameter space where behaviour
changes qualitatively rather than gradually.

## Relationships

- [[emergence]] — the defining phenomenon
- [[agent-based-model]] — the modelling approach matched to these systems
- [[flocking]] — canonical example
- [[tipping-point]] — qualitative regime change in complex systems
- [[self-organisation]], [[decentralisation]], [[feedback]] — defining properties
- [[chaos]] — a route by which simple deterministic rules produce complex behaviour
- [[cellular-automaton]] — a minimal formalism exhibiting complex-system behaviour

## What makes a system complex

[[w04a-complex-systems-and-emergence]] fills in the definition with a worked survey: few
parts and simple rules can be either regular (a planet orbiting a star) or chaotic (the
three-body problem, or the logistic map's bifurcation cascade — see [[chaos]]); many parts
with simple rules can be ordered (a crystal), disordered (a gas), or genuinely complex
(flocking, [[cellular-automaton|cellular automata]], complex networks); many parts with
complicated, heterogeneous rules produce complex-but-reproducible behaviour (biological
development, termite colonies, markets); and many parts under classical engineering design
or centralised leadership (an orchestra, the military) instead produce deterministic or
centralised behaviour by construction. The property distinguishing genuine complex systems
from the engineered/centralised cases is [[decentralisation]] — no single controller, only
[[feedback|local information and local feedback]] — combined with [[self-organisation]].
Sayama's working definition, quoted directly in the lecture, is the subject's canonical
one: systems of interacting, typically nonlinear components that may self-organise, sit
between fully regular and fully random, and exhibit emergent macroscopic behaviour.

## Sources

- [[w01a-introduction]] — introduces complex systems via murmurations, crowds, and
  COVID-19 transmission.
- [[w04a-complex-systems-and-emergence]] — the 2×2 "parts × rule complexity" survey,
  decentralisation, feedback, and Sayama's working definition.
- [[sayama-2015-modeling-and-analysis-of-complex-systems-ch1]] — source of the working
  definition; frames complex systems as filling Weaver's gap between "problems of
  simplicity" and "problems of disorganized complexity".
