---
title: Difference Equation
type: concept
tags: [dynamical-systems, model-design, epidemiology]
date: 2026-08-16
---

# Difference Equation

A difference equation defines the state of a system at the next time step as a function of
its current state, written $x_{t+1} = f(x_t)$. Iterating it generates a trajectory. It is
the discrete-time way of specifying a dynamical system, and the differential equation
$dx/dt = f(x)$ is its continuous-time counterpart.

## How it works

A function maps an input to an output: $f(x) = 3x$ takes $x$ and returns three times it.
Iteration feeds the output back in as the next input, producing the sequence

$$x_0,\; f(x_0),\; f(f(x_0)),\; f(f(f(x_0))),\; \ldots$$

Writing the same thing with a time index gives $x_{t+1} = 3x_t$ over the sequence $x_0, x_1,
x_2, \ldots, x_t$. This is what makes the model *dynamical*: the current state depends on
the previous state, so past behaviour propagates forward.

By convention the step size is $\Delta t = 1$, and what one step represents — a day, a week,
six hours — is a modelling decision made separately. That decision is not free: the
parameters must be expressed on the same time base, so a recovery rate of $\gamma = 0.14$
means something different per day than per week.

The deterministic [[sir-model]] is the subject's worked instance. Its state is the triple
$(S_t, I_t, R_t)$, and the update rules are

$$S_{t+1} = S_t - \beta S_t I_t$$
$$I_{t+1} = I_t + \beta S_t I_t - \gamma I_t$$
$$R_{t+1} = R_t + \gamma I_t$$

Each equation is a bookkeeping statement about a [[compartmental-model]] flow: $\beta S_t
I_t$ people leave $S$ and arrive in $I$, and $\gamma I_t$ people leave $I$ and arrive in
$R$. The terms appear twice with opposite signs, which is what keeps the total population
constant.

## Formula

The continuous-time form replaces discrete steps with instantaneous rates of change:

$$\frac{dS}{dt} = -\beta S I, \qquad \frac{dI}{dt} = \beta S I - \gamma I, \qquad
\frac{dR}{dt} = \gamma I$$

Models written this way commonly track the *fraction* of the population in each compartment
rather than counts, so that

$$S + I + R = 1$$

The recovery rate has an interpretable inverse: $D = 1/\gamma$ is the average time spent
infectious. A rate of $\gamma = 1/4$ per day means an average of four days infectious, or
equivalently that a quarter of the infectious population recovers each day. The two readings
are the same statement about a rate.

## Why it matters

Difference and differential equations are how models get written down in a form you can
reason about mathematically rather than only run. The threshold result $R_0 = \beta/\gamma$
comes from analysing these equations, not from watching simulations
([[reproduction-number]]).

They also mark the boundary of what the subject does with mathematics. The lecture was
explicit that this is the only session deriving model behaviour analytically; the rest of
the subject works with agent-based models where the population-level equations are not
available and behaviour has to be measured from output.

The translation between an equation system and an ABM is worth holding onto in both
directions. A difference equation over compartment counts and a state machine over
individual agents can describe the same disease, but the equation version cannot condition a
transition on an individual's history, location or attributes — see
[[compartmental-vs-agent-based]].

## Relationships

- [[deterministic-model]] — difference equations are its usual implementation
- [[compartmental-model]] — each equation is a compartment's balance of inflows and outflows
- [[sir-model]] — the worked system
- [[reproduction-number]] — derived by analysing these equations
- [[scheduling]] — the ABM analogue of "the next state depends on the current one"
- [[model-scales]] — choosing what one timestep represents

## Sources

- [[w03b-reproduction-number]] — introduces functions and iteration, writes the SIR
  difference equations and their differential counterpart, notes the $\Delta t = 1$
  convention and the fraction formulation, and gives the $D = 1/\gamma$ interpretation.
