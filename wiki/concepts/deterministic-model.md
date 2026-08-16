---
title: Deterministic Model
type: concept
tags: [model-design, simulation, epidemiology]
date: 2026-08-16
---

# Deterministic Model

A deterministic model produces a unique outcome from a given set of parameters and initial
conditions. Each state has exactly one possible successor, so repeated runs of the same
configuration are identical. It is the alternative to a stochastic model, which generates a
distribution of potential outcomes ([[stochasticity]]).

## How it works

Where a stochastic [[sir-model]] draws a random number to decide whether each contact
transmits, the deterministic version applies the expected flow directly: a fixed proportion
of susceptible-infectious encounters produce infections each step. The randomness is not
approximated or seeded, it is absent. The model simulates the average behaviour of the
system rather than one sample from it.

Mechanically these models are usually [[difference-equation]] systems in discrete time, or
differential equations in continuous time. The discrete SIR form is

$$S_{t+1} = S_t - \beta S_t I_t, \qquad I_{t+1} = I_t + \beta S_t I_t - \gamma I_t,
\qquad R_{t+1} = R_t + \gamma I_t$$

which is simple enough to run in a spreadsheet, and which produces exactly the same smooth
single-peaked curve on every execution.

The parameters change meaning in the translation. In the agent-based version $q$ is a
per-contact transmission probability and $\gamma$ a per-day recovery probability; in the
deterministic version $\beta$ and $\gamma$ are per-capita rates of effective contact and
recovery. Reusing a number across the two formulations without re-deriving it is a
straightforward way to get wrong answers.

## Why it matters

The trade-off is explicit and worth being able to argue both ways.

Deterministic models are cheap, reproducible without seed management, and tractable
analytically. The threshold result $R_0 = \beta/\gamma$ and the relationship between $R_0$
and the final attack rate are both derived from the deterministic formulation, not measured
from simulation output. They also give a clean answer to "what does the typical outbreak
look like" without needing hundreds of runs.

What they cannot do is represent variability, and in epidemics the variability is the
interesting part. A deterministic SIR model with $R_0 = 6.25$ always produces an outbreak.
The equivalent stochastic model produces no outbreak at all in roughly 45% of runs
([[stochastic-fadeout]]), and the distribution of final sizes is bimodal
([[bimodal-distribution]]) with the deterministic answer sitting near one mode while ignoring
the other entirely. Tail events — the reason the lecturer raised black swans — are invisible
by construction.

The practical position taught in the subject is that the choice follows the question. Use a
deterministic model to characterise average dynamics or to do mathematics; use a stochastic
model when the spread of outcomes, the probability of extinction, or rare high-impact
scenarios are what the decision depends on.

## Relationships

- [[stochasticity]] — the property being given up
- [[stochastic-fadeout]] — the behaviour a deterministic model cannot produce
- [[difference-equation]] — the usual implementation form
- [[sir-model]] — the worked instance
- [[compartmental-model]] — deterministic compartmental models are the classical form
- [[compartmental-vs-agent-based]] — the fuller comparison
- [[reproduction-number]] — derived from this formulation

## Sources

- [[w03b-reproduction-number]] — introduces deterministic models as the alternative to
  stochastic ones, builds the SIR difference and differential equations, notes the
  identical-output property, and gives the argument for wanting each kind.
- [[w03a-analysing-models]] — supplies the stochastic run distributions the deterministic
  model averages over.
