---
title: Zombie Apocalypse — A Worked ODD Overview
type: material
tags: [worked-example, model-design, odd, sir-model]
date: 2026-08-06
---

# Zombie Apocalypse — A Worked ODD Overview

A reconstruction of the in-class design exercise from [[w02b-modelling-disease-spread]]. The
task was to write the **Overview** section of an [[odd-protocol]] description — purpose;
entities, state variables and scales; process overview and scheduling — for a model of a
zombie outbreak. The scenario is deliberately absurd, which is useful: with no real data to
appeal to, every design decision has to be justified by the purpose rather than by realism.

## The scenario

A zombie is a reanimated corpse that feeds on human flesh. The idea comes from
Afro-Caribbean belief systems, particularly voodoo practice in the Caribbean derived from
West African cultures, and was popularised by twentieth-century horror film — *Night of the
Living Dead* onwards.

The rules given were four transitions:

- Susceptible humans can die of natural causes and become **removed**.
- Removed humans can reanimate and become **zombies**.
- Susceptible humans bitten by a zombie become zombies themselves, effectively immediately.
- Susceptible humans can defeat zombies, which returns them to being **removed** — in the
  films, typically by destroying the head.

This is a [[compartmental-model]] with a cycle in it, which is what makes it a more
interesting exercise than [[sir-model]]: the removed state is not absorbing.

## 1. Purpose

Several purposes were proposed, and the exercise's point is that they are not
interchangeable — each implies a different model.

| Proposed purpose | What the model must then represent |
|---|---|
| Design human settlements that limit an outbreak | Spatial layout, barriers, density — the environment is the thing being varied |
| Minimise casualties | A mortality count as the observed output, and interventions to compare |
| Test lethal responses ("what stops them?") | Combat mechanics and human capability as parameters |
| Devise escape plans | Mobility, routes, and cost of evacuation; population is the thing being moved |

The settlement-design and escape-plan purposes pull hardest in opposite directions, which is
what makes the later scale decision follow from this section rather than being chosen
independently.

## 2. Entities, state variables and scales

**Entities.** One entity: humans. The class considered whether zombies are a second entity
and settled on a single entity with multiple states, since a zombie is a human in a
different state rather than a different kind of thing. Whether the environment counts as an
entity was raised at the end and answered: the environment is defined and can carry
conditions, but it is the environment, not an agent.

**State variables.** The disease-like state, with a refinement the class identified:

- **Susceptible** — a living human.
- **Zombie** — reanimated and infectious.
- **Removed (natural death)** — dead, and still able to reanimate.
- **Removed (zombie destroyed)** — permanently out of the model.

Splitting *removed* in two is the substantive design contribution of the exercise. A single
removed state cannot express the difference between a corpse that might reanimate and one
that cannot, and that difference is exactly what determines whether the outbreak can sustain
itself.

Further state variables were floated but not settled: combat capability, whether an agent is
military or civilian, and zombie variation (fast versus slow, weak versus strong).

**Scales.** Chosen from the purpose, following [[model-scales]]:

- Designing settlements that survive means representing **years**, since the interest is in
  how a society adapts to living with the threat. The lecture drew the analogy to the gap
  between *28 Days Later* and *28 Years Later*: the first film is the chaos of the initial
  outbreak, the second is the society that formed afterwards, and they are not the same
  model.
- Planning an escape means representing the **first week**.

Spatial scale was not settled, but settlement design implies a spatially explicit model,
whereas a pure casualty-count model might not need one.

## 3. Process overview and scheduling

Not reached in class before time ran out. The processes implied by the four transitions are:

1. **Natural death** — each susceptible human dies with some probability per step.
2. **Reanimation** — each naturally-dead human reanimates with some probability per step.
3. **Biting** — each zombie in contact with a susceptible human converts it, with the
   conversion effectively immediate rather than delayed.
4. **Defeat** — each susceptible human in contact with a zombie destroys it with some
   probability, moving it to permanent removal.

Processes 3 and 4 are the same encounter resolved two ways, which raises a scheduling
question the SIR model does not face: when a human and a zombie meet, which outcome is
tested first, and does the order bias the result? This is the same class of problem as the
deferred-update rule in [[scheduling]] — the schedule is part of the model, and leaving it
implicit means the answer depends on implementation order.

## What the exercise demonstrates

The purpose section does real work. "Minimise casualties" and "design settlements" produce
different entities, different observed outputs and different temporal extents, and there is
no way to write sections 2 and 3 without having committed to one. That is the argument for
ODD's ordering: purpose first, because everything downstream is constrained by it.

## Related

- [[odd-protocol]] — the template being filled in
- [[sir-model]] — the model this extends structurally
- [[compartmental-model]] — the state diagram, here with a cycle
- [[model-extension]] — the exercise as an instance of extending a basic model
- [[truffle-foraging-model-design]] — the Week 1 equivalent exercise
- [[w02b-modelling-disease-spread]] — the source lecture
