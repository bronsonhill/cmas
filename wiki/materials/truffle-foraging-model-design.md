---
title: Truffle Foraging — A Worked Model Design
type: material
tags: [worked-example, model-design, modelling-cycle]
date: 2026-08-01
---

# Truffle Foraging — A Worked Model Design

A reconstruction of the in-class design exercise from [[w01b-modelling-cycle]], worked
through as a first pass at steps 1–3 of the [[modelling-cycle]]. No code was written; the
point is the reasoning that precedes it.

## 1. The starting question

> What is an efficient strategy for searching for mushrooms in a forest?

This is too broad to constrain a design. It leaves open what kind of mushroom, what
"efficient" means, and what the searcher can perceive — and so it licenses no decisions.

**Narrowing it to truffles changes everything:**

| Property of truffles | Consequence for the model |
|---|---|
| Grow **underground** | Cannot be found by sight; a non-visual sensing mechanism is required |
| Do **not cluster** | Greedy / cluster-based search loses its justification |
| Grow with **host trees** | Tree location becomes a usable cue |
| Very **valuable** | Justifies the cost of modelling at all |

That last row answers a question worth asking explicitly and early — *do we need a model?*
For a cheap and abundant target, probably not.

## 2. Candidate strategies and what each assumes

| Strategy | Requires | Verdict for truffles |
|---|---|---|
| Random walk, large step | Nothing — zero-information baseline | Reasonable starting point |
| Greedy / cluster-based | Targets clustered in space | Fails — truffles don't cluster |
| Spiral | A sensible centre; spacing ≤ sensing radius | Workable; needs a start point |
| Zigzag / transect | A bounded area to sweep | Workable general-purpose sweep |
| Cue-directed (host trees, logs, litter) | Known correlation with target | Strong — exploits real biology |
| Multi-agent | More searchers, coordination | Faster coverage, higher cost, sharing problem |

See [[search-strategy]] for the general treatment. The headline conclusion: **no strategy
is best in the abstract** — viability follows from the target's spatial distribution and
the sensing mechanism.

## 3. The sensing mechanism

Truffle hunters use pigs or dogs, which locate truffles by smell. Making this explicit
forces the model-relevant question:

> How far away can the pig detect a truffle?

That radius is a **parameter**, and it is coupled to the search geometry — there is no
point spacing a spiral or transect more widely than the sensing radius, and no benefit to
packing it much tighter. See [[agent-sensing]].

## 4. First pass at model structure

Following [[model-structure]]:

- **Scales** — a grid on the order of a few kilometres: roughly how far a forager can cover
  on foot. Not an Australia-sized world.
- **Entities** — the forager and the pig (possibly one composite agent), truffles, host
  trees, the forest environment.
- **State variables** — the searcher's current mode (uninformed sweep vs. local search near
  a cue), position, heading, truffles found.
- **Processes** — sensing (smell), movement (per the chosen strategy), collection.
- **Parameters** — sensing radius, step size, number of searchers, truffle density.

## 5. What to include, and what to leave out

Raised in class as candidates, with the deciding question always *would the answer change
without it?*

- **Topography** — plausibly relevant to where truffles grow and how fast a forager moves.
- **Climate / moisture** — relevant to truffle growth; may only need a coarse
  representation, not a detailed one.
- **Leaf litter** — a possible visual cue; probably a low-priority detail for a first model.
- **Host trees** — high priority, since they drive the most promising strategy.
- **A model of how truffles spread** — valuable if the question extends to sustainability.
- **Historical search data** — useful for [[pattern-oriented-modelling]] and calibration
  later, not for a first model.
- **Weather stopping a forager going out** — a different question; leave out.

The guiding heuristic throughout is **start simple** and add detail in priority order — see
[[abstraction]] and [[occams-razor]].

## Open questions

- What does "efficient" mean here — truffles per hour, per kilometre walked, or per dollar?
  The objective function was never pinned down in class, and it determines what counts as a
  better strategy. This connects to [[optimisation]] and [[satisficing]].
- If multiple searchers are modelled, do they share discoveries? Raised in class but left
  unresolved, and it changes the multi-agent result substantially.

## Related

- [[w01b-modelling-cycle]] — the source lecture
- [[modelling-cycle]], [[research-question]], [[model-structure]]
- [[search-strategy]], [[agent-sensing]]
