---
title: Imperfect Information
type: concept
tags: [abm, agent-behaviour, sensing, decision-making]
date: 2026-08-30
---

# Imperfect Information

Agents in real systems act on partial and noisy readings of their world. Imperfect
information is the design decision to represent that in a model rather than granting
agents omniscience.

## How it works

Imperfection enters [[agent-sensing]] in four distinct ways, and they are worth
distinguishing because they have different consequences:

- **Range.** An agent senses only out to some distance, or only within some
  [[agent-neighbourhood|neighbourhood]].
- **Coverage of agents.** It can read only a subset of the other agents — those nearby,
  or those it is linked to.
- **Coverage of variables.** It observes some state variables and not others. A house
  buyer sees the asking price, not the seller's reserve.
- **Accuracy.** What it does observe carries error. Two kinds: random noise, which
  averages out over many observations, and systematic bias, which does not.

The fourth is the one models most often skip. The
[[business-investment-model]] as presented explicitly grants error-free sensing of profit
and risk, and the lecture flagged this as an assumption to relax — real investors read
other bidders' seriousness at an inspection through a thick layer of bias.

## More information is not automatically better

The Week 5b experiment is the counterexample worth remembering. Raising the sensing radius
from 1 to 5 improved mean investor wealth; raising it to 8 made it worse. Two mechanisms
were offered. The landscape is uniformly random, so a wider view reveals more options but
no *gradient* — global information carries no directional signal. And a bigger step
reaches a local optimum faster and then sticks there, the same trade-off as a large
learning rate in gradient descent. Muñoz labelled the effect the **paradox of choice**:
more options means more scope for regret, without better outcomes. He was explicit that
this framing was his hypothesis rather than a tested result.

The same pattern showed up when a fully connected communication network replaced the
radius: knowing what everyone else earns tells you nothing about where to move when the
landscape has no structure.

## Why it matters

An [[agent-based-model]] is a framework for evaluating what imperfect decision-making does
to a system — which only works if the imperfection is modelled. Granting agents perfect
information silently converts a question about behaviour under uncertainty into an
optimisation exercise. It is also the assumption most worth putting through
[[sensitivity-analysis]], since sensing range routinely changes the emergent outcome
rather than just its speed.

## Relationships

- [[agent-sensing]] — the mechanism this qualifies
- [[agent-neighbourhood]] — how range and coverage are specified
- [[bounded-rationality]] — the decision-theoretic counterpart
- [[satisficing]] — the decision rule imperfect information motivates
- [[stochasticity]] — random sensing error is one of its uses

## Sources

- [[w05a-sensing]] — the four sources of imperfection, with the house-hunting worked
  example
- [[w05b-adaptation-and-objectives]] — the sensing-radius sweep, the network experiment,
  and the paradox of choice
