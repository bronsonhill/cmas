# Content Log

## [2026-08-01] ingest | Week 1a: Introduction

- **Source page:** `wiki/sources/w01a-introduction.md`
- **New concept pages:** agent-based-model, complex-system, emergence, flocking, model,
  modelling-cycle, optimisation, satisficing, simulation, stochasticity, tipping-point
- **New entity pages:** andres-munoz, boids, covid-19-abm-australia, mesa, netlogo,
  wilensky-and-rand
- **Updated pages:** wiki/sources/index.md, wiki/concepts/index.md, wiki/entities/index.md

## [2026-08-01] lint

- 24 pages scanned, 0 issues. Report: `wiki/lint-reports/2026-08-01.md`

## [2026-08-01] ingest | Week 1b: A First Model & the Modelling Cycle

- **Source page:** `wiki/sources/w01b-modelling-cycle.md`
- **New concept pages:** abstraction, agent-sensing, counterfactual, model-communication,
  model-structure, occams-razor, pattern-oriented-modelling, research-question,
  search-strategy
- **New entity pages:** heliocentric-model, mercator-projection,
  nasa-black-hole-simulation, oroville-dam-model
- **New material pages:** truffle-foraging-model-design
- **Updated pages:** concepts/modelling-cycle (expanded to the canonical six steps),
  concepts/model, concepts/simulation, concepts/agent-based-model, concepts/optimisation,
  entities/netlogo, all four section indexes

## [2026-08-01] lint

- 40 pages scanned, 0 issues. Report: `wiki/lint-reports/2026-08-01.md`

## [2026-08-02] cue-cards | Week 1 lectures

- **New material pages:** week-01-cue-cards (16 cards: 5 elaborative interrogation,
  4 mechanism, 4 contrast, 3 failure-mode)
- **Derived from:** sources/w01a-introduction, sources/w01b-modelling-cycle, and the
  Week 1 concept pages
- **Updated pages:** materials/index
- **Anki export:** `wiki/materials/week-01-cue-cards.anki.tsv` (gitignored, regenerable)


## [2026-08-06] ingest | Week 2a: Describing Models & Week 2b: Modelling Disease Spread

- **Source pages:** `wiki/sources/w02a-describing-models.md`,
  `wiki/sources/w02b-modelling-disease-spread.md`
- **New concept pages:** odd-protocol, model-scales, scheduling, initial-conditions,
  reproducibility, sir-model, compartmental-model, contact-rate, exponential-growth,
  epidemic-intervention, null-model, model-extension
- **New entity pages:** volker-grimm, grimm-odd-2010, sars-2003-outbreak,
  covid-19-pandemic, doherty-institute
- **New material pages:** zombie-apocalypse-model-design
- **Updated pages:** concepts/model-structure, concepts/modelling-cycle,
  concepts/stochasticity, concepts/model-communication, concepts/research-question,
  entities/andres-munoz, entities/covid-19-abm-australia, all four section indexes

## [2026-08-06] lint

- 61 pages scanned, 0 issues. Report: `wiki/lint-reports/2026-08-06.md`

## [2026-08-08] query | Limitations of SIR compared to an ABM

- **Question:** what are the limitations of an SIR (compartmental/equation-based) model
  compared to an agent-based model?
- **Pages read:** concepts/sir-model, concepts/compartmental-model, concepts/contact-rate,
  concepts/agent-based-model, sources/w02b-modelling-disease-spread
- **New material page:** compartmental-vs-agent-based
- **Updated pages:** concepts/sir-model, concepts/compartmental-model,
  concepts/agent-based-model, materials/index
- **Gap flagged:** no source in the wiki develops the ODE/aggregate formulation directly —
  the aggregate side is reconstructed from one sentence in w02b. A reading on compartmental
  epidemiology would let the comparison cite rather than infer. The "costs of the ABM"
  section is marked in-page as an addition, not derived from ingested content.

## [2026-08-09] cue-cards | Week 2 lectures

- **New material pages:** week-02-cue-cards (16 cards: 6 elaborative interrogation,
  3 mechanism, 2 contrast, 5 failure-mode)
- **Derived from:** sources/w02a-describing-models, sources/w02b-modelling-disease-spread,
  and the Week 2 concept pages (odd-protocol, sir-model, scheduling, contact-rate,
  null-model, model-scales)
