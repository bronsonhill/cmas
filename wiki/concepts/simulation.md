---
title: Simulation
type: concept
tags: [foundations, definitions]
date: 2026-08-01
---

# Simulation

A simulation is an approximate imitation of the **operation** of a process or system —
where "operation" means the system's behaviour *over time*. In practice, a simulation is
the computational implementation of a [[model]].

## How it works

The defining ingredient is time. A static representation of a system is a model; running
that representation forward, step by step, so that its state evolves, is a simulation.
The systems of interest in this subject are all **dynamical** — they change at every step.

A simulation *can* be physical (a wind tunnel, a medical training dummy), but is usually
computational. Simulation is used across:

- **Engineering** — water flow over a ship's hull, airflow over a wing
- **Entertainment** — computer games, film special effects
- **Education** — training for surgical procedures
- **Science** — galaxy formation, theories of evolution: systems that cannot be
  experimented on directly
- **Decision-making** — forecasting weather and epidemics, infrastructure planning

That third and fifth cases explain much of simulation's value: it substitutes for
experiments that are impossible, unethical, or too expensive to run on the real system.

## Why it matters

Simulation is what turns a model from a description into an instrument. Once a model runs,
you can vary parameters, replicate under different random seeds, and observe outcomes you
could not derive analytically — which is exactly what makes [[emergence|emergent]]
behaviour in a [[complex-system]] accessible at all.

## Relationships

- [[model]] — what a simulation implements
- [[agent-based-model]] — a type of simulation model
- [[stochasticity]] — why simulation results require replication
- [[netlogo]], [[mesa]] — the environments used to build simulations in this subject
- [[counterfactual]] — the alternate-scenario runs a simulation makes possible
- [[nasa-black-hole-simulation]] — simulation whose purpose was instrument design

## Sources

- [[w01a-introduction]] — defines simulation via "operation", i.e. behaviour over time,
  and surveys application domains.
- [[w01b-modelling-cycle]] — stresses that simulation concerns *dynamics* (static models
  being of limited interest), and adds the [[nasa-black-hole-simulation]] example.
