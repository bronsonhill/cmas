---
title: TRACE Documentation
type: concept
tags: [methodology, model-description, documentation, odd]
date: 2026-08-19
---

# TRACE Documentation

TRACE — TRAnsparent and Comprehensive model Evaluation — is a standard format for documenting
the whole modelling process: development, testing, parameterisation, analysis and
application. Where an [[odd-protocol]] description says what the model is, a TRACE document
says what was done to it and what evidence supports trusting it.

## How it works

A TRACE document collects the material an ODD deliberately leaves out — the rationale for
each design decision, the data and calibration behind each parameter value, the tests run on
each submodel, the sensitivity analyses, and the evaluation of whether the model is fit for
its stated purpose ([[sensitivity-analysis]], [[model-analysis]]). It is normally a
supplement rather than main text, and it typically contains an ODD inside it.

The 2020 ODD update recommends TRACE as the place to put design rationale when including it
inline would make the ODD unreadable ([[grimm-2020-odd-second-update]]). The same update
adds optional "Rationale" subsections to each ODD element, so the two overlap by design and
the choice is one of length rather than kind.

## Why it matters

A complete model description does not by itself establish that the model is any good.
Reproducing someone's model exactly and getting their results back proves only that the code
matches the description ([[reproducibility]]). TRACE exists to make the evidential trail —
why these parameters, which tests passed, what the model was checked against — as inspectable
as the model structure.

## Relationships

- [[odd-protocol]] — describes the model; TRACE describes the process around it
- [[reproducibility]] — the underlying motivation for both
- [[model-analysis]] — the analyses a TRACE document records
- [[pattern-oriented-modelling]] — one of the evaluation strategies documented
- [[model-communication]] — the audience question that separates the two formats

## Sources

- [[grimm-2020-odd-second-update]] — positions TRACE as the companion format for rationale
  and evaluation, and supplies two example TRACE documents.
