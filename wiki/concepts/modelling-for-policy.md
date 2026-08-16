---
title: Modelling for Policy
type: concept
tags: [decision-analysis, epidemiology, intervention]
date: 2026-08-16
---

# Modelling for Policy

Using a model for policy means using an already-validated model to inform a decision. The
pipeline is problem, objectives, interventions, projections, decision analysis and
implementation, with the model supplying the projection step — estimating how each candidate
intervention would affect the stated objectives.

## How it works

The six steps as taught:

1. **Problem** — engage with the decision-maker to identify what needs solving
2. **Objectives** — identify the management objectives
3. **Interventions** — define the actions that can be taken
4. **Projections** — evaluate the impact of interventions on objectives
5. **Decision analysis** — evaluate the relative merit of the interventions
6. **Implementation** — put the chosen intervention into practice

The model enters at step 4 and nowhere else. Its outputs may send the process backwards:
projections can prompt revision of the objectives or consideration of interventions that
were not on the original list. If data is collected after implementation, it feeds back to
improve future projections.

Two steps carry most of the difficulty. Defining objectives means naming metrics of success,
and in the COVID-19 case those included reduced cases, lower mortality and minimised
economic impact — but also considerations such as acceptability and restrictions on personal
freedom that are much harder to quantify. A consideration that cannot be measured cannot be
projected, so the choice of objectives silently determines what the analysis can say. Defining
interventions means enumerating the levers available: for the pandemic, lockdowns, vaccines,
mask mandates, social distancing, quarantine and border closures, tested individually or in
combination ([[epidemic-intervention]]).

The [[influenza-antiviral-stockpile-model]] is the worked case. The problem was reducing the
impact of a pandemic given a limited antiviral stockpile. The objectives were delaying the
outbreak peak and minimising total infections. The interventions were using the drugs for
prophylaxis or for treatment. Projections were run across a range of epidemiological
scenarios, and the analysis found treatment alone insufficient on either objective. The
result was implemented in the Australian pandemic plan.

## Why it matters

Policy modelling differs from [[modelling-for-science]] in what it assumes and what it
changes. It assumes the model has already been validated, so validation is not part of the
loop, and it seeks to act on the system rather than to understand it. Science asks why
segregation happens; policy asks what could be done about it.

The antiviral case shows why a negative result matters here. Concluding that an intervention
does not work is itself a decision-relevant finding, and it changed what Australia planned to
rely on. Policy modelling is a comparison between actions, so ruling one out is progress.

The step that deserves scepticism is the handoff at implementation. The lecturer's aside was
that a politician can announce a measure "because the model tells us" and treat that as
absolution. The model supplies projections under assumptions; it does not supply the value
judgements in the objectives, and presenting it as though it does misrepresents what was
computed.

## Relationships

- [[modelling-for-science]] — the contrasting purpose
- [[epidemic-intervention]] — the intervention step, for epidemics
- [[influenza-antiviral-stockpile-model]] — the worked case
- [[covid-19-abm-australia]] — a policy model of the same kind, at national scale
- [[outbreak-summary-measures]] — the quantities projections report
- [[model-analysis]] — the projection and decision-analysis steps in practice
- [[counterfactual]] — what a projection of an unimplemented intervention is
- [[herd-immunity-threshold]] — a policy target derived from a model

## Sources

- [[w03a-analysing-models]] — sets out the six-step pipeline, notes that policy models are
  typically already validated, works through the antiviral stockpile case, and lists the
  COVID-19 interventions and success metrics raised in class.