- **Updated pages:** materials/index
- **Anki export:** `wiki/materials/week-02-cue-cards.anki.tsv` (gitignored, regenerable)

## [2026-08-16] ingest | Week 3a: Analysing Models

- **Source page:** `wiki/sources/w03a-analysing-models.md`
- **New concept pages:** model-analysis, modelling-for-science, modelling-for-policy,
  summary-statistic, outbreak-summary-measures, bimodal-distribution, stochastic-fadeout
- **New entity pages:** schelling-segregation-model, thomas-schelling,
  influenza-antiviral-stockpile-model
- **Updated pages:** concepts/stochasticity, concepts/tipping-point, concepts/sir-model,
  concepts/modelling-cycle, concepts/epidemic-intervention, entities/netlogo,
  entities/andres-munoz, materials/compartmental-vs-agent-based, sources/index,
  concepts/index, entities/index

## [2026-08-16] ingest | Week 3b: The Reproduction Number and Deterministic Models

- **Source page:** `wiki/sources/w03b-reproduction-number.md`
- **New concept pages:** reproduction-number, herd-immunity-threshold, deterministic-model,
  difference-equation
- **New entity pages:** netlogo-hiv-model
- **Updated pages:** concepts/sir-model, concepts/compartmental-model,
  concepts/exponential-growth, concepts/epidemic-intervention, concepts/tipping-point,
  concepts/stochasticity, entities/netlogo, entities/andres-munoz,
  materials/compartmental-vs-agent-based, sources/index, concepts/index, entities/index
- **Gap closed:** the open question on `materials/compartmental-vs-agent-based` — that the
  aggregate/ODE formulation was reconstructed from one sentence in w02b — is resolved by
  this source, which gives the difference and differential equations directly.
- **Source discrepancies:** the recording differs from the slides on the fadeout example's
  recovery rate (1.4 spoken vs 0.4 on the slide), COVID-19 reproduction numbers by variant,
  and the measles/chickenpox coverage thresholds. Slides taken as authoritative and the
  discrepancies recorded on the source page.

## [2026-08-16] lint | post-ingest check

- **Result:** 81 pages scanned, 0 issues. No dangling links, orphans or index drift.
- **Report:** `wiki/lint-reports/2026-08-16.md`

## [2026-08-16] digest | w03a — Analysing Models

- **Digest page:** `wiki/materials/w03a-analysing-models-digest.md`
- **Built from:** sources/w03a-analysing-models (19-slide deck + recording transcript)
- **Updated pages:** sources/w03a-analysing-models (digest backlink), materials/index
- **Anchors:** slide numbers only. The supplied transcript carries no time markers and the
  source page holds a Canvas course link rather than a recording URL, so timestamp anchors
  could not be produced.

## [2026-08-16] digest | w03b — The Reproduction Number and Deterministic Models

- **Digest page:** `wiki/materials/w03b-reproduction-number-digest.md`
- **Built from:** sources/w03b-reproduction-number (23-slide deck + recording transcript)
- **Updated pages:** sources/w03b-reproduction-number (digest backlink), materials/index
- **Anchors:** slide numbers only, as above.
- **Note:** the slide/recording discrepancies recorded on the source page are reproduced as a
  table at the top of the digest, since three of them are exam-relevant numbers.- **Lint:** 84 pages scanned, 0 issues. Report at `wiki/lint-reports/2026-08-16.md`.

## [2026-08-16] cue-cards | Week 3 lectures

- **New material page:** week-03-cue-cards (38 cards: 15 elaborative interrogation,
  7 mechanism, 6 contrast, 10 failure-mode)
- **Derived from:** sources/w03a-analysing-models, sources/w03b-reproduction-number, their
  digests, and the Week 3 concept pages (reproduction-number, herd-immunity-threshold,
  deterministic-model, difference-equation, stochastic-fadeout, bimodal-distribution,
  summary-statistic, outbreak-summary-measures, model-analysis, modelling-for-science,
  modelling-for-policy)
- **Updated pages:** materials/index
- **Anki export:** `wiki/materials/week-03-cue-cards.anki.tsv` (gitignored, regenerable)
- **Note:** deliberately larger than the 16-card Week 1 and Week 2 decks — Week 3b is the
  subject's only quantitative lecture, so formulas, derivations and interpretations each
  need separate cards. One card covers the slide/recording discrepancies themselves, since
  three of the four are examinable numbers.
- **Lint:** 85 pages scanned, 0 issues.
