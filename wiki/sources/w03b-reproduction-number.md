---
title: "Week 3b: The Reproduction Number and Deterministic Models"
type: source
source_type: lecture
link: https://canvas.lms.unimelb.edu.au/courses/239814
tags: [comp90083, week-03, lecture, reproduction-number, deterministic-model, epidemiology, assignment-1]
date: 2026-08-16
---

# Week 3b: The Reproduction Number and Deterministic Models

## Overview

The second Week 3 lecture, delivered by [[andres-munoz]], is the last one covering general
modelling before the subject moves to specific model families, and the last one covering
epidemics in detail. It introduces the [[reproduction-number]], gives the deterministic
counterpart of the stochastic SIR runs from [[w03a-analysing-models]], and closes with a
second pass over the zombie design exercise aimed at policy questions rather than model
structure.

The reproduction number $R$ is the average number of secondary cases infected by a typical
primary case. Its basic form $R_0$ assumes an entirely susceptible population and, for the
SIR model, equals $\beta / \gamma$. It functions as a threshold: below one the outbreak
dies out, above one it may take off. The lecturer connected this to the segregation model's
convergence breakdown from the previous lecture — both are critical points where the
qualitative behaviour of a system changes ([[tipping-point]]). $R$ is also a parameter you
generally cannot observe directly, because it depends on how many people someone actually
encounters and which of those encounters transmitted; it has to be estimated from data.
Runs with $\beta = 0.25$ and $\gamma = 0.4$, giving $R_0$ below one, die out whether the
outbreak starts from one infectious agent or a hundred, which the lecturer tied to H5N1
influenza spreading from birds to humans without becoming human-transmissible.

The deterministic detour answers the question of why you would ever give up stochasticity.
The argument for stochastic models is that we care about tail events, and a mean hides them
— which is what the bimodal distributions in the previous lecture demonstrated. But when
you want the typical case, or want to do mathematics on the model rather than sample from
it, a [[deterministic-model]] produces a unique outcome from given parameters and initial
conditions and runs cheaply. The lecture builds it through function iteration: a function
maps an input to an output, iteration feeds the output back in, and a
[[difference-equation]] writes that as $x_{t+1}$ in terms of $x_t$. Applied to SIR this
gives the discrete-time update $S_{t+1} = S_t - \beta S_t I_t$, $I_{t+1} = I_t + \beta S_t
I_t - \gamma I_t$, $R_{t+1} = R_t + \gamma I_t$, with $\beta$ and $\gamma$ now rates rather
than per-contact probabilities. The continuous-time form replaces these with differential
equations, and models of this kind usually track population fractions summing to one. The
recovery rate carries a directly interpretable inverse: $D = 1/\gamma$ is the average
infectious period, so $\gamma = 1/4$ means four days infectious, or equivalently a quarter
of the infectious population recovering per day.

Analysing the deterministic model is what yields the results that make $R_0$ useful. The
final attack rate rises steeply between $R_0 = 1$ and $R_0 = 2$, then saturates — above
roughly four, essentially everyone is infected. Four worked disease profiles separate the
two parameters' effects: measles ($R_0 = 16$, seven days infectious) infects nearly
everyone very fast; chickenpox ($R_0 = 8$, seven days) is slower but still peaks within
about ten days; mumps ($R_0 = 8$, fourteen days) has the same reach but a longer, flatter
peak that occupies hospital beds for longer; smallpox ($R_0 = 4$, fourteen days) still
reaches most people but peaks around day 40, which is preparation time — this is what
"flattening the curve" refers to. The final application is vaccination: modelled in the
simplest way as moving individuals from $S$ directly to $R$, it reduces the effective
reproduction number, and the fraction that must be covered to prevent an outbreak is
$v \ge 1 - 1/R_0$ ([[herd-immunity-threshold]]).

## Key concepts

- [[reproduction-number]]
- [[herd-immunity-threshold]]
- [[deterministic-model]]
- [[difference-equation]]
- [[sir-model]], [[compartmental-model]]
- [[stochasticity]], [[stochastic-fadeout]]
- [[tipping-point]]
- [[epidemic-intervention]]
- [[exponential-growth]]
- [[outbreak-summary-measures]]
- [[research-question]], [[model-extension]]

## Key entities

