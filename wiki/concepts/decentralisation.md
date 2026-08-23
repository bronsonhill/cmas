---
title: Decentralisation
type: concept
tags: [complexity, foundations]
date: 2026-08-23
---

# Decentralisation

Decentralisation is the absence of a single controller or leader directing a system's
behaviour, with control instead distributed across its many components.

## How it works

The lecture breaks decentralisation into three components:

- **Distribution** — each part of the system carries only a subset of the global
  information; no single component holds the whole picture.
- **Bounded knowledge** — no part has a full view of the system state, only of its local
  neighbourhood.
- **Parallelism** — parts can act simultaneously rather than waiting on a central scheduler.

The worked example is market prices: no central computer sets prices, yet buying and
selling by many independent, locally-informed agents produces an aggregate signal — prices
rising, falling, or crashing under panic — that looks coordinated without being centrally
directed.

## Why it matters

Decentralisation is what distinguishes a complex system from a classically engineered one.
An orchestra or a military unit has many parts and complicated rules, but behaviour is
governed by a central cause, leader, or plan — deliberately centralised by design. A
complex system instead relies on [[self-organisation]] arising purely from local
interaction, which is exactly the property that makes [[agent-based-model|agent-based
models]] the right tool: there is no global rule to write down directly, only local rules
whose aggregate effect must be simulated.

## Relationships

- [[complex-system]] — decentralisation is one of its defining properties
- [[self-organisation]] — the process decentralisation enables in the absence of central
  control
- [[feedback]] — local signals that propagate through a decentralised system

## Sources

- [[w04a-complex-systems-and-emergence]] — introduces distribution, bounded knowledge, and
  parallelism, with the market-price example.
