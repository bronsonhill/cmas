---
title: Scheduling
type: concept
tags: [methodology, model-design, abm, odd]
date: 2026-08-06
---

# Scheduling

The schedule of an agent-based model is the ordered sequence of actions performed each time
step, specifying which entities execute which processes and in what order. It forms the
second half of section 3 of the [[odd-protocol]], alongside the process overview.

## How it works

An action pairs a set of entities with a process: "each susceptible agent checks for
contact with each infectious agent", "each infectious agent tests for recovery". The
schedule states the order of those actions and any conditions that trigger transitions
between them — when an agent switches from searching to exploiting a patch, for example.
Pseudo-code is the recommended representation, because the order and the branching are
exactly what pseudo-code expresses well.

The subtle part is **when a state change takes effect**. In the [[sir-model]] worked
through in lecture, infection and recovery are decided on one day but applied on the next.
This is not biological realism about incubation periods, though that reading is available;
it is a computational necessity. Agents are processed sequentially, so if agent 2 is
infected and its state flips immediately, agents 3 through 10 are evaluated against a
population containing one more infectious agent than existed at the start of the day. The
result is more infections per step than the rules specify, and the number depends on the
order in which agents happen to be visited. The lecturer compared this to a race condition
in parallel processing, where the outcome depends on the interleaving of reads and writes
rather than on the logic.

The fix is to compute all transitions against the state at the start of the step and apply
them together at the end — a synchronous update. Deferring recovery has the same
justification in reverse: applying it immediately would remove agents from the infectious
pool before the other agents had a chance to be exposed to them.

## Why it matters

Scheduling decisions change results without changing any rule or parameter. Two
implementations of the same written model specification can produce different epidemic
curves purely because one updates in place and the other defers. That makes the schedule
part of the model, not part of the implementation, which is why the ODD protocol requires
it to be stated explicitly rather than left to whoever writes the code.

## Relationships

- [[odd-protocol]] — section 3
- [[sir-model]] — the worked example where deferred update matters
- [[model-structure]] — processes and their ordering
- [[stochasticity]] — random draws are made per action, so order affects which draws apply
  to which agents

## Sources

- [[w02a-describing-models]] — defines the schedule as an ordered sequence of actions, with
  pseudo-code as a representation.
- [[w02b-modelling-disease-spread]] — the SIR next-day update rule and the race-condition
  reasoning behind it.
