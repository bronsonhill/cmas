---
title: "Sayama (2015) Ch. 1 — Introduction"
type: material
source: [[sources/sayama-2015-modeling-and-analysis-of-complex-systems-ch1]]
date: 2026-08-23
tags: [comp90083, week-04, digest, complex-systems, emergence, self-organisation]
status: complete
---

# Sayama (2015) Ch. 1 — Introduction

> [!abstract] Orientation — read this first (~1 min)
> **The problem this chapter solves.** [[w04a-complex-systems-and-emergence]] quotes
> Sayama's definition of a complex system on a single slide, in attribution, without the
> argument behind it. This chapter is that argument: it explains *why* the definition has
> the shape it does — what the two traditional views of a system fail to cover, and why
> emergence and self-organisation, though constantly conflated, are actually two
> different claims.
>
> **Core claims**
> 1. Complex systems science exists to fill the gap between two traditions that already
>    have well-developed tools: systems with few, tightly-coupled components (solved
>    analytically) and systems with many, fully independent components (solved
>    statistically). Neither tool works on *interdependent* components.
> 2. Emergence is a claim about *scale*: a macroscopic property is emergent when it
>    can't be simply reduced to the microscopic rules producing it.
> 3. Self-organisation is a claim about *scale and time together*: a system
>    self-organises when it spontaneously develops macroscopic structure as time
>    progresses, with no external designer imposing that structure.
> 4. Self-organisation looks like it violates the second law of thermodynamics but
>    doesn't, because self-organising systems are open — they exchange energy with their
>    environment rather than being sealed off from it.
> 5. Complex systems science has three historical roots (nonlinear dynamics, systems
>    theory, game theory) and four more recent research fronts (pattern formation,
>    evolution and adaptation, networks, collective behaviour) — a field map, not a
>    single theory.
>
> **Prerequisites.** None beyond general scientific literacy — this is the textbook's
> opening chapter.
> **Where it sits.** Directly cited on [[w04a-complex-systems-and-emergence]]'s "What is a
> complex system?" slide, which quotes this chapter's definition verbatim in attribution.
> Chapter 1 is orientation only; the textbook's real modelling content (dynamical systems,
> discrete- and continuous-time models, bifurcations, chaos) starts in Chapter 2 onward,
> outside this week's assigned reading.
> **Sources.** Chapter 1, "Introduction" (printed pp. 3–9, §1.1–1.2) ·
> **digest read time ~7 min**

---

## The Spine

### The definition, given outright
`§1.1, p. 3`

Sayama opens the book with the definition rather than building up to it — an unusual
choice he flags himself, on the grounds that starting from an outright claim is more
honest than pretending the book will "discover" it inductively:

> Complex systems are networks made of a number of components that interact with each
> other, typically in a nonlinear fashion. Complex systems may arise and evolve through
> self-organization, such that they are neither completely regular nor completely
> random, permitting the development of emergent behavior at macroscopic scales.

A footnote traces the definition's ancestry to Herbert Simon's 1962 formulation: "[A]
complex system [is] a system made up of a large number of parts that interact in a
nonsimple way." Sayama's version is, by his own account, "just a bit wordier." The
definition is immediately grounded in real examples: gene regulatory networks within a
cell, physiological systems of an organism, brains and other neural systems, food webs,
the global climate, stock markets, the Internet, social media, and national and
international economies and cultures all carry these properties.

### Defining complex systems by what they are not
`§1.1, pp. 3–4`

The chapter's organising move, following American mathematician and systems scientist
Warren Weaver, is a three-way split of possible systems:

- **Problems of simplicity** — components are tightly coupled to each other with only a
  few, or no, degrees of freedom left within the system, so the whole collection can be
  described as a single entity with a small number of variables. Example: rigid-body
  mechanics. Well-developed classical theory handles this case completely.
- **Problems of disorganized complexity** — components are fully independent of each
  other. Examples: an ideal gas (thermodynamics), fixed coin tosses (probability theory).
  Conventional statistics handles this case perfectly, since independence is exactly
  what statistical tools are built to exploit.
