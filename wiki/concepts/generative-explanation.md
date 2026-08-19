---
title: Generative Explanation
type: concept
tags: [abm, methodology, emergence, modelling-philosophy]
date: 2026-08-19
---

# Generative Explanation

Generative explanation is the claim that you have explained a macroscopic regularity when you
can grow it: a population of heterogeneous agents following plausible local rules produces
the large-scale pattern without it being written into the rules. [[joshua-epstein]]'s slogan
is "if you didn't grow it, you didn't explain it."

## How it works

The explanandum is a system-level regularity — a wealth distribution, a spatial settlement
pattern, an epidemic curve, residential segregation. The explanans is a set of agent-level
behavioural rules plus an interaction structure. Running the model constitutes the
explanation: the pattern appears in the aggregate output although no agent has any
representation of it ([[emergence]], [[agent-based-model]]).

[[schelling-segregation-model]] is the canonical case. Segregation emerges from a mild
same-neighbour preference; no agent wants a segregated city, and one still forms. That result
is an explanation of a sufficient mechanism, and it says nothing about which cities will
segregate or when.

The standard is sufficiency, not uniqueness. Growing a pattern shows the mechanism *can*
produce it, which is a candidate explanation rather than a proof that reality works this way
— another rule set may generate the same pattern. This is why the criterion sits alongside
[[pattern-oriented-modelling]]: matching several patterns at once narrows the field of
sufficient mechanisms considerably.

## Why it matters

It gives agent-based modelling a defensible epistemic role that regression cannot fill. A
statistical fit relates aggregates to aggregates; a generative model states a mechanism at
the level where the behaviour actually happens and derives the aggregate from it. It also
explains why an ABM can be valuable while predicting nothing
([[explanation-vs-prediction]]).

## Relationships

- [[emergence]] — the phenomenon generative explanation exploits
- [[explanation-vs-prediction]] — what this kind of explanation does and does not buy
- [[agent-based-model]] — the modelling paradigm it justifies
- [[schelling-segregation-model]] — the worked example
- [[pattern-oriented-modelling]] — the discipline that constrains sufficient mechanisms
- [[complex-system]] — the class of systems where local rules and global pattern diverge

## Sources

- [[epstein-2008-why-model]] — introduces the term, with the Anasazi reconstruction as the
  data-driven example, and separates it explicitly from prediction.
