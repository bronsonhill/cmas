---
title: Research Question
type: concept
tags: [methodology, model-design]
date: 2026-08-01
---

# Research Question

The research question is the problem a [[model]] is built to answer. It is step 1 of the
[[modelling-cycle]] and the step that determines the model's scope — what must be included
and what may be left out.

## How it works

A good research question is:

- **Specific.** "What is an efficient strategy for foraging mushrooms?" is too broad to
  constrain a design. Narrowing it to *truffles* immediately changes the model: truffles
  grow underground and do not cluster, which rules out a greedy [[search-strategy]] and
  requires a smell-based [[agent-sensing]] mechanism. The more self-contained the question,
  the better-scoped the model.
- **Non-trivial.** It must actually need a model. "If the temperature rises, do I need
  lighter clothing?" is answerable without one.
- **Motivated.** There is a reason to want the answer — it did not come from nowhere.
  Examples raised: should Melbourne lock down to limit COVID? Should we invest in a given
  stock? How will a change in housing tax affect the neighbourhood?
- **Answerable by a model.** The question must be of a kind that simulation can address.

Formulating this well is named the **hardest step** in the cycle, and the one students
struggled with most in previous years' assignments. The payoff is that a clear question
does the work of deciding the rest of the design: scales, entities, which processes matter.

## Why it matters

Almost every downstream modelling decision traces back to the question. A vague question
produces a model with no principled basis for inclusion or exclusion, which is how models
sprawl. The lecturer named this failure mode directly in Week 2 as **scope creep**, the
project-management term for a task whose boundaries were never specified: the question is
what fixes the scope, and the model is finished when it answers the question rather than
when it runs out of features to add. For coursework, both projects require formulating a
question, and it is where marks are most readily lost.

## Relationships

- [[modelling-cycle]] — step 1
- [[odd-protocol]] — the question becomes the Purpose section
- [[model-extension]] — each extension should be motivated by a question
- [[model]] — purpose, of which the research question is the operational form
- [[abstraction]] — the question licenses the simplifications
- [[model-structure]] — what the question is translated into
- [[truffle-foraging-model-design]] — worked example of narrowing a question

## Sources

- [[w01b-modelling-cycle]] — presented as the hardest and most important step, with the
  mushroom/truffle narrowing as the demonstration.
- [[w02a-describing-models]] — the scope-creep argument for defining the question first,
  and the Assignment 1 requirement to state a research question.
- [[a1-project-specification]] — task 1 of the assignment; the question must be unanswerable
  by baseline SIR, which is what forces a structural extension.
