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

### The deterministic formulation

Week 3 gives the same model without the randomness. In the deterministic version the state
is the compartment counts $(S_t, I_t, R_t)$ rather than individual agents, and the update is
a [[difference-equation]] system applying the expected flow directly:

$$S_{t+1} = S_t - \beta S_t I_t, \qquad I_{t+1} = I_t + \beta S_t I_t - \gamma I_t,
\qquad R_{t+1} = R_t + \gamma I_t$$

with a continuous-time counterpart $dS/dt = -\beta S I$, $dI/dt = \beta S I - \gamma I$,
$dR/dt = \gamma I$, usually written over population fractions so that $S + I + R = 1$.

The parameters change meaning across the two formulations and the symbols are easy to
confuse. In the agent-based version $q$ is a per-contact transmission probability and
$\gamma$ a per-day recovery probability. In the deterministic version $\beta$ is a
per-capita rate of *effective* contact — average contacts per person per unit time
multiplied by $q$ — and $\gamma$ is a recovery rate whose inverse $D = 1/\gamma$ is the
average infectious period. A value carried across without re-derivation will be wrong.

Analysing the deterministic system yields the results that make the model useful as a
decision tool: $R_0 = \beta/\gamma$ ([[reproduction-number]]), the saturating relationship
between $R_0$ and the final attack rate, and the vaccination coverage threshold
$v \ge 1 - 1/R_0$ ([[herd-immunity-threshold]]). What it cannot produce is the fadeout mode
— it generates an outbreak every time $R_0 > 1$, whereas the stochastic version fails to
establish in roughly 45% of runs at $R_0 = 6.25$ ([[stochastic-fadeout]]).

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
- [[compartmental-vs-agent-based]] — what the aggregate formulation of this model gives up
- [[deterministic-model]], [[difference-equation]] — the aggregate formulation
- [[reproduction-number]], [[herd-immunity-threshold]] — results derived from it
- [[outbreak-summary-measures]] — what to record when running it
- [[stochastic-fadeout]], [[bimodal-distribution]] — the shape of its output across runs

## Sources

- [[w02b-modelling-disease-spread]] — introduces the model, the $N = 10$ implementation,
  the algorithm, the traced run, the parameter-sweep reasoning, and the weaknesses raised
  in discussion.
- [[w03a-analysing-models]] — stochastic runs at $N = 10{,}000$, $\beta = 2.5$,
  $\gamma = 0.4$, and the distributions of final size, peak size and peak timing across
  replicates.
- [[w03b-reproduction-number]] — the deterministic difference and differential equation
  formulation, the meaning shift in $\beta$ and $\gamma$, $R_0 = \beta/\gamma$, the four
  worked disease profiles, and vaccination as an $S \to R$ transfer.
