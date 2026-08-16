---
title: Modelling for Science
type: concept
tags: [modelling-cycle, abm, epistemology]
date: 2026-08-16
---

# Modelling for Science

Using a model for scientific purposes means using it to understand a mechanism, following
the inductive approach: observe, question, hypothesise, predict, test, analyse and conclude
or repeat. In agent-based modelling the hypotheses take a particular form — individual-level
behaviours proposed as explanations for population-level phenomena.

## How it works

The six steps as taught:

1. **Observe** — what don't we understand?
2. **Question** — usually beginning "why?" or "how?"
3. **Hypothesise** — alternative answers to that question
4. **Predict** — what does each hypothesis imply?
5. **Test** — evaluate the predictions
6. **Analyse and conclude** — or return to step 1

What makes this specifically agent-based is step 3. The hypothesis is not a statement about
aggregate quantities but about what individuals do, implemented as agent rules. The test is
then whether running those rules reproduces the observed population-level pattern
([[emergence]], [[pattern-oriented-modelling]]).

The [[schelling-segregation-model]] is the worked case. The observation is that residential
segregation persists even among populations who profess not to discriminate. The question is
how to explain it. The hypothesis is that mild individual preferences about neighbours are
sufficient — no discriminatory intent required. The prediction is that such preferences
produce increasingly homogeneous neighbourhoods. The test runs scenarios varying the
strength of preference and measuring homogeneity. The conclusion is that the hypothesis is
plausible: a 30% same-type threshold produces neighbourhoods around 73% homogeneous.

Note what "plausible" is doing there. Reproducing the pattern establishes that the
hypothesised mechanism is *sufficient* to generate it, not that it is the mechanism actually
operating. This is the standard epistemic limit of generative explanation, and it is why the
cycle loops rather than terminating.

## Why it matters

The distinguishing feature against [[modelling-for-policy]] is that science modelling does
not try to change the system. Schelling's model asks why segregation occurs; the policy
version of the same problem asks what a government could do about it. The model may be
identical, but the experiments differ — a scientific study varies the hypothesised mechanism
to see whether the pattern survives, while a policy study varies interventions to see which
performs best.

The distinction also shapes what counts as a good result. A negative finding is scientifically
useful (the hypothesised mechanism does not reproduce the pattern, so it is not sufficient),
whereas a policy analysis needs a comparison between actions.

## Relationships

- [[modelling-for-policy]] — the other purpose, contrasted throughout Week 3
- [[modelling-cycle]] — the modelling-specific version of this loop
- [[schelling-segregation-model]] — the worked instance
- [[emergence]] — population-level pattern from individual-level rules
- [[pattern-oriented-modelling]] — patterns as the test criterion
- [[research-question]] — step 2 in practice
- [[agent-based-model]] — the implementation form for the hypotheses
- [[model-analysis]] — steps 5 and 6

## Sources

- [[w03a-analysing-models]] — sets out the inductive approach, states that hypotheses are
  posed as individual-level behaviours evaluated on their ability to reproduce observed
  patterns, and works the segregation model through all six steps.
