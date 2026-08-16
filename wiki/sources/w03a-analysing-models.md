---
title: "Week 3a: Analysing Models"
type: source
source_type: lecture
link: https://canvas.lms.unimelb.edu.au/courses/239814
tags: [comp90083, week-03, lecture, model-analysis, summary-statistics, stochasticity]
date: 2026-08-16
---

# Week 3a: Analysing Models

## Overview

The first Week 3 lecture, delivered by [[andres-munoz]], moves from building models to
using them. It is framed around the "Analyse the model" step of the [[modelling-cycle]],
and answers two questions: what people are trying to achieve when they analyse a model, and
how the output of many stochastic runs gets compressed into numbers you can reason about.

Analysis means two things at once. You study the model to understand how it behaves and to
check that it is correct, and you use it to solve the problem it was built for
([[model-analysis]]). The reason simulation is worth the trouble is that real-world data is
constrained — collecting more of it may be expensive, slow, unethical or impossible,
whereas a simulation can be manipulated freely and observed as often as you like. The
lecturer illustrated the cost side with research practice: paid survey panels, and
fieldwork that requires travelling to wherever the animals you study actually live. That
freedom is only useful under discipline, so the lecture pushes students from *playing* with
a model — moving sliders to see what happens — toward designing experiments that answer a
stated question, varying parameters, initial conditions and random seeds systematically
from a baseline rather than opportunistically.

The purpose of a model shapes how it is used, and the lecture separates two purposes.
[[modelling-for-science]] follows the inductive cycle of observe, question, hypothesise,
predict, test, analyse and conclude, with hypotheses posed as individual-level behaviours
and implemented as ABMs whose population-level output is compared against observed
patterns; the worked case is the [[schelling-segregation-model]], demonstrated live in
NetLogo. [[modelling-for-policy]] instead assumes the model is already validated and runs
problem, objectives, interventions, projections, decision analysis and implementation, with
the model supplying the projection step; the worked case is the
[[influenza-antiviral-stockpile-model]], whose analysis concluded that treatment alone
could neither delay the peak nor reduce infections enough, and which fed into the
Australian pandemic plan.

The second half is about summarisation, and it is the part with a trap in it. An
agent-based model can emit the trajectory of every agent and every environment variable at
every step, which is far more data than anyone can use, so you choose observations of
interest driven by the question ([[summary-statistic]]). For an outbreak the natural
choices are the final size, the size of the peak and the timing of the peak
([[outbreak-summary-measures]]), each mapping to a decision — total burden, peak demand on
the health system, and how long you have to prepare. Averaging those across runs looks
obvious and is wrong here. Repeated stochastic runs of the same SIR setup produce a
*bimodal* distribution ([[bimodal-distribution]]): in roughly half the runs the outbreak
fails to establish and infects almost nobody ([[stochastic-fadeout]]), and in the rest it
infects around half the population. The mean falls in the empty valley between the two
modes and describes no run that ever happened. Increasing the population from ten thousand
to a million smooths individual trajectories but does not remove the fadeout mode — a
non-trivial fraction of runs still produce no outbreak at all, whatever the population size.

## Key concepts

- [[model-analysis]]
- [[modelling-for-science]]
- [[modelling-for-policy]]
- [[summary-statistic]]
- [[outbreak-summary-measures]]
- [[bimodal-distribution]]
- [[stochastic-fadeout]]
- [[stochasticity]]
- [[sir-model]], [[contact-rate]]
- [[modelling-cycle]], [[research-question]]
- [[tipping-point]]
- [[epidemic-intervention]]

## Key entities

- [[andres-munoz]] — lecturer
- [[schelling-segregation-model]] — the science-purpose worked example
- [[thomas-schelling]] — its author
- [[influenza-antiviral-stockpile-model]] — the policy-purpose worked example
- [[netlogo]] — used for the live segregation demonstration
- [[covid-19-pandemic]] — source of the intervention examples

## Topics covered (revision checklist)

- Weekly objectives: describe how models are used in science and policy; design and apply
  summary measures of model behaviour; explain the significance of the reproduction number
- Recap of the [[modelling-cycle]] diagram, with patterns entering at "assemble hypotheses"
  and at "analyse the model" ([[pattern-oriented-modelling]])
- ODD recap questions: which cycle stages the [[odd-protocol]] serves (choosing model
  structure, implementing, communicating — not primarily formulating the question); which
  section holds a described-and-justified process (process overview and scheduling for
  simple behaviour, submodels for complex behaviour, design concepts for learning /
  optimisation / communication); the environment is described under entities, state
  variables and scales
- What it means to analyse a model: understand its behaviour, check correctness, improve
  performance, and use it on the problem it was designed for
- Why simulate: real-world data collection can be costly, time-consuming, unethical or
  impossible; a simulation can be manipulated freely and sampled without limit
- Playing versus controlled experiments: ask what you want to know about the behaviour, then
  design experiments to learn it; vary parameters, initial conditions and seeds
  systematically from a baseline
- Modelling for science — the inductive approach: observe, question ("why?" / "how?"),
  hypothesise, predict, test, analyse and conclude or repeat