- **Problems of organized complexity** — the large gap between the two above, where
  components are neither tightly coupled into one unit nor statistically independent,
  but genuinely **interdependent**. Weaver named this gap; complex systems science is
  Sayama's name for the field built to fill it.

The pedagogical function of this framing is that it tells you what tool *not* to reach
for. If a system is tightly coupled with few degrees of freedom, classical mechanics-style
analytical tools apply directly. If components are independent, statistics applies
directly. Neither applies to a system of genuinely interdependent parts — which is
precisely the situation an [[agent-based-model|ABM]] or a cellular automaton is designed
to handle by simulation rather than by closed-form solution, connecting this framing
directly to why the subject spends nine weeks (4–9, per the "Designing agent-based
models" block) on model *design* rather than analytical shortcuts.

### Emergence: a claim about scale
`§1.1, p. 4`

Emergence was first discussed in philosophy over a century before this book, and the
chapter opens with two illustrative examples chosen for their intuitive force rather than
their technical precision: you can easily tell a dog wagging its tail is *alive*, but it
is extremely difficult to explain what microscopic physical or chemical processes make
that organism "alive"; you know you are conscious, but describing which
neurophysiological processes constitute "consciousness" is hard. Both "livingness" and
"consciousness" are **emergent properties** — macroscopic properties that resist simple
reduction to the microscopic rules that produce them.

Despite a long history of debate and multiple competing definitions, the chapter adopts
one specific formulation, credited to complex systems scientist Yaneer Bar-Yam, on the
grounds that it is simple and consistent with most of what's proposed in the literature:

> Emergence is a nontrivial relationship between the properties of a system at
> microscopic and macroscopic scales. Macroscopic properties are called emergent when it
> is hard to explain them simply from microscopic properties.

The operative test given in the surrounding prose: if you observe a macroscopic property
that is fundamentally different from what you would naturally expect from the microscopic
rules, you are witnessing emergence. The claim is entirely about *scale* — comparing a
system's description at one level of granularity against its description at another.

### Self-organisation: a claim about scale and time together
`§1.1, pp. 4–5`

Self-organisation is introduced as a distinct idea that gets confused with emergence
constantly — the chapter states some researchers use the two terms "almost
interchangeably," and treats disentangling them as worth doing carefully:

> Self-organization is a dynamical process by which a system spontaneously forms
> nontrivial macroscopic structures and/or behaviors over time.

The key addition relative to emergence is *time*: you call something self-organising when
you observe the system organising itself to produce a nontrivial macroscopic structure
or behaviour *as time progresses* — a process, not a static comparison across scales.

The chapter addresses the objection this immediately invites: doesn't spontaneous
increase in order violate the second law of thermodynamics (entropy of a closed system
increases monotonically over time)? The resolution is that self-organising systems are
not, in fact, going against the law — they are **open systems**, driven by energy flow
coming from and going to their environment, not closed ones. The second law applies to
closed systems; a system exchanging energy with its surroundings can locally decrease its
own entropy while the combined system-plus-environment entropy still increases. Sayama
frames self-organisation as *giving emergent properties a dynamical explanation*: where
emergence names the fact that a nontrivial macro/micro relationship exists,
self-organisation describes the process by which that relationship actually comes to be,
over time.

### The seven topical clusters
`§1.2, pp. 6–9`

The chapter closes by mapping the field into seven clusters, organised around the two
core ideas (emergence over scale, self-organisation over time), split into three
historical roots and four more recent research fronts:

**Historical roots:**

- **Nonlinear dynamics** — the oldest cluster, tracing back to Newton and Leibniz's 17th-
  century invention of calculus, but only recognised in the 20th century as capable of
  producing *chaos*. Here **nonlinearity** means the outputs of a system are not given by
  a linear combination of its inputs; in the context of system behaviour, "inputs" and
  "outputs" can mean current and next states, and if that relationship isn't linear, the
  system is a *nonlinear system*. The possibility of chaotic behaviour in such systems
  implies no analytical solution will generally be available — named explicitly as one of
  the several origins of the idea of complexity itself.
- **Systems theory** — developed rapidly during and after WWII, driven by wartime demand
  for mathematical theories of computation, control, and communication. Landmark
  contributions: Alan Turing's foundational theoretical computer science, Norbert
  Wiener's cybernetics, Claude Shannon's information and communication theory. A common
  thread: all originated from engineers facing real complex problems and building tools
  to meet societal demand.
- **Game theory** — a mathematical theory of strategic decision-making, established by
  von Neumann and Oskar Morgenstern, developed during the Cold War in response to the
  need to model balance between two dominant powers. Its models typically assumed
  rationality among players, letting decision-making be formalised as a deterministic
  dynamical system — linking game theory back to nonlinear dynamics — and its influence
  now spans economics, political science, psychology, ecology, and evolutionary biology.

**Recent research fronts:**

- **Pattern formation** — a self-organising process involving both space and time: many
  components distributed over a spatial domain interact (typically locally) to create an
  interesting spatial pattern as time progresses. **Cellular automata**, developed by von
  Neumann and Ulam in the 1940s, are given as the chapter's own worked example, alongside
  **partial differential equation** models, which describe spatial as well as temporal
  change.
- **Evolution and adaptation** — spans biological evolutionary theory (traceable to
  Darwin) and its computational analogues developed in the "complex adaptive systems"
  tradition: evolutionary computation, artificial neural networks, and other frameworks
  now grouped under machine learning or soft computing, which began rapid development in
  the 1980s alongside complex systems science itself and remain conceptually and
  historically coupled to it.
- **Networks** — long studied as *graph theory* in mathematics since Leonhard Euler in
  the 18th century, reinvigorated recently by the availability of large-scale relational
  data (social media, mobile phones, the internet).
- **Collective behaviour** — social dynamics and swarm-style coordination, similarly
  reinvigorated by data availability, enabling researchers to analyse network structure at
  multiple scales and to build dynamical models of how collectives actually behave.

The chapter is explicit that this seven-cluster map is the author's own view, "by no
means well defined or well accepted by the community" — the textbook's own chapters are
organised by methodology (modelling and analysis technique), not by these topical
clusters, precisely so the reader learns transferable "how-to" skills rather than a
taxonomy tied to any one research community's boundaries.

---

## Recall Layer

> [!question]- State Sayama's working definition of a complex system, in full.
> Complex systems are networks made of a number of components that interact with each
> other, typically in a nonlinear fashion. They may arise and evolve through
> self-organisation, such that they are neither completely regular nor completely
> random, permitting the development of emergent behaviour at macroscopic scales. `p. 3`

> [!question]- Weaver's three-way split: what makes rigid-body mechanics a "problem of
> simplicity" and an ideal gas a "problem of disorganized complexity", and what gap is
> left over?
> Rigid-body mechanics: components are tightly coupled with only a few (or no) degrees of
> freedom, so the whole can be described as a single entity with a small number of
> variables — classical mechanics handles this directly. An ideal gas: components are
> fully independent, so conventional statistics handles it directly. The gap is
> "problems of organized complexity" — systems whose components are genuinely
> *interdependent*, neither one tightly-coupled unit nor a set of independent parts —
> which is what complex systems science exists to address. `pp. 3–4`

> [!question]- Give the Bar-Yam definition of emergence used in the chapter, and state
> the operative test for recognising it.
> Emergence is a nontrivial relationship between a system's properties at microscopic and
> macroscopic scales; a macroscopic property is emergent when it's hard to explain simply
> from microscopic properties. Test: if you observe a macroscopic property fundamentally
> different from what you'd naturally expect from the microscopic rules, you're witnessing
> emergence. `p. 4`

> [!question]- What's the one-word difference between the definitions of emergence and
> self-organisation, and why does it matter?
> **Time.** Emergence is about scale alone — a static comparison between micro and macro
> descriptions of a system. Self-organisation is about scale *and* time — it names the
> dynamical process by which macroscopic structure or behaviour spontaneously develops as
> time progresses. It matters because self-organisation gives emergent properties a
> *dynamical explanation*: emergence names that the relationship exists, self-organisation
> describes how it comes to exist. `pp. 4–5`

> [!question]- Self-organisation looks like it violates the second law of thermodynamics.
> Why doesn't it?
> The second law applies to *closed* systems, where entropy increases monotonically.
> Self-organising systems are *open* — they exchange energy with their environment. A
> system can locally decrease its own entropy (increase its order) while drawing on
> energy flow from outside, without violating the second law for the system-plus-
> environment as a whole. `p. 4–5`

> [!question]- Name the three historical roots of complex systems science and one
> landmark contribution associated with each.
> Nonlinear dynamics — recognition (20th century) that nonlinear systems can be chaotic
> and hence analytically unsolvable. Systems theory — Turing's theoretical computer
> science, Wiener's cybernetics, Shannon's information theory (all WWII-era, engineering-
> driven). Game theory — von Neumann and Morgenstern's Cold War-era formalisation of
> strategic decision-making. `pp. 6–7`

> [!question]- Name the four more recent research-front clusters and give the chapter's
> own worked example for pattern formation specifically.
> Pattern formation, evolution and adaptation, networks, collective behaviour. Pattern
> formation's worked example: cellular automata (von Neumann and Ulam, 1940s), alongside
> partial differential equation models. `p. 8`

> [!question]- Why does the textbook organise its own chapters by modelling/analysis
> methodology rather than by these seven topical clusters?
> Because the clusters are the author's own view of the field, not a well-defined or
> universally accepted taxonomy, and because methodologies of modelling and analysis
> traverse many of the clusters rather than belonging to just one. Organising by method
> teaches transferable "how-to" skills the reader can apply to any subject of their own
> interest, rather than tying the material to one research community's boundaries. `p. 9`

> [!failure] Common failure modes
> - Treating emergence and self-organisation as synonyms — the chapter is explicit that
>   researchers frequently do this and that it is a conflation worth resisting; emergence
>   is about scale, self-organisation is about scale *and* time.
> - Concluding self-organisation violates thermodynamics — the resolution (open vs.
>   closed systems) is a one-line fix but is easy to miss if you only remember "order
>   increases without external intervention" without the open-system qualifier.
> - Assuming "many components" alone puts a system into the "organized complexity" gap —
>   an ideal gas has enormous numbers of components and is squarely a problem of
>   *disorganized* complexity, because those components are statistically independent.

> [!exam] Exam surface
> Likely framed as: given a description of a system, classify it using Weaver's
> three-way split and justify the classification; distinguish emergence from
> self-organisation using both definitions precisely, possibly via a worked example (a
> flock, a market, a crystal); or explain why self-organisation doesn't violate the
> second law of thermodynamics. Also plausible: name and briefly describe the seven
> topical clusters, or identify which cluster a described research area belongs to.

> [!todo] Open threads
> The chapter is deliberately introductory and doesn't attempt to formalise "nontrivial"
> in either the emergence or self-organisation definitions — both rely on an intuitive
> sense of "hard to explain simply" or "not naturally expected," which the rest of the
> textbook (outside this week's assigned Chapter 1) presumably tightens with concrete
> mathematical tools (dynamical systems, bifurcation, chaos) not covered in this reading.

---

## Topics covered

- [ ] `p. 3` — outright definition of complex systems, real-world examples →
  [[#The definition, given outright]]
- [ ] `pp. 3–4` — Weaver's three-way distinction (simplicity / disorganized complexity /
  organized complexity) → [[#Defining complex systems by what they are not]]
- [ ] `p. 4` — emergence: Bar-Yam's definition and the dog/consciousness examples →
  [[#Emergence: a claim about scale]]
- [ ] `pp. 4–5` — self-organisation: definition, the second-law objection and its
  resolution, relationship to emergence →
  [[#Self-organisation: a claim about scale and time together]]
- [ ] `pp. 6–7` — historical roots: nonlinear dynamics, systems theory, game theory →
  [[#The seven topical clusters]]
- [ ] `pp. 8–9` — recent fronts: pattern formation, evolution and adaptation, networks,
  collective behaviour; caveat on the map's authorial nature →
  [[#The seven topical clusters]]

## Connections

`See also:` [[complex-system]], [[emergence]], [[self-organisation]], [[chaos]],
[[cellular-automaton]], [[w04a-complex-systems-and-emergence]] (quotes this chapter's
definition directly), [[w04b-2d-cellular-automata]] (works the pattern-formation cluster's
example in full technical detail).
