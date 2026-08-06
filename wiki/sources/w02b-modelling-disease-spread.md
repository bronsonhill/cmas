---
title: "Week 2b: Modelling Disease Spread"
type: source
source_type: lecture
link: https://canvas.lms.unimelb.edu.au/courses/239814
tags: [comp90083, week-02, lecture, sir-model, epidemiology, model-design]
date: 2026-08-06
---

# Week 2b: Modelling Disease Spread

## Overview

The second Week 2 lecture, delivered by [[andres-munoz]]. It introduces the
[[sir-model]] — the model students extend for Assignment 1 — and uses it to demonstrate a
model design heuristic that the summary slide states directly: start from a basic model and
add structure, rather than building the complicated version first ([[model-extension]]).

The motivation is epidemiological. Pandemics recur across history and carry high mortality:
the Black Death killed roughly a third of Europe's population in the 1300s, and the 1918
Spanish flu killed more people than the concurrent First World War. The lecture contrasts
two recent outbreaks. [[sars-2003-outbreak]] produced a cumulative case curve that rose and
then flattened after an intervention around May 2003, with case counts contained to the
thousands. [[covid-19-pandemic]] instead went exponential ([[exponential-growth]]). The
questions policymakers faced were why SARS was contained and COVID-19 was not, when
Australia could safely reopen its borders, whether the disease could be eliminated (it
could not — it is now endemic), and why national experiences differed so widely. The
lecturer noted that colleagues who taught this subject worked on the Australian pandemic
response at the [[doherty-institute]], using agent-based models to inform policy.

Models are needed because the alternative — deliberately infecting people to observe what
happens — is unethical, slow, and yields a single scenario rather than a comparison. The
dynamics are genuinely complex, spanning pathogen evolution, immune response,
person-to-person transmission, global transport, social behaviour, interventions, treatment
and vaccine development, misinformation and politics. The modelling response is to pull one
lever at a time rather than all at once, since a model containing everything explains
nothing.

The [[sir-model]] itself is the minimal representation: every individual is susceptible,
infectious, or recovered, with transitions $S \to I \to R$ and no return path. The lecture
gave a small worked implementation — ten agents, one initially infectious, everybody meets
everybody each day, infection on contact with probability $q$, recovery with probability
$\gamma$ — and traced it for $q = 0.2$, $\gamma = 1$ over seven days, peaking at three
simultaneous infectious agents before dying out. Two design points came out of the trace.
State changes take effect on the *next* day, not immediately, so that processing agents
sequentially does not let a newly infected agent infect others within the same step; the
lecturer compared this to a race condition in parallel processing ([[scheduling]]). And the
[[contact-rate]] assumption that everybody meets everybody is only defensible at small
scale — applied to a five-million-agent Melbourne with $q = 0.2$ it would infect a million
people on day one, so parameters have to be assessed against the model setup, not only
against the dynamics you want.

The remainder of the lecture is critique and extension. Students identified the model's
weaknesses: parameters are hard to estimate empirically, there is no death state, immunity
is assumed permanent so reinfection is impossible, and the state space is too coarse to
represent asymptomatic carriers or severity. Transmission risk depends on population
density, social behaviour and cultural practice — the lecturer cited burial rites involving
washing the bodies of the dead as a driver of Ebola transmission in parts of Africa. The
class then designed the Overview section of an ODD for a zombie apocalypse model, an
exercise reconstructed in [[zombie-apocalypse-model-design]].

An answer to an Ed discussion question opened the lecture and is worth recording: the
supplied scaffolding model distributes agents uniformly across an unstructured space
because a uniform distribution introduces no positional bias, making it a [[null-model]]
baseline; and it starts from a single infected agent because outbreaks begin with a patient
zero rather than a cluster.

## Key concepts

- [[sir-model]]
- [[compartmental-model]]
- [[contact-rate]]
- [[exponential-growth]]
- [[epidemic-intervention]]
- [[null-model]]
- [[model-extension]]
- [[scheduling]]
- [[stochasticity]]
- [[odd-protocol]] (applied in the design exercise)
- [[complex-system]], [[emergence]]

## Key entities

- [[andres-munoz]] — lecturer
- [[sars-2003-outbreak]] — the contained outbreak
- [[covid-19-pandemic]] — the uncontained one
- [[doherty-institute]] — where colleagues built ABMs for the Australian response
- [[covid-19-abm-australia]] — that class of policy model, introduced in Week 1a

## Topics covered (revision checklist)

- Ed board answer on the scaffolding model's assumptions:
  - Uniform agent distribution over an unstructured space = a null model, introducing no
    positional bias; every position equally probable
  - One initially infected agent (patient zero), not a cluster
  - Changing these adds assumptions; the assignment is not about tuning parameters
- History of pandemics: Black Death (~1/3 of Europe, 1300s), Spanish flu (1918, more deaths
  than World War I)
- SARS 2003: cumulative case curve rises then flattens after intervention around May;
  schools and public facilities closed in Hong Kong; contained to Hong Kong and Southeast
  Asia
