---
title: Compartmental vs Agent-Based Epidemic Models
type: material
tags: [epidemiology, sir-model, abm, model-design, comparison, revision]
date: 2026-08-08
---

# Compartmental vs Agent-Based Epidemic Models

A comparison of the two ways of formalising the same disease model: the original
compartmental formulation, where the population is a set of fractions flowing between
states, and the agent-based reinterpretation, where each individual holds a state and the
population counts are summed out. Written in response to the question "what are the
limitations of an SIR model compared to an ABM?".

Two clarifications frame everything below:

- **The SIR model taught in this subject is already agent-based.** The lecture
  implementation is ten agents each holding $S$, $I$ or $R$ ([[sir-model]]). So the useful
  contrast is not "SIR vs ABM" but *aggregate compartmental formulation* vs *agent-based
  formulation* of the same compartment diagram.
- **Some SIR limitations are not about the formalism at all.** No death state, permanent
  immunity, and a state space too coarse for asymptomatic carriers or severity gradations
  are properties of the SIR *specification*; an agent-based SIR inherits every one of them
  ([[sir-model]]). Fixing them means adding compartments — SEIR, SIRS, a dead state — in
  either formalism ([[model-extension]]).

Everything in the first two sections is derived from wiki pages and cited. The
"Costs of the agent-based version" section is flagged as an addition — it is not in the
lecture material currently ingested.

## What the aggregate formulation gives up

### No individuals, so no heterogeneity

In the original mathematical formulation each compartment holds a *fraction* of the
population and the arrows between compartments are flow rates, giving coupled differential
equations. No individual is represented; the model tracks how much of the population sits
in each state over time ([[compartmental-model]]). Every susceptible is therefore identical
and interchangeable.

The agent-based version reuses the same box-and-arrow diagram for a different purpose: each
agent holds one state at a time and the diagram describes the transition sequence of a
*single individual*, closer to a state machine than to a system of equations
([[compartmental-model]]). Population-level counts become an output of the model rather
than the modelled quantity ([[agent-based-model]]). That is what makes individual attributes
— age, comorbidity, differing susceptibility, all named as complexity factors in
[[w02b-modelling-disease-spread]] — expressible at all.

### Well-mixed contact, which does not survive scale-up

The aggregate model assumes mass action: transmission proportional to the product of the
susceptible and infectious fractions, i.e. everybody can meet everybody. At $N = 10$ this is
defensible — it describes a household or a single room, nine contacts per agent per day
([[contact-rate]]). At population scale it collapses: applied to a five-million-agent
Melbourne with per-contact probability $q = 0.2$, the first infectious agent contacts
everyone and infects roughly a million people on day one. Nothing about the rules is wrong;
the contact structure has become absurd ([[contact-rate]]).

The standard replacement is that a person meets a roughly constant $c$ others per day
regardless of population size. That decouples transmission from $N$ and forces the model to
represent *which* others — neighbourhoods, households, workplaces, a network — rather than
treating the population as well-mixed ([[contact-rate]]). An aggregate flow rate cannot
express "which"; an ABM can, because contact is a property of agents situated in a space
([[model-scales]]).

This also changes what a parameter *means*. $q = 0.2$ at 5 contacts per day and $q = 0.2$ at
100 contacts per day describe different worlds — the second is super-spreader behaviour, not
typical behaviour — so parameter plausibility has to be assessed against the contact
structure, not only against whether the dynamics look right ([[contact-rate]]).

### No space, and therefore nowhere for interventions to act

Basic SIR has no spatial or network structure and no interventions ([[sir-model]]). This
matters more than it first appears, because population density, social behaviour, cultural
practice, mobility restrictions and lockdowns all act *by changing who contacts whom*
([[epidemic-intervention]], [[contact-rate]]). A model with no contact structure has no
surface for most real interventions to attach to. Spatial explicitness is one of the ways an
ABM constrains contact ([[model-scales]]).

### Deterministic trajectory vs sampled outcomes

Both SIR transitions are random draws, so a single run is one sample from a distribution of
outcomes rather than "the model's behaviour" ([[stochasticity]]). The traced lecture run at
$q = 0.2$, $\gamma = 1.0$ gave $|I| = 1, 1, 1, 2, 3, 1, 0$ across $t = 0 \ldots 6$ — a peak
of three, then extinction with one agent never infected ([[sir-model]]). A different seed
gives a different curve. The aggregate ODE version yields one smooth deterministic
trajectory instead, which is exactly what you do not want at small numbers or near
extinction.

[[w03a-analysing-models]] quantifies how much this costs. Repeated stochastic runs at
$N = 10{,}000$, $\beta = 2.5$, $\gamma = 0.4$ ($R_0 = 6.25$) produce a bimodal final-size
distribution: roughly 45% of runs fade out before the outbreak establishes, and the rest
infect around 5,200 agents ([[stochastic-fadeout]], [[bimodal-distribution]]). The
deterministic version produces an outbreak every time, so the entire fadeout mode is
invisible to it — and increasing the population to a million does not remove that mode.

