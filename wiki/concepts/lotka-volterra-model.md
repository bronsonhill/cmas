---
title: Lotka-Volterra Model
type: concept
tags: [population-dynamics, predator-prey, dynamical-systems]
date: 2026-08-23
---

# Lotka-Volterra Model

The Lotka-Volterra model is the classical continuous-time predator-prey model, describing
coupled exponential growth and decay between a prey population and a predator population
that depends on it for food.

## How it works

Let $R$ be a prey ("rabbit") population and $F$ a predator ("fox") population, under the
assumptions that prey have unlimited food and grow at a rate proportional to their size
absent predators, predators eat only prey and decline at a rate proportional to their size
absent prey, and the environment is otherwise static. The model is given by coupled
ordinary differential equations:

## Formula

$$\frac{dR}{dt} = \alpha R - \beta RF$$

$$\frac{dF}{dt} = \delta RF - \gamma F$$

where $\alpha$ is the prey birth rate, $\beta$ the predation rate, $\delta$ the conversion
efficiency of eaten prey into new predators, and $\gamma$ the predator death rate. Both
equations combine a positive inflow term and a negative outflow term — read as stocks
($R$, $F$) with probabilistic in/outflows, the same system can be recast as a discrete
stochastic process: at each time step, a prey is born with probability $\alpha$, a
predator dies with probability $\gamma$, each predator meets a prey with probability
proportional to prey count and eats it with probability $\beta$, and an eaten prey yields a
new predator with probability $\delta$. This reformulation is what makes the model
expressible as a [[cellular-automaton|cellular-automaton]]- or agent-style local-
interaction model rather than only as a system of ODEs.

## Why it matters

The model was motivated by, and reproduces qualitatively, the sustained out-of-phase
oscillation seen in 90 years of Hudson Bay Company hare and lynx trapping records
(1845–1935) — real predator-prey systems genuinely cycle, and Lotka-Volterra was the first
model to derive that cycling from individual-level birth, death, and predation
assumptions rather than fitting a curve to it directly. It is the subject's bridge example
between continuous population-level dynamics (in the tradition of the [[sir-model]]) and
discrete, local-interaction models like [[cellular-automaton|CA]] or
[[agent-based-model|ABMs]].

## Relationships

- [[sir-model]], [[compartmental-model]] — the same population-flow style of model, applied
  to disease rather than predation
- [[cellular-automaton]] — the discrete/stochastic reformulation that lets Lotka-Volterra
  be simulated as a local-interaction model
- [[feedback]] — predation is a negative-feedback coupling between the two populations

## Sources

- [[w04b-2d-cellular-automata]] — the Hudson Bay hare/lynx motivation, the model's
  assumptions, the ODE system, and its discrete stochastic reformulation.
