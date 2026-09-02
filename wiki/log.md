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

## [2026-08-19] ingest | Assignment 1: Project Specification

- **Source page:** `wiki/sources/a1-project-specification.md`
- **New concept pages:** sensitivity-analysis
- **New entity pages:** none
- **Updated pages:** concepts/model-extension, concepts/research-question,
  concepts/odd-protocol, concepts/model-communication, sources/index, concepts/index
- **Note:** the written brief for the assignment [[w02a-describing-models]] briefed verbally.
  Recorded under `link-only` — no text from the PDF is reproduced, and the marking criteria
  are summarised as weights rather than quoted descriptions.
- **Lint:** 87 pages scanned, 0 issues. Report at `wiki/lint-reports/2026-08-19.md`.

## [2026-08-19] ingest | Epstein (2008) "Why Model?" and Grimm et al. (2020) ODD second update

- **Source pages:** `wiki/sources/epstein-2008-why-model.md`,
  `wiki/sources/grimm-2020-odd-second-update.md`
- **New concept pages:** explanation-vs-prediction, generative-explanation, trace-documentation
- **New entity pages:** joshua-epstein, sugarscape
- **Updated pages:** concepts/odd-protocol (new "What the 2020 update changed" section),
  concepts/pattern-oriented-modelling, concepts/sensitivity-analysis, concepts/model,
  concepts/modelling-for-policy, concepts/reproducibility, concepts/model-communication,
  concepts/emergence, entities/volker-grimm, entities/grimm-odd-2010, sources/index,
  concepts/index, entities/index
- **Note:** both papers are open-access JASSS articles, so they are summarised more fully than
  copyright course material would be; still no verbatim text beyond short attributed phrases.
- **Discrepancy recorded:** the Week 2a lecture teaches ten design concepts; the 2020 protocol
  lists eleven (learning and prediction separate). Flagged on `concepts/odd-protocol`.
- **Lint:** 95 pages scanned, 0 issues. Report at `wiki/lint-reports/2026-08-19.md`.

## [2026-08-20] digest | Epstein (2008) and Grimm et al. (2020)

- **New material pages:** epstein-why-model-digest, grimm-2020-odd-second-update-digest
- **Built from:** sources/epstein-2008-why-model (JASSS 11(4) 12, 17 paragraphs),
  sources/grimm-2020-odd-second-update (JASSS 23(2) 7, sections 1-6)
- **Updated pages:** both source pages (digest backlinks), materials/index
- **Anchors:** JASSS paragraph numbers, not timestamps — both sources are papers, so there is
  no recording to align against and no transcript-only layer to surface.
- **Note:** Epstein's sixteen reasons and Grimm's summary-ODD recipe are reproduced in full
  rather than compressed; they are the parts a reader would otherwise go back to the original
  for. The ten-vs-eleven design concepts discrepancy against the Week 2a lecture is called out
  in both the Grimm digest and on concepts/odd-protocol.- **Lint:** 97 pages scanned, 0 issues. Report at `wiki/lint-reports/2026-08-20.md`.

## [2026-08-23] ingest | Week 4a: Complex Systems & Emergence

- **Source page:** `wiki/sources/w04a-complex-systems-and-emergence.md`
- **New concept pages:** self-organisation, decentralisation, feedback, chaos
- **New entity pages:** craig-reynolds
- **Updated pages:** concepts/complex-system, concepts/emergence, concepts/flocking,
  entities/boids, entities/andres-munoz, sources/index, concepts/index, entities/index

## [2026-08-23] ingest | Week 4b: 2D Cellular Automata

- **Source page:** `wiki/sources/w04b-2d-cellular-automata.md`
- **New concept pages:** cellular-automaton, game-of-life, wolfram-classes,
  turing-completeness, lotka-volterra-model
- **New entity pages:** john-von-neumann, stanislaw-ulam, conways-game-of-life,
  stephen-wolfram, alfred-lotka, vito-volterra
- **Updated pages:** concepts/complex-system, concepts/emergence, entities/andres-munoz,
  sources/index, concepts/index, entities/index

## [2026-08-23] ingest | Sayama (2015), Introduction to the Modeling and Analysis of Complex Systems — Chapter 1

- **Source page:** `wiki/sources/sayama-2015-modeling-and-analysis-of-complex-systems-ch1.md`
- **New concept pages:** none (concepts already created from the Week 4a/4b lectures)
- **New entity pages:** hiroki-sayama
- **Updated pages:** concepts/complex-system, concepts/emergence, sources/index,
  entities/index
- **Note:** open-access CC BY-NC-SA textbook (Open SUNY / Milne Publishing), summarised
  more fully than copyright course material would be, consistent with treatment of the
  Epstein and Grimm open-access papers. Only Chapter 1 was read; the rest of the book is
  out of scope for this ingest.

## [2026-08-23] lint

- **Lint:** 118 pages scanned, 0 issues. Report at `wiki/lint-reports/2026-08-23.md`.

