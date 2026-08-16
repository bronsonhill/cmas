---
title: Epidemic Intervention
type: concept
tags: [epidemiology, policy, model-design]
date: 2026-08-06
---

# Epidemic Intervention

An epidemic intervention is a deliberate action taken to reduce transmission. In a
transmission model, an intervention is represented as a change to the model's parameters or
structure partway through a run, rather than as a different model.

## How it works

Interventions act on one of three things:

- **Contact structure.** Lockdowns, curfews, quarantine, school and border closures, and
  travel restrictions all reduce who meets whom, lowering the effective [[contact-rate]].
- **Transmission per contact.** Masks and hygiene measures reduce $q$ without changing the
  number of contacts.
- **The susceptible pool.** Vaccination moves agents out of $S$ without passing through $I$,
  which in [[sir-model]] terms is a new transition rather than a parameter change.

Contact-tracing apps sit across the first two — they identify exposed individuals so that
they can be isolated, which removes contacts after the fact.

Modelling an intervention rather than the disease is a legitimate research question in its
own right, and the lecture put it forward as one of the routes for extending the assignment
model: what happens if a vaccine is introduced after day $k$, or if mobility is restricted
once case counts pass a threshold? Both require the intervention to have a start time and a
trigger, which is a scheduling question ([[scheduling]]) as much as a parameter one.

Interventions also have effects the disease model does not capture. The lecture named
misinformation and conspiracy theories, adverse events that undermine confidence in a
vaccine, and the political and economic capacity of a government to sustain closures with
subsidies. These sit outside a simple transmission model but shape whether an intervention
achieves the effect the model predicts.

Week 3 supplies the criterion for whether an intervention works: it must drive the effective
[[reproduction-number]] below one. That single condition covers all three levers, because
$R = \beta/\gamma$ and $\beta$ is contacts multiplied by per-contact transmission
probability. Reducing contacts, reducing transmission per contact, and removing susceptibles
are three routes to the same threshold. For vaccination the requirement is quantitative:
coverage must reach $v \ge 1 - 1/R_0$ ([[herd-immunity-threshold]]).

Interventions can also target *when* rather than *whether*. The Week 3b disease profiles
show that the same final size can arrive as a sharp early peak or a flat late one, and
"flattening the curve" is an intervention aimed at peak size and peak timing rather than at
total infections ([[outbreak-summary-measures]]). Delaying a peak buys preparation time even
when it does not reduce the eventual burden — which is exactly what the antiviral stockpile
study set as its objective ([[influenza-antiviral-stockpile-model]]).

## Why it matters

The 2003 SARS response is the lecture's evidence that interventions work: the case curve
flattened after action was taken, and the outbreak was contained
([[sars-2003-outbreak]]). Understanding which components of that response mattered was an
active question for the modellers advising the COVID-19 response
([[covid-19-pandemic]]) — which is a use of models that only makes sense if interventions
can be represented explicitly and compared.

## Relationships

- [[sir-model]] — the base model interventions extend
- [[contact-rate]] — the main lever most interventions pull
- [[model-extension]] — interventions as an extension route
- [[counterfactual]] — comparing intervention scenarios is a counterfactual experiment
- [[covid-19-abm-australia]] — a model built to evaluate physical-distancing policy
- [[reproduction-number]] — the quantity an intervention must push below one
- [[herd-immunity-threshold]] — the coverage requirement for vaccination
- [[modelling-for-policy]] — the pipeline interventions are compared within
- [[influenza-antiviral-stockpile-model]] — a worked comparison of two interventions

## Sources

- [[w02b-modelling-disease-spread]] — the list of interventions raised in discussion, the
  SARS containment example, and the suggestion to model an intervention rather than the
  disease.
- [[w03a-analysing-models]] — interventions situated within the policy pipeline, the
  COVID-19 intervention list, and the metrics of success discussion.
- [[w03b-reproduction-number]] — vaccination modelled as an $S \to R$ transfer, the coverage
  formula, and the criterion of driving $R$ below one.
