---
title: "Grimm et al. (2020) — The ODD Protocol: A Second Update"
type: source
source_type: paper
link: https://www.jasss.org/23/2/7.html
tags: [comp90083, reading, odd, model-description, abm, grimm]
date: 2026-08-19
---

# Grimm et al. (2020) — The ODD Protocol: A Second Update

## Overview

The current version of the [[odd-protocol]], published in *JASSS* 23(2) 7 (doi
10.18564/jasss.4259) by [[volker-grimm]] and seventeen co-authors including Steven Railsback
and Bruce Edmonds. Open access. Subtitle: *A Second Update to Improve Clarity, Replication,
and Structural Realism*. It follows the 2006 original and the 2010 first update
([[grimm-odd-2010]], the subject's assigned version).

The paper is unusual in being mostly a diagnosis of its own protocol's failure modes. ODD
was adopted far more widely than its authors expected, and the authors went and read a lot
of the resulting ODDs. The problems they found: guidance materials existed only as a
supplement to a paywalled 2010 paper and were rarely used; modellers described their mental
model rather than what the program actually does, producing descriptions too incomplete to
re-implement; ODDs run long (5–10 pages typically, 30–40 for complex models) so authors
substitute a summary and offer code on request; there was no format for describing a model
that re-uses parts of an existing one; and ODD had no clear link to either the model's code
or to [[pattern-oriented-modelling]].

The fixes are mostly structural additions rather than changes to the seven elements. Element
1 is renamed **"Purpose and patterns"**, so the patterns used to design and evaluate the
model are stated up front, before the entities and state variables that were chosen on the
basis of those patterns. Every element gains an optional **"Rationale"** subsection for why
the design decision was made, not just what it was. New supplements provide a full guidance
document and checklists (S1), a template for a **summary ODD** that fits a journal article
with the full ODD in supplementary material (S2), **nested ODDs** for submodels that need ten
or more pages of their own (S3), guidance on ODDs for **modified models** including the
"delta-ODD" that describes only what changed (S4), a licence template so ODD text can legally
be re-used (S5), example TRACE documents (S6), and a template for describing simulation
experiments (S7).

The motto for the incompleteness problem is worth memorising: *describe what the program
does, not what you think the model does*. The authors also recommend naming conventions and
comments that let a reader move between the ODD and the code, on the grounds that code is the
most authoritative description a model has and pretending otherwise makes ODDs ambiguous.

The closing argument is expansionary: only the design concepts are specific to ABMs, so ODD
could in principle describe any simulation model and become a lingua franca for simulation
modelling generally.

## Key concepts

- [[odd-protocol]] — the subject of the paper
- [[pattern-oriented-modelling]] — now explicitly linked into ODD element 1
- [[model-communication]] — the protocol's original purpose
- [[reproducibility]] — the replication crisis is the paper's framing motivation
- [[trace-documentation]] — the companion format for documenting the whole modelling process
- [[model-structure]] — what an ODD formalises
- [[emergence]], [[stochasticity]], [[agent-sensing]] — three of the eleven design concepts

## Key entities

- [[volker-grimm]] — lead author
- [[grimm-odd-2010]] — the version this updates, and the one set as subject reading
- [[netlogo]] — named as a platform whose primitives must be understood to read model code

## Topics covered (revision checklist)

- The seven ODD elements and the three categories O / D / D; the numbering is to be used as
  given
- Eleven design concepts: basic principles, emergence, adaptation, objectives, learning,
  prediction, sensing, interaction, stochasticity, collectives, observation. Unused ones may
  be omitted; new ones of general interest may be appended
- Element 1 renamed "Purpose and patterns"; patterns as evaluation criteria stated up front
- Optional "Rationale" subsection in each element
- Why ODD spread unevenly across disciplines (Figure 2: growth mainly in the life sciences,
  flat overall since 2011)
- The five issues: guidance scarcity, mental-model descriptions, length, re-use, ambiguity
  relative to code — plus the missing POM link
- Summary ODD: start from the three overview elements, narrative form, ODD keywords
  italicised, drop section titles, full ODD always written first
- Nested ODD: a submodel described with a reduced ODD (elements 1, 3, 7)
- Delta-ODD, and when it is inappropriate (original ODD not freely available)
- Licensing ODD text for re-use; copyleft and no-warranty clauses
- Linking ODD to code: shared naming conventions, comments, hyperlinked ODD-plus-code
  documents, tables mapping elements to file and procedure
- TRACE as the wider documentation format; ODD as the "Materials" half of Materials and
  Methods, with simulation experiments as the "Methods" half
- Outlook: ODD for non-ABM simulation models, automated ODD-to-code links and why they are
  risky, who maintains ODD long term (CoMSES/OpenABM), certification of ODD reviewers

## Notable claims / results

- ODD's seven elements are unchanged by this update. What changed is element 1's name and
  scope, the optional rationale subsections, and the surrounding guidance.
- The design concepts are the only genuinely ABM-specific part of the protocol — everything
  else applies to any simulation model. This is the basis for the lingua franca claim.
- Typical ODDs run 5–10 pages; complex ones exceed 30–40. Length is the practical reason
  ODDs end up in supplements where they are neither reviewed nor read carefully.
- The 2006 paper had 2,258 Google Scholar citations and the 2010 one 1,783 as of November
  2019.
- Deciding which processes to represent as adaptive decision-making is called out as a
  critical design decision that must be made carefully and justified — usually only a few
  processes can be modelled this way.
- Reporting only the patterns a model does reproduce, while omitting ones it was expected to
  reproduce and failed to, is described as resembling HARKing. Missing patterns should be
  reported.

## Connections

Read against [[grimm-odd-2010]], this is a same-skeleton update: nothing students learned in
[[w02a-describing-models]] is invalidated, but the lecture's "ten design concepts" is eleven
here (learning and prediction are separate), and the lecture's element 1 "Purpose" is
"Purpose and patterns". For [[a1-project-specification]] the useful parts are the summary-ODD
guidance — the assignment report is exactly the summary-in-the-article case — and the
rationale subsections, since the assignment allocates 6 of 20 marks to justifying modelling
choices.

`See also:` [[odd-protocol]] · [[epstein-2008-why-model]] · [[model-extension]] ·
[[pattern-oriented-modelling]] · [[reproducibility]]
