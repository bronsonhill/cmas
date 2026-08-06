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

## Sources

- [[w02b-modelling-disease-spread]] — the list of interventions raised in discussion, the
  SARS containment example, and the suggestion to model an intervention rather than the
  disease.
