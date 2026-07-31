---
title: Occam's Razor
type: concept
tags: [foundations, model-design, philosophy-of-science]
date: 2026-08-01
---

# Occam's Razor

Occam's razor is the principle that when two explanations account for the same
observations, the simpler one should be preferred.

## How it works

In modelling this is a design criterion, not merely a philosophical preference: given two
models that answer the question equally well, take the one with fewer moving parts.

The canonical demonstration is the geocentric-versus-heliocentric pair
([[heliocentric-model]]). Both were built for the same purpose — explaining the observed
motion of the planets. The geocentric model could do it, but only by adding **epicycles**:
small secondary orbits layered on the main orbits, needed to account for planets appearing
to reverse direction in the sky. Placing the Sun at the centre made that machinery
unnecessary. The simpler model explained the same observations *better*, and the extra
complexity turned out to be an artefact of the wrong starting assumption.

The lesson generalises: unnecessary complexity in a model is often a symptom of a wrong
structural choice elsewhere, not a sign of thoroughness. When a model needs increasingly
baroque additions to fit, that is a reason to re-examine its foundations — which in the
[[modelling-cycle]] means returning to step 1 or 2.

## Why it matters

It supplies the justification for the subject's repeated instruction to *start simple*.
Simplicity is not just cheaper to implement and debug; it is more likely to be right, and
it makes the mechanism producing the behaviour visible rather than buried under detail.

## Relationships

- [[abstraction]] — the practice; Occam's razor is the principle behind it
- [[heliocentric-model]] — the worked example
- [[model]] — simplicity is judged relative to purpose
- [[modelling-cycle]] — applied when assembling hypotheses and choosing structure

## Sources

- [[w01b-modelling-cycle]] — introduced via the geocentric/heliocentric contrast, with
  epicycles as the concrete cost of the more complex model.
