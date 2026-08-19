---
title: "Assignment 1: Project Specification"
type: source
source_type: other
link: https://canvas.lms.unimelb.edu.au/courses/239814
tags: [comp90083, assignment-1, assessment, odd-protocol, model-extension, netlogo]
date: 2026-08-19
---

# Assignment 1: Project Specification

## Overview

The written brief for the subject's first project, released 3 August 2026 and due 23:59 on
Sunday 30 August 2026. It is worth 20% of the subject and is done individually. The task:
take a provided NetLogo agent-based model of infection spreading through a population,
extend it, and use the extension to answer a research question the baseline SIR model
cannot answer. The brief is explicit that the assessment is on modelling reasoning,
justification and communication rather than on how much code gets written.

Three deliverables sit behind that. A research question relevant to science or policy; a
modified [[netlogo]] model file; and a single integrated report of about 1,200 words written
against a supplied LaTeX template, using the [[odd-protocol]] as its organising structure.
The report is the marked artifact — the model file is uploaded for verification and is not
independently marked, though a model that doesn't implement the stated extension, or whose
results can't be reproduced from it, is penalised under the modelling-choices and
experimental-design criteria.

The brief's sharpest constraint is on what counts as an extension. Changing parameter
values, thresholds, or initial conditions is not enough. The extension must add at least one
process that alters how agents transition between states, interact, or respond to system
conditions over time — a change to the model's generative dynamics, which may require new
agent state variables. The brief gives one suitable question (delayed infectiousness after
infection, changing outbreak timing and shape) and one unsuitable one (how infection or
recovery probability affects total outbreak size), and the difference between them is
exactly this structural test, not the topic.

Experimental design carries its own requirement: vary one key parameter of the extension
across a couple of values and report how behaviour changes. The brief frames this as
checking how sensitive the results are to the extension's design choices, not as a
formal sensitivity analysis.

## Key concepts

- [[research-question]] — task 1; must be answerable by simulation and not by baseline SIR
- [[model-extension]] — the structural change at the centre of the task
- [[odd-protocol]] — the required framework for describing the model
- [[model-communication]] — the stated audience is technical but non-specialist
- [[sir-model]] — the baseline being extended, and the source of its own critique list
- [[agent-based-model]] — the modelling paradigm of the provided model
- [[abstraction]] — task 2, identifying the relevant entities, processes and interactions
- [[sensitivity-analysis]] — the "vary one key parameter across a couple of values" requirement
- [[reproducibility]] — the model file exists so reported results can be re-derived
- [[epidemic-intervention]] — one of the named gaps in the baseline model

## Key entities

- [[netlogo]] — the platform for the provided and extended model
- [[covid-19-pandemic]] — the motivating example in the background section

## Topics covered (revision checklist)

- Assessment weight (20%), release date (3 Aug 2026), due date (23:59 Sun 30 Aug 2026)
- Individual work; discussion allowed, sharing code or writing not
- Six numbered tasks: pose question; analyse and abstract the system; extend the NetLogo
  model; justify decisions and assumptions; design and run experiments; write the report
- Approach sequence: understand the baseline model, read the recommended readings, formulate
  the question, analyse the baseline against it, decide the extension, design the experiments
- Named limitations of baseline SIR: no loss of protective immunity, no per-person risk
  factors, no interventions, no behavioural variation such as compliance
- What counts as an extension vs what does not (structure vs parameters)
- Deliverables: NetLogo model file plus a single integrated report, uploaded separately (not
  zipped), both carrying name and student number
- Word limit ~1,200, excluding tables, figure captions, references and the AI declaration;
  the template's pre-filled baseline ODD description (~704 words of prose, 37 of headings)
  does not count
- Mandatory LaTeX template from Canvas; word count must be stated
- GenAI policy: permitted for brainstorming, finding sources, light editing; not for
  generating or substantially paraphrasing written content, and not for writing model code.
  A declaration covering tools, purpose, representative prompts and influence on modelling
  decisions is mandatory and is itself assessed
- Citations require a linked DOI
- Late penalty: 2 marks per day or part thereof; extensions via the Faculty process
- Two-mark deduction for failing the file-submission requirements
- Marking criteria C1–C5 and their weights
- Suggested report section structure with per-section word budgets
- The two illustrative boundary-case questions

## Notable claims / results

- Marking, out of 20: C1 problem formulation and abstraction (4), C2 modelling choices and
  structural extension (6), C3 evaluation of assumptions and limitations (4), C4 experimental
  design and interpretation (4), C5 communication and model explanation (2).
- C2 is the largest single criterion, which matches the brief's repeated insistence that the
  extension be structural.
- Suggested word budgets: title ~25, background ~250–300, question ~25, model ~300–350,
  modelling decisions ~150–200, experimental design ~200–250, results ~100, discussion
  ~200–250. That sums to roughly 1,250–1,500, so the ~1,200 target implies trimming
  somewhere; the budgets are a shape, not an addition.
- The results section is budgeted at ~100 words and one or two figures or tables. Most of
  the marks sit in reasoning around the results, not the results themselves.
- Realism is explicitly not required: "So long as your question is broadly 'on topic' and can
  be addressed via an extended SIR model, you are free to be creative." No expectation of
  real-world completeness or novelty.
- Figures and tables are to be placed at the top of the page.

## Connections

The Week 2a lecture ([[w02a-describing-models]]) briefed this assignment verbally and
introduced the ODD protocol it requires; the Week 2b lecture
([[w02b-modelling-disease-spread]]) produced the SIR critique list that doubles as a menu of
candidate extensions. [[w03a-analysing-models]] and [[w03b-reproduction-number]] supply the
analysis side — [[outbreak-summary-measures]] are the natural outputs to measure, and
[[stochastic-fadeout]] is the reason a single run is not an answer.

`See also:` [[model-extension]] · [[research-question]] · [[odd-protocol]] ·
[[sir-model]] · [[netlogo]] · [[sensitivity-analysis]] · [[model-analysis]]