## [2026-08-23] digest | Week 4a, Week 4b, Sayama Ch. 1

- **Digest pages:** `wiki/materials/w04a-complex-systems-and-emergence-digest.md`,
  `wiki/materials/w04b-2d-cellular-automata-digest.md`,
  `wiki/materials/sayama-2015-modeling-and-analysis-of-complex-systems-ch1-digest.md`
- **Updated pages:** `wiki/sources/w04a-complex-systems-and-emergence.md`,
  `wiki/sources/w04b-2d-cellular-automata.md`,
  `wiki/sources/sayama-2015-modeling-and-analysis-of-complex-systems-ch1.md` (digest
  back-links added), `wiki/materials/index.md`

## [2026-08-23] cue-cards | Week 4

- **Deck:** `wiki/materials/week-04-cue-cards.md` (+ `.anki.tsv` export, 28 cards)
- **Source pages:** `wiki/sources/w04a-complex-systems-and-emergence.md`,
  `wiki/sources/w04b-2d-cellular-automata.md`,
  `wiki/sources/sayama-2015-modeling-and-analysis-of-complex-systems-ch1.md`
- **Updated pages:** `wiki/materials/index.md`
- **Note:** balanced technical/mechanism cards (CA rule numbering, Wolfram-class
  identification, Life's update algorithm, Lotka-Volterra ODEs and their discrete
  reformulation) against conceptual cards (emergence vs self-organisation,
  decentralisation, complex-system classification) per explicit user requirement.

## [2026-08-23] lint | combined pass after digests and cue-cards

- **Lint:** 1 dangling link found (`materials/week-04-cue-cards` → `[[logistic-map]]`),
  fixed by creating `wiki/concepts/logistic-map.md` (promoted from an inline mention on
  the w04a source page to a full concept page) and linking it from
  `wiki/sources/w04a-complex-systems-and-emergence.md` and `wiki/concepts/index.md`.
  Re-run: 124 pages scanned, 0 issues. Report at `wiki/lint-reports/2026-08-23.md`.

## [2026-08-30] ingest | Week 5 — modelling agent behaviour (sensing, adaptation, objectives)

- **Source pages:** `wiki/sources/w05a-sensing.md`,
  `wiki/sources/w05b-adaptation-and-objectives.md`,
  `wiki/sources/kennedy-2012-modelling-human-behaviour.md`
- **New concept pages:** `adaptive-behaviour`, `objective-function`, `agent-learning`,
  `agent-prediction`, `agent-interaction`, `collectives`, `agent-neighbourhood`,
  `imperfect-information`, `bounded-rationality`, `rational-choice-theory`,
  `threshold-rule`, `cognitive-architecture`, `bdi-architecture`, `pecs-framework`,
  `fast-and-frugal-heuristics`, `social-influence`
- **New entity pages:** `william-kennedy`, `herbert-simon`, `gerd-gigerenzer`, `soar`,
  `act-r`, `business-investment-model`
- **Updated pages:** `concepts/agent-sensing.md` (three sensing questions, variable
  scope table), `concepts/satisficing.md` (satisficing thresholds; why it can beat
  greedy optimisation), `concepts/optimisation.md`, `concepts/odd-protocol.md` (design
  concepts now linked to their own pages), `concepts/cellular-automaton.md` ($S^{S^N}$
  rule-count generalisation), `concepts/scheduling.md`, `concepts/stochasticity.md`,
  `entities/andres-munoz.md`, `entities/netlogo.md`, all three section indexes
- **Not ingested:** Tutorial 4 (BehaviorSpace) materials from the same Canvas folder —
  tutorials have not been ingested in previous weeks. Flag if that should change.

## [2026-08-30] lint | after Week 5 ingest

- **Lint:** 149 pages scanned, 0 issues. Report at `wiki/lint-reports/2026-08-30.md`.

## [2026-09-02] digest | w05a, w05b, Kennedy (2012) — modelling agent behaviour

- **Digests:** `wiki/materials/w05a-sensing-digest.md`,
  `wiki/materials/w05b-adaptation-and-objectives-digest.md`,
  `wiki/materials/kennedy-2012-modelling-human-behaviour-digest.md`
- **Source pages:** `wiki/sources/w05a-sensing.md`,
  `wiki/sources/w05b-adaptation-and-objectives.md`,
  `wiki/sources/kennedy-2012-modelling-human-behaviour.md` (digest back-links added)
- **Updated pages:** `wiki/materials/index.md`
- **Note:** first digests with real recording timestamps — the VTT transcripts were
  re-parsed keeping cue times, so every spine section carries `slides N–M` plus `MM:SS`.
  Canvas recordings have no linkable URL, so timestamps are plain rather than clickable.
- **Contradiction flagged:** the Week 5b recording says at `22:08` that agents become
  "less risk averse" late in a run; the plotted output, the $(1-F)^T$ mechanism and the
  Week 5a statement all say *more*. Recorded as an open thread in the w05b digest rather
  than silently corrected.