- [[andres-munoz]] — lecturer
- [[covid-19-pandemic]] — reproduction numbers by variant
- [[sars-2003-outbreak]] — $R_0$ around 3, met with hard interventions anyway
- [[netlogo]], [[netlogo-hiv-model]] — suggested reading for assignment extension ideas

## Topics covered (revision checklist)

- Assignment marking rubric released; the subject weights abstraction, question formulation,
  experiment design and presentation of results over volume of code
- Positioning: last lecture on general modelling concepts; game-theoretic models from Week
  6, network models Week 7, optimisation and satisficing later, model evaluation from Week 8
- Reproduction number $R$: average secondary cases per typical primary case
- Basic reproduction number $R_0$: the same quantity in a totally susceptible population
- $R_0 = \beta / \gamma$ for the SIR model
- Threshold behaviour: $R < 1$ the outbreak dies out; $R > 1$ it may take off
- Generation diagrams contrasting a branching cascade ($R_0 > 1$) with a shrinking one
  ($R_0 < 1$)
- $R$ as a non-observable parameter — contact counts and attribution of transmission are
  hard to measure; estimates come from data after the fact
- Critical points / phase transitions as the general phenomenon; the segregation model's
  ~70% threshold as the other instance
- Fadeout runs at $N = 10{,}000$, $\beta = 0.25$, $\gamma = 0.4$, 25 simulations: from 1
  initial infectious, outbreaks reach only tens of people and die out; from 100 initial
  infectious they still die out, so the outcome is not driven by the initial number
- H5N1 influenza as the real-world analogue: transmissible from birds to humans, not
  sustained between humans; seasonal influenza has $R_0$ near 1
- Why stochastic models: real systems contain randomness, and tail events (black swans)
  matter — a mean over a stochastic system can be deceiving
- Why deterministic models: a unique outcome per parameter set and initial condition, the
  typical or average case, and tractability for mathematical analysis
- Functions and iteration: $f(x) = 3x$; the iterated sequence $x_0, f(x_0), f(f(x_0)),
  \ldots$; written as a difference equation $x_{t+1} = 3x_t$ over $x_0, x_1, \ldots, x_t$
- Deterministic SIR as difference equations, with state $S_t, I_t, R_t$ and
  $\Delta t = 1$ by convention, the timestep length chosen afterwards (a day, a week, six
  hours)
- $\beta$ and $\gamma$ as per-capita rates of effective contact and of recovery, rather than
  the per-contact probabilities of the agent-based version
- Compartment diagram with flows $\beta S I$ from $S$ to $I$ and $\gamma I$ from $I$ to $R$
- Recovery rate and duration: $D = 1/\gamma$ is the average infectious period; $\gamma =
  1/4$ means four days infectious, or a quarter of the infectious recovering each day
- Running the deterministic model: implementable in a spreadsheet, R or MATLAB; identical
  output on every run, unlike the stochastic version
- Difference versus differential equations: discrete steps versus continuous change;
  $dS/dt = -\beta S I$, $dI/dt = \beta S I - \gamma I$, $dR/dt = \gamma I$
- Models often expressed as population fractions with $S + I + R = 1$
- Final attack rate against $R_0$: zero below one, a steep rise between one and two, then
  saturation; above roughly four almost everyone is infected
- Worked disease profiles (all deterministic SIR, $N = 1000$):
  - measles-like: $R_0 = 16$, $\gamma = 0.14$ ($1/\gamma = 7$ days) — sharp early peak near
    750 infectious, everyone infected
  - chickenpox-like: $R_0 = 8$, $\gamma = 0.14$ (7 days) — peak near 620 around day 9
  - mumps-like: $R_0 = 8$, $\gamma = 0.07$ (14 days) — same reach, peak near 620 around
    day 18, much slower decline
  - smallpox-like: $R_0 = 4$, $\gamma = 0.07$ (14 days) — peak near 400 around day 38
- Reading the profiles for real-world implications: peak height as hospital load, infectious
  duration as bed-occupancy time, peak timing as preparation time, and the flatter-later
  curve as "flattening the curve"
- The two questions these models are asked: what is $R$ for this disease in this population,
  and how many people must be vaccinated to prevent an outbreak
- Vaccination modelled as moving individuals from the $S$ compartment to $R$, equivalently
  reducing the effective reproduction number below one
