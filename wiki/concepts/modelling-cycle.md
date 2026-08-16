---
title: Modelling Cycle
type: concept
tags: [methodology, abm]
date: 2026-08-01
---

# Modelling Cycle

The modelling cycle is the iterative methodology by which a [[model]] is designed,
implemented and applied: formulate a question, assemble hypotheses, choose a structure,
implement, analyse and revise, and communicate — returning to earlier steps as the work
demands.

## How it works

The six canonical steps:

1. **Formulate the question.** A clear research question provides the focus for the model
   and decides what to include and leave out. It must be non-trivial and actually
   answerable by a model — "if the temperature rises, should I wear lighter clothes?"
   needs no model. This is named the hardest step. See [[research-question]].
2. **Assemble hypotheses for essential processes and structures.** Research and brainstorm
   what must go into the model — read papers, go into the field, ask domain experts. Keep
   this open-ended at first, then filter. The governing heuristic is **start simple**: a
   simple behaviour may be two or three lines of code, whereas building everything at once
   produces a mass of bugs. Details are added later, in priority order.
3. **Choose scales, entities, state variables, processes and parameters.** Translate the
   hypotheses into equations, rules or algorithms, and produce a *written outline* before
   any code. See [[model-structure]].
4. **Implement the model.** The technical phase of turning the written design into a
   runnable [[simulation]]. This phase reveals the consequences of the assumptions made
   earlier — often uncomfortably.
5. **Analyse, test and revise.** Use the model to answer the motivating question. Typically
   the most time-consuming step, and it frequently forces reformulation of the question and
   revision of the model. If the model doesn't reproduce the behaviour it should, that is
   itself information — it points at a mechanism that is wrong or uncontrolled.
6. **Communicate the model.** Convey the insight to the relevant stakeholders. See
   [[model-communication]].

The standard diagram draws this as a clean loop with "Patterns!" marked at two transitions
— between assembling hypotheses and choosing structure, and between analysis and
communication. The loop is somewhat misleading: **any step can send you back to any
earlier step**. You may reach implementation and discover the question was wrong, or begin
choosing structure and realise something essential was omitted.

## Why it matters

The cycle makes model building an empirical practice rather than a one-shot translation
from system to code. It enforces checking the model against patterns instead of trusting
its plausibility, and it establishes that a first model is *expected* to be wrong. For
coursework it is also the implicit structure of both projects — question, design,
implementation, analysis, report.

Week 3 develops step 5 into a practice with its own structure ([[model-analysis]]). Analysis
means both establishing that the model is correct and using it on the problem, and getting
there requires moving from playing with parameters to designing experiments that vary
parameters, initial conditions and seeds systematically from a baseline. The same week also
distinguishes two purposes the cycle can serve — [[modelling-for-science]], which tests
whether hypothesised individual behaviours reproduce an observed pattern, and
[[modelling-for-policy]], which assumes a validated model and uses it to project the effects
of candidate interventions.

Where ODD helps in the cycle was also revisited: primarily at choosing model structure,
implementing, and communicating, rather than at formulating the question, since the question
and hypotheses precede writing the description.

The [[odd-protocol]] occupies the transition from step 2 to step 3: it is the mechanism
for turning brainstormed hypotheses into a formal written model structure. Week 2 also
supplies the lecturer's reasons for the cycle being iterative — the question may need
reformulating, the implementation may contain errors, or the model may simply not produce
the behaviour of interest. The later stages connect to calibration, sensitivity and
uncertainty analysis in weeks 10–12.

## Relationships

- [[odd-protocol]] — spans the step 2 → step 3 transition
- [[model-extension]] — iterating the cycle by adding one element at a time
- [[research-question]] — step 1, and the hardest
- [[model-structure]] — step 3
- [[model-communication]] — step 6
- [[pattern-oriented-modelling]] — how "Patterns!" enters the cycle
- [[abstraction]], [[occams-razor]] — the principles governing what goes in
- [[model]], [[simulation]], [[agent-based-model]] — what is being built
- [[stochasticity]] — verification of a stochastic model requires replication
- [[truffle-foraging-model-design]] — a worked pass through the early steps
- [[model-analysis]] — step 5 in detail
- [[modelling-for-science]], [[modelling-for-policy]] — the two purposes the cycle serves

## Sources

- [[w01b-modelling-cycle]] — the canonical six-step presentation, with the caveat that the
  loop is not strictly sequential, and emphasis on question formulation and communication.
- [[w01a-introduction]] — earlier, briefer sketch of the cycle as hypothesis → build →
  verify → refine.
- [[w02a-describing-models]] — locates ODD between steps 2 and 3, and gives three reasons
  the cycle iterates: wrong question, implementation errors, absent target behaviour.
