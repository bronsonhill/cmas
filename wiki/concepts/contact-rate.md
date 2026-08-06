---
title: Contact Rate
type: concept
tags: [epidemiology, model-design, assumptions]
date: 2026-08-06
---

# Contact Rate

The contact rate, conventionally $c$, is the number of other individuals a person
encounters in a given period. In a transmission model it is the structure through which
infection travels, and it is where the simplest models break first.

## How it works

The small [[sir-model]] taught in lecture assumes everybody meets everybody each day. With
$N = 10$ this is defensible — it describes something like a household or a single room, and
each agent has 9 contacts per day.

The assumption does not scale. Applied to a Melbourne-sized population of five million with
per-contact infection probability $q = 0.2$, the first infectious agent contacts everyone
and infects roughly a million people on day one. Nothing about the rules is wrong; the
contact structure has become absurd.

The standard replacement assumption is that contact rate is roughly constant in population
size: a person meets about $c$ others per day whether they live in a town or a city. That
decouples transmission from $N$ and forces the model to represent *which* others — local
neighbourhoods, households, workplaces, a network — rather than treating the population as
well-mixed.

The parameters interact, which is the point the lecture pressed. A per-contact probability
of $q = 0.2$ means something different at 5 contacts per day than at 100. At 100 contacts,
$q = 0.2$ describes an agent infecting 20 people daily — super-spreader behaviour, not
typical behaviour. Parameter values therefore have to be assessed against the model's
contact structure, not only against whether they produce dynamics that look right.

## Why it matters

Contact structure is the main lever separating a toy SIR model from one that can say
anything about a real population, and it is the first thing that has to change when the
population grows. It is also where most of the interesting extensions live: population
density, social behaviour, cultural practices, mobility restrictions and lockdowns all act
by changing who contacts whom ([[epidemic-intervention]]).

## Relationships

- [[sir-model]] — where the well-mixed assumption is introduced
- [[epidemic-intervention]] — interventions mostly operate on contact structure
- [[model-extension]] — adding local contact is the standard first extension
- [[model-scales]] — spatial structure is one way to constrain contact
- [[abstraction]] — well-mixed is an abstraction that holds only at small scale

## Sources

- [[w02b-modelling-disease-spread]] — the five-million-agent counterexample, the constant-$c$
  scaling assumption, and the super-spreader reading of $q = 0.2$ at 100 contacts.