- Herd immunity threshold $v \ge 1 - 1/R_0$, increasing with $R_0$
- Threshold values from the lecture chart: $R_0 = 1 \to 0\%$, $1.25 \to 20\%$, $1.6 \to
  37.5\%$, $2 \to 50\%$, $2.5 \to 60\%$, $4 \to 75\%$, $5 \to 80\%$, $8 \to 87.5\%$, $10
  \to 90\%$, $12.5 \to 92\%$, $16 \to 93.75\%$, $20 \to 95\%$
- Disease bands on the same chart: influenza ~1–2, SARS ~2–4, COVID-19 ancestral ~2.5–3,
  alpha ~4–5, delta ~5–8, polio ~5–8, chickenpox ~10–12, measles ~12–18
- Measles outbreak in Texas attributed to vaccination coverage falling below the threshold
- Annual influenza vaccination explained by circulating strains changing plus waning
  immunity; each year's vaccine targets predicted strains and may miss
- Zombie exercise, second pass: framing a science or policy question, what to add to the
  model, and what to measure
  - The supplied $S \to Z \to D \to Z$ diagram contains a closed loop, so a permanently-dead
    state is needed
  - Candidate interventions raised: safe zones or isolation (with a capacity limit),
    cremation of corpses, decapitation, an anti-zombie task force
  - Rejected question: "maintain a sustainable ratio of humans to zombies" — not tractable
    as stated, needs bounding
  - Outputs to track: total cremated, remaining safe-zone capacity, the personnel required
    to carry out cremation
- Assignment pointer: the NetLogo Models Library HIV model (under Biology), which adds
  partner pairings and behavioural factors to transmission, as a source of extension ideas

## Notable claims / results

- $R_0 = \beta/\gamma$ is a ratio of a transmission rate to a recovery rate, so the same
  $R_0$ can arise from a highly transmissible short infection or a mildly transmissible long
  one. Chickenpox and mumps in the lecture both sit at $R_0 = 8$ and produce very different
  curves.
- The threshold at $R = 1$ is a critical point, not a gradual transition: the qualitative
  behaviour of the system changes on either side of it.
- Below $R_0 = 1$, seeding the population with a hundred infectious agents instead of one
  does not produce an outbreak. Outbreak establishment depends on the reproduction number,
  not on the size of the introduction.
- $R$ is not directly observable. It is inferred from data, which is why estimates for the
  same disease vary between sources and get revised.
- The relationship between $R_0$ and the final attack rate saturates. Increasing $R_0$ from
  4 to 16 changes the speed and peak of an outbreak far more than it changes how many people
  are eventually infected.
- Stochastic and deterministic formulations answer different questions. The deterministic
  SIR model produces the average trajectory, and by construction cannot produce the fadeout
  mode that [[w03a-analysing-models]] showed occupying roughly half of all stochastic runs.
- Modelling vaccination as an $S \to R$ transfer is the crudest possible representation and
  is adequate only for asking about coverage thresholds. Representing imperfect vaccine
  efficacy requires a separate state with a reduced infection probability.
- The vaccination coverage needed rises steeply with $R_0$, which is why highly
  transmissible diseases such as measles are the first to return when coverage slips.

## Connections

- Direct continuation of [[w03a-analysing-models]]: that lecture showed the fadeout mode in
  stochastic runs, and this one gives the threshold quantity that explains it.
- Supplies the aggregate/ODE formulation that [[compartmental-vs-agent-based]] previously
  had to reconstruct from a single sentence in [[w02b-modelling-disease-spread]].
- Extends [[sir-model]] from the agent-based version taught in Week 2 to its deterministic
  compartmental counterpart, and makes explicit that $\beta$ and $\gamma$ change meaning
  between the two.
- [[epidemic-intervention]] gains a quantitative criterion here — an intervention works if
  it drives the effective reproduction number below one.
- Continues the zombie design exercise begun in [[zombie-apocalypse-model-design]], moving
  from structure to questions and interventions.

## Notes on source discrepancies

The slides are treated as authoritative where the recording differs from them. The lecturer
gave the recovery rate for the fadeout example as 1.4 while the slide reads $\gamma = 0.4$;
quoted COVID-19 at $R_0 \approx 6$ for delta and $\approx 4$ for alpha against chart bands
of roughly 5–8 and 4–5; and gave measles and chickenpox coverage thresholds of about 90%
where the chart gives 93.75% and 87.5%. The attack-rate curve was described in the
recording as logarithmic; it is a saturating curve arising from the final-size relation, not
a logarithm.