- COVID-19: exponential growth in cumulative cases
- Policy questions: why SARS was contained, what enabled COVID-19 to spread, when Australia
  could reopen (borders closed ~18 months, quarantine on arrival), whether elimination was
  possible (no — endemic), why country experiences differed
- Why models are needed: infecting people is unethical, slow, and gives one scenario
- Factors making the dynamics complex: pathogen mutation and virulence, airborne vs contact
  transmission, individual susceptibility (age, comorbidity), global transport patterns,
  social behaviour, interventions, treatments and vaccines, misinformation, politics and
  economic capacity to sustain lockdowns
- Interventions named: lockdowns, curfews, quarantine, contact-tracing apps, masks,
  vaccines, travel restrictions
- The SIR model: three states, transitions $S \to I \to R$, recovery assumed permanent
  - Origins in mathematics as compartments holding population *fractions*, with flows
    between them; in an ABM the same diagram describes one individual's state sequence
- Simple implementation: $N = 10$, one infectious at $t=0$, everybody meets everybody daily,
  infection per contact with probability $q$, recovery per day with probability $\gamma$
- Algorithm per day: (1) for each susceptible, check contact with each infectious, draw
  $n$, infect if $n < q$; (2) for each infectious, draw $n$, recover if $n < \gamma$;
  (3) stop when no infectious remain, else advance a day
- Worked trace with $q = 0.2$, $\gamma = 1.0$: $|I| = 1, 1, 1, 2, 3, 1, 0$ over $t = 0..6$
- Deferred state change: infection and recovery take effect the following day, so sequential
  processing does not double-count within a step — a race condition in miniature
- Parameter sweeps reasoned qualitatively: low $q$ and high $\gamma$ shortens infectious
  duration, shrinks the peak and dies out fast; high $q$ and low $\gamma$ gives a large
  simultaneous infected pool and exponential growth
- Contact scaling: the standard assumption is that one person meets roughly a fixed number
  $c$ of others per day regardless of population size; the everybody-meets-everybody
  assumption breaks at scale
- $q = 0.2$ with 100 contacts implies super-spreader behaviour; parameter plausibility
  depends on the contact structure, not just on the desired dynamics
- Weaknesses of basic SIR raised in discussion: uncertain parameters, no death state, no
  reinfection / waning immunity, too few states (asymptomatic carriers, severity), unrealistic
  population size, no spatial or local contact structure
- Other transmission-risk factors: population density, social life, cultural practices
  (Ebola and funerary washing of bodies)
- Modelling interventions rather than the disease: vaccination introduced after day $k$,
  lockdowns, mobility restrictions
- Zombie apocalypse design exercise (Overview section of an ODD): purposes proposed included
  designing urban settlements that limit outbreaks, minimising casualties, testing lethal
  responses, and devising escape plans; one entity (humans) with states susceptible,
  zombie, and two kinds of removed (died naturally vs zombie destroyed); scale chosen from
  the purpose — first week of chaos versus years of adaptation

## Notable claims / results

- The SIR model's compartments originated as population fractions with flows between them;
  reusing the diagram for an individual agent's state sequence is the agent-based
  reinterpretation, not the original meaning.
- Deferring state changes to the next time step is a modelling decision with real
  consequences: applying infection immediately during a sequential sweep inflates the number
  of infectious agents within a single day.
- The everybody-meets-everybody assumption is scale-dependent. At $N = 10$ it is defensible
  (a household); at $N = 5{,}000{,}000$ with $q = 0.2$ it infects a million agents on day
  one, which is why local contact structure has to be introduced as population grows.
- Parameter values must be assessed against the model's contact structure as well as against
  the dynamics being sought — $q = 0.2$ means something different at 5 contacts than at 100.
- Empirical grounding is uneven: recovery rate can be estimated from observed illness
  duration (roughly a week for influenza), but $q$ is hard to estimate because it depends on
  contact rate.
- A uniform initial distribution is chosen as a null model precisely because it adds no
  information and therefore no bias — see [[null-model]].
- SARS 2003 was contained and COVID-19 was not; understanding what the 2003 response did
  differently was an active question for the modellers advising the 2020 response.
- The design heuristic stated in the summary: start with a basic model and incorporate more
  structure, rather than building complexity from the outset.

## Connections

- Applies the Overview section of [[odd-protocol]] from [[w02a-describing-models]] to a new
  model in the zombie exercise; the SIR model is also the "existing model" an ODD can be
  written for.
- Supplies the base model that Assignment 1 extends, briefed in [[w02a-describing-models]].
- [[scheduling]] gets its concrete justification here — Week 2a named it as an ODD section,
  this lecture shows what goes wrong without it.
- [[stochasticity]] is the mechanism throughout: both transitions are random draws, so a
  single run is one sample from a distribution of outcomes.
- [[covid-19-abm-australia]] from [[w01a-introduction]] is the policy-scale version of the
  model built up here.
- [[zombie-apocalypse-model-design]] is the worked exercise derived from this lecture.