### Extension is structurally richer in the agent-based version

Adding a compartment to the aggregate version means adding an equation and a rate. Adding
one to the agent-based version means adding a state plus the rules governing entry and exit
— and those rules can depend on an individual agent's history, location or attributes in
ways an aggregate rate cannot express ([[compartmental-model]]). The zombie exercise makes
this concrete: "removed" splits into died-of-natural-causes and destroyed-after-reanimating,
because one can still become a zombie and the other cannot
([[zombie-apocalypse-model-design]]).

### Averaging destroys the mechanism

ABMs are the right tool whenever heterogeneity, local interaction and adaptation matter —
that is, whenever averaging over the population would destroy the mechanism you care about
([[agent-based-model]]). The aggregate formulation performs that averaging as its first
move, before any analysis begins. Where the object of study is a [[complex-system]] whose
collective pattern is not encoded in any individual rule, that is fatal by construction
([[emergence]]).

## Costs of the agent-based version

**Flagged as an addition, not derived from ingested lecture content.** The wiki does not
currently state these; they are the standard counterweights and are worth verifying against
a source before being relied on in assessment.

- **Computational cost.** An ODE system solves in milliseconds at any population size; an
  ABM's cost scales with agent count and interaction density. Million-agent models are
  described as a recent capability enabled by cheap computing ([[agent-based-model]]) —
  which is itself evidence that the cost is real.
- **Analytical tractability.** Compartmental models yield closed-form results — a basic
  reproduction number, an epidemic threshold, a final-size relation. An ABM yields sampled
  runs, so equivalent statements have to be established empirically over many replicates.
  [[w03b-reproduction-number]] confirms this from the lecture side: $R_0 = \beta/\gamma$,
  the saturating attack-rate curve, and the coverage threshold $v \ge 1 - 1/R_0$ are all
  derived from the deterministic equations ([[reproduction-number]],
  [[herd-immunity-threshold]]).
- **Parameter burden.** Empirical grounding is already uneven at SIR scale: recovery rate
  can be estimated from observed illness duration (roughly a week for influenza), but $q$ is
  hard to estimate because it depends on contact behaviour ([[sir-model]]). Adding agent
  heterogeneity, spatial structure and behavioural rules multiplies the number of quantities
  needing justification, and this is the standard motivation for validating against patterns
  rather than exact values ([[pattern-oriented-modelling]]).
- **Complexity for its own sake.** The subject's stated heuristic is to start from a basic
  model and add structure one element at a time, not to build the complicated version first
  ([[model-extension]], [[occams-razor]]). Reaching for an ABM before the aggregate model
  has failed inverts that.

## One-line summary

The aggregate compartmental model has a single limitation with four consequences: **it
models the population, not the people.** Heterogeneity, local contact structure, space, and
chance all follow from that — and those four are precisely the levers real interventions
pull.

## Relationships

- [[sir-model]] — the model being compared, and its specification-level weaknesses
- [[compartmental-model]] — the two readings of the same compartment diagram
- [[agent-based-model]] — the bottom-up alternative
- [[contact-rate]] — the assumption that breaks first
- [[stochasticity]], [[epidemic-intervention]], [[model-extension]] — the axes of difference
- [[zombie-apocalypse-model-design]] — worked case of an agent-level compartment split
- [[deterministic-model]], [[difference-equation]] — the aggregate formulation in full
- [[stochastic-fadeout]], [[bimodal-distribution]] — what the deterministic version cannot show

## Sources

- [[w02b-modelling-disease-spread]] — the SIR model, the $N = 10$ implementation, the
  compartments-as-fractions origin, the five-million-agent contact counterexample, the
  parameter-plausibility argument, and the weaknesses raised in discussion.
- [[w01a-introduction]] — the definition of an ABM and the case for it where averaging
  would destroy the mechanism.
- [[w03b-reproduction-number]] — the deterministic compartmental formulation as difference
  and differential equations, and the analytical results derived from it. Ingested
  2026-08-16, closing the gap flagged below.
- [[w03a-analysing-models]] — the distribution of outcomes across stochastic replicates.

## Open questions

- ~~The aggregate/ODE side is reconstructed from a single sentence in
  [[w02b-modelling-disease-spread]]; no source in the wiki develops the mathematical
  formulation directly.~~ **Resolved 2026-08-16.** [[w03b-reproduction-number]] gives the
  difference and differential equation formulation and the results derived from it, so the
  aggregate side of this comparison now cites a source rather than inferring. The sections
  above have been updated where the new source bears on them; the "costs of the agent-based
  version" list is still partly an addition rather than lecture-derived.
- Whether the subject expects the ODE-vs-ABM contrast in assessment at all is unconfirmed —
  Assignment 1 extends the agent-based version.
