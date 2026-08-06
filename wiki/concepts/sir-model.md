---
title: SIR Model
type: concept
tags: [epidemiology, compartmental-model, abm, assignment-1]
date: 2026-08-06
---

# SIR Model

The SIR model represents an epidemic by assigning every individual one of three states —
**S**usceptible, **I**nfectious, **R**ecovered — and allowing only the transitions
$S \to I \to R$. It is the minimal model of disease transmission, and the base model
students extend for Assignment 1.

## How it works

Two events can happen to an individual. A susceptible person who encounters an infectious
person may become infected. An infectious person may recover. Recovery is permanent in the
basic model: there is no path from $R$ back to $S$, so immunity never wanes and reinfection
is impossible.

The subject's small worked implementation makes the agent-based version concrete:

- **State.** A population of $N = 10$ agents, each holding $S$, $I$ or $R$.
- **Initial condition.** Nine susceptible, one infectious.
- **Contact assumption.** The group is small enough that everybody meets everybody each day.
- **Infection.** Each time a susceptible agent meets an infectious agent, it becomes
  infectious on the next day with probability $q$.
- **Recovery.** An infectious agent recovers on the next day with probability $\gamma$.

The daily schedule is:

1. For each susceptible $X$, and each infectious $Y$ it contacts, draw $n \sim U(0,1)$;
   if $n < q$ then $X$ is infected by $Y$.
2. For each infectious $Y$, draw $n$; if $n < \gamma$ then $Y$ recovers.
3. If no infectious agents remain, stop; otherwise advance to the next day.

Both transitions take effect on the *following* day, which is what stops a sequential sweep
from letting a newly infected agent infect others within the same step — see [[scheduling]].

A traced run with $q = 0.2$ and $\gamma = 1.0$ gave $|I| = 1, 1, 1, 2, 3, 1, 0$ across
$t = 0 \ldots 6$: a small peak of three simultaneous infections, then extinction with one
agent never infected. Because both transitions are random draws, this is one sample, not
the model's behaviour ([[stochasticity]]).

## Formula

The two parameters govern the dynamics:

$$q = \Pr(\text{infection} \mid \text{contact between } S \text{ and } I)$$

$$\gamma = \Pr(\text{recovery per day} \mid \text{infectious})$$

$\gamma$ sets the expected infectious duration: at $\gamma = 1$ every infectious agent
recovers after exactly one day, and lower $\gamma$ lengthens the infectious period. Their
interaction determines the outcome. Low $q$ with high $\gamma$ shortens the time each agent
is infectious and shrinks the pool that can transmit, so the outbreak dies out quickly with
a small peak. High $q$ with low $\gamma$ gives a large simultaneous infectious pool and
exponential growth ([[exponential-growth]]), and is correspondingly hard to bring back
under control.

## Why it matters

SIR is where the subject's "start simple, then extend" heuristic is demonstrated. The model
is deliberately weak, and naming the weaknesses is the route to a research question
([[model-extension]]):

- Parameters are hard to estimate. Recovery has empirical grounding — influenza resolves in
  roughly a week — but $q$ depends on contact behaviour and is not directly observable.
- There is no death state; everyone recovers.
- Immunity is permanent, so waning immunity and reinfection cannot be represented.
- The state space is too coarse for asymptomatic carriers or severity gradations.
- The everybody-meets-everybody assumption does not survive scale-up — see
  [[contact-rate]].
- There is no spatial or network structure, and no interventions
  ([[epidemic-intervention]]).

## Relationships

- [[compartmental-model]] — the mathematical tradition SIR comes from
- [[contact-rate]] — the assumption that breaks first as population grows
- [[scheduling]] — why transitions are deferred to the next day
- [[stochasticity]] — both transitions are probabilistic
- [[epidemic-intervention]], [[model-extension]] — routes to extending it
- [[null-model]], [[initial-conditions]] — the uniform, single-patient-zero setup
- [[covid-19-abm-australia]] — a policy-scale descendant

## Sources

- [[w02b-modelling-disease-spread]] — introduces the model, the $N = 10$ implementation,
  the algorithm, the traced run, the parameter-sweep reasoning, and the weaknesses raised
  in discussion.