- Hypotheses posed as individual-level behaviours implemented as ABMs, evaluated on their
  ability to reproduce observed population-level patterns
- Segregation worked through the science pipeline: observe residential segregation among
  populations professing not to discriminate; hypothesise that mild individual neighbourhood
  preferences suffice; predict increasingly homogeneous neighbourhoods; run scenarios
  varying preference strength and measuring homogeneity; conclude the hypothesis is plausible
- Live NetLogo demonstration: a 30% similarity threshold converges quickly to roughly 73%
  observed similarity with clearly defined clusters; a 90% threshold does not converge;
  convergence breaks down somewhere around a 70% threshold ([[tipping-point]])
- Modelling for policy: problem, objectives, interventions, projections, decision analysis,
  implementation — with the model supplying projections, and post-implementation data
  feeding back
- COVID-19 interventions recalled in class: lockdowns, vaccines, mask mandates, social
  distancing, quarantine, border and airport closures
- Metrics of policy success: reduced cases, lower mortality, minimised economic impact, and
  harder-to-quantify considerations such as acceptability and restrictions on freedom
- Influenza antiviral stockpile study: problem (reduce pandemic impact), objectives (delay
  the peak, minimise infections), interventions (prophylaxis versus treatment), projections
  across epidemiological scenarios, finding that treatment alone was insufficient,
  implemented in the pandemic plan
- Statistical analysis of simulation models: quantify outputs as summary statistics, compare
  scenarios, quantify parameter-to-statistic relationships, compare against observed data
- Combinatorial output volume: agents × steps × runs × scenarios grows past what can be
  stored or read, so observations must be chosen
- Definition of $\beta$ used from here on: average contacts per person per unit time,
  multiplied by the per-contact transmission probability $q$
- Baseline stochastic SIR runs: $N = 10{,}000$, $\beta = 2.5$, $\gamma = 0.4$; a single run
  peaks near 400 infectious around step 55
- Repeated runs at the same settings vary in peak height, peak timing, skew and duration —
  and some produce no outbreak at all
- Outbreak observations of interest: final size (total infected), peak size (demand on the
  health system), peak timing (preparation time)
- Final-size distribution is bimodal: roughly 45% of runs near zero, the remainder clustered
  around 5,200 of 10,000 agents
- Peak-size distribution is likewise bimodal, with a mode near 500 infectious
- Peak-timing distribution is bimodal and noisier: an early spike near $t = 0$ from the
  failed outbreaks, and a broad mode around $t = 45$
- Scaling to $N = 1{,}000{,}000$: trajectories become smoother and less jagged, peak height
  is predictable near 48,000, timing remains variable, and the no-outbreak line persists
- Why the mean misleads on a bimodal distribution: it lands in the valley between the modes
  and corresponds to no actual run

## Notable claims / results

- Analysing a model is two activities: verifying that it behaves correctly and is an
  adequate abstraction, and applying it to the problem it was built for. Building models to
  play with is a stage, not the destination.
- The case for simulation rests on the cost and feasibility of real-world data, not on
  simulation being intrinsically better. Where data is cheap and ethical to collect, the
  argument weakens.
- Science and policy uses of models differ in what they change. Science seeks to understand
  a mechanism without intervening; policy asks which action to take, and the model is used
  at the projection step to compare interventions.
- Schelling's result is that mild individual preferences are sufficient for strong
  population-level segregation: a 30% same-type threshold produces neighbourhoods around 73%
  homogeneous. No discriminatory intent is required for the pattern to appear
  ([[emergence]]).
- Very strong preferences do not simply produce stronger segregation — above roughly a 70%
  threshold the model stops converging at all, because insufficient agents can be satisfied
  simultaneously.
- The antiviral analysis found treatment alone insufficient to delay the peak or reduce
  infections across a range of outbreak scenarios, which is a negative result that changed
  policy.
- Repeated runs of an identical stochastic SIR configuration yield a bimodal final-size
  distribution. The mean of that distribution (around 3,000 infected in the worked case) is
  a value no run produced.
- Stochastic fadeout is the *most common* single outcome at these parameters — around 45% of
  runs — despite $R_0 = 6.25$ being well above one.
- Increasing population size damps run-to-run variability in the trajectory shape but does
  not eliminate the fadeout mode; the probability of no outbreak is not a small-population
  artefact.
- The lecture's stated takeaway: once you have chosen the data points you care about, do not
  compress them blindly — check the shape of their distribution first.

## Connections

- Continues [[w02b-modelling-disease-spread]], reusing the same SIR model but analysing it
  rather than constructing it.
- Supplies the "analyse the model" step of the [[modelling-cycle]] introduced in
  [[w01b-modelling-cycle]].
- Paired with [[w03b-reproduction-number]], which explains why the fadeout mode exists and
  gives the deterministic counterpart of these stochastic runs.
- [[stochasticity]] was named as a property in Week 2; this lecture shows what it costs you
  at analysis time.
- The ODD recap at the start revisits [[odd-protocol]] from [[w02a-describing-models]].
