---
title: Cellular Automaton
type: concept
tags: [complexity, cellular-automata, pattern-formation]
date: 2026-08-23
---

# Cellular Automaton

A cellular automaton (CA) is an array of automata ("cells"), each holding a state from a
finite set, whose state updates each discrete time step according to a local rule applied
to the current states of nearby cells.

## How it works

A CA is defined by four pieces: **entities** are cells, each with a single state variable
taking one of a finite set of values (e.g. off/on, or a continuous-state extension);
**scales** are discrete in both time (generations) and space (typically a 1D or 2D grid,
though higher-dimensional and network arrangements are possible); **processes and
scheduling** are the update rules, classically local, deterministic, and applied
synchronously to every cell at once.

**Elementary 1D CA** make the rule mechanism concrete: a ring of two-state cells, each
updated from a neighbourhood of itself and its two adjacent cells ($K=3$), has
$2^{2^3} = 256$ possible rule tables — each of the 8 possible 3-cell neighbourhood patterns
maps to a 0 or 1 output for the centre cell — and each rule table can be numbered by
reading its 8 outputs as a binary integer. Rings avoid boundary effects. Many of the 256
are trivially equivalent under mirror reflection or 0/1 complement, leaving 88 essentially
distinct rules.

**2D CA** redefine neighbourhood: the **Von Neumann neighbourhood** is the four orthogonal
neighbours, the **Moore neighbourhood** is all eight surrounding cells. [[game-of-life]] is
the canonical 2D example.

[[stephen-wolfram|Wolfram]]'s 1984 classification sorts CA long-run behaviour into four
classes: Class 1 evolves to a fixed homogeneous state; Class 2 to a fixed inhomogeneous
(periodic/limit-cycle) state; Class 3 to [[chaos|chaotic]], aperiodic behaviour sensitive
to initial conditions; Class 4 to complex, unstable, interacting local structures — the
class of most computational interest, since it includes [[turing-completeness|Turing
complete]] rules such as rule 110.

## Formula

The number of possible rule tables for a CA with $S$ states and a neighbourhood of $N$
cells (including the cell itself) is

$$S^{S^{N}}$$

There are $S^N$ distinct neighbourhood configurations, and each maps independently to one
of $S$ outputs. The elementary case $S=2$, $N=3$ gives $2^{2^3}=256$; three states over the
same neighbourhood already gives $3^{27} \approx 7.6 \times 10^{12}$. The count grows
doubly exponentially in the neighbourhood size, which is the formal version of the claim
that very few moving parts generate very large spaces of possible behaviour.

An elementary 1D CA rule can be encoded as an integer by reading its lookup-table outputs
as a binary number. For rule table 01011010 (outputs for neighbourhoods 000 through 111,
in order):

$$(0\times128)+(1\times64)+(0\times32)+(1\times16)+(1\times8)+(0\times4)+(1\times2)+(0\times1) = 90$$

giving "rule 90".

## Why it matters

CA demonstrate that a system with no continuous mathematics at all — just a grid, a finite
state set, and a local lookup table — can produce the full range of [[complex-system]]
behaviour, from frozen order to [[chaos]] to structured, interacting, computation-capable
patterns. Rule 30's output visually resembles the pigment pattern on the *Conus textile*
seashell, and CA-style local rules have been used to model tumour growth, bushfire spread,
and urban growth — evidence that the CA formalism, despite strong simplifying assumptions
(synchronous, deterministic updates), captures something real about how local interaction
generates macroscopic pattern.

## Relationships

- [[game-of-life]] — the canonical 2D CA
- [[wolfram-classes]] — the four-way behaviour classification
- [[turing-completeness]] — some CA rules (rule 110, Life) are computationally universal
- [[complex-system]], [[emergence]] — CA as a minimal demonstration of both
- [[chaos]] — Wolfram's Class 3 is CA-native chaotic behaviour

## Sources

- [[w04b-2d-cellular-automata]] — full treatment: history, formal definition, elementary
  1D CA, rule numbering, Wolfram classes, 2D neighbourhoods, applications.
- [[sayama-2015-modeling-and-analysis-of-complex-systems-ch1]] — names CA as the chapter's
  example model for the pattern-formation topical cluster, credited to von Neumann and
  Ulam, 1940s.
- [[w05a-sensing]] — the rule-count generalisation $S^{S^N}$, from the Week 4 revision
  questions.
