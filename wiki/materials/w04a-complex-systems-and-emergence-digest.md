---
title: "Week 4a — Complex Systems & Emergence"
type: material
source: [[sources/w04a-complex-systems-and-emergence]]
date: 2026-08-23
tags: [comp90083, week-04, digest, complex-systems, emergence, flocking, boids]
status: complete
---

# Week 4a — Complex Systems & Emergence

> [!abstract] Orientation — read this first (~1 min)
> **The problem this lecture solves.** Weeks 1–3 treated "build an ABM" as the default
> tool without asking when it is the *right* tool. This lecture answers that: it names
> the property — complexity — that makes a system worth simulating rather than solving
> on paper, and gives you a working definition precise enough to test a system against.
>
> **Core claims**
> 1. Number of parts alone doesn't predict complexity: two bodies orbiting are solvable
>    and regular, three bodies are chaotic, despite an identical rule (gravity) and one
>    extra part.
> 2. A single deterministic equation with no randomness — the logistic map — can produce
>    chaos as a parameter varies; chaos is not disorder, it is deterministic behaviour
>    that *looks* disorganised.
> 3. Many parts obeying simple rules can land anywhere from fully ordered (crystals) to
>    fully disordered-but-homogeneous (gases) to genuinely complex (flocks, CA, networks)
>    — part count and rule simplicity underdetermine the outcome.
> 4. Many parts with complicated, heterogeneous rules can still produce complex but
>    *reproducible and robust* behaviour (development, markets) — complexity is not the
>    same as unpredictability.
> 5. Many parts under classical-engineering design or single central authority produce
>    deterministic or centralised behaviour *by construction* — the absence of central
>    control is what makes a system a candidate for computational modelling.
> 6. Sayama's working definition: complex systems are made of interacting, typically
>    nonlinear components, may arise through self-organisation, sit between fully regular
>    and fully random, and exhibit emergent macroscopic behaviour.
> 7. Decentralisation has three separable components — distribution, bounded knowledge,
>    parallelism — and feedback is either positive (amplifies fluctuations) or negative
>    (dampens them).
> 8. The boids model turns a demonstration into science once you specify agent-level
>    rules *and* population-level outputs comparable against real flock data.
>
> **Prerequisites.** [[flocking]], [[emergence]], [[agent-based-model]].
> **Where it sits.** Opens the subject's second block, "Designing agent-based models"
> (Weeks 4–9), after Weeks 1–3 covered the modelling cycle, ODD, and analysis generically.
> Sets up [[w04b-2d-cellular-automata]], the lecture's second archetypal complex system.
> **Sources.** Deck (41 slides) + recording (~1 hr) · **digest read time ~11 min**

---

## The Spine

### What is a system?
`slides 1–5` · opening

The lecture opens by asking the room for a definition of "system" before showing the
slide's own — a deliberate move, since the point is that the word is used loosely across
disciplines and needs tightening before "complex" can attach to it meaningfully. Oxford's
definition — *a set of things working together as parts of a mechanism or an
interconnecting network* — is illustrated across physiology (organs sharing a function),
biology (an organism as a whole), computing (interacting hardware/software units), and
astronomy (celestial bodies connected by mutual attraction). [!mic] The lecturer's own
gloss, given before the slide was shown, converges on the same idea from a different
angle: *"a set of entities that interact with purpose"* — purpose meaning the interaction
accomplishes something, not that any single part intends it. He runs the same definition
across the university, society, the human body (cells communicating), a computer
(memory ↔ CPU via a protocol), and the Earth itself, to establish that "system" is not a
technical term reserved for computing — almost everything you can point at is one.

### Few parts, simple rules → simple or complex behaviour
`slides 7–9` · early

Two bodies orbiting under gravity — sun and planet — can be solved analytically and
produce a regular, closed trajectory: you can compute where the Earth will be on any
future date. Add a third body (a planet orbiting two stars) and the *same rule*
(gravitational attraction, unchanged) produces trajectories with no closed-form solution
and no repeating structure: the **three-body problem**. [!mic] The lecturer is explicit
about what "chaotic" does and doesn't mean here, since it's the point most likely to be
misread: *"chaos sometimes is misunderstood — some people might think it's completely
random, disorganised, there's nothing there. But mathematically, chaos is actually a
sort of deterministic state that looks random."* You can still say something about where
a chaotic trajectory tends to fall; you just can't write down where it will be.

The same lesson recurs with a single equation and zero randomness: the **logistic map**

$$x_{n+1} = rx_n(1-x_n)$$

Plotting the long-run value of $x$ against the parameter $r$ produces a bifurcation
diagram — a smooth line splitting into two, then four, then a chaotic band, as $r$
increases. [!mic] A student asked why the diagram looks the way it does; the lecturer's
answer locates the limit of the demonstration precisely: *"this is just for a
one-dimensional system"* — the logistic map is the simplest possible case, one variable,
and even that is enough to generate deterministic chaos. This is chaos theory's subject
matter: systems whose behaviour is deterministic but looks disorganised, and the
possibility of such behaviour is named in the lecture as one of the sources of the idea
of *complexity* itself.

### Many parts, simple rules → order, disorder, or complexity
`slides 10–13`

Crystals (highly ordered, regular lattices) and gases in a sealed piston (highly
disordered at the particle level, but statistically homogeneous as a whole) are both
"many parts, simple rules" systems, yet neither is considered complex. [!mic] The
lecturer's reasoning for excluding them: *"despite being formed with many parts, we
understand very clearly what the rules that govern them, and there is nothing kind of
special appearing"* — for the sealed gas specifically, *"there is no interchange between
the outside... so the system behaves more or less uniformly,"* i.e. disorganised at the
particle level but organised as a whole, with no emergent macroscopic property beyond
what statistical mechanics already predicts.

Flocking behaviour — the murmuration of starlings shown as the lecture's running image —
sits differently: many parts, simple local rules, but genuinely complex, unpredictable-
in-detail global behaviour. This is the **archetypal complex system** the lecture keeps
returning to, alongside cellular automata, pattern formation, and complex networks
([[w04b-2d-cellular-automata]] takes up the second of these). [!mic] The lecturer frames
the archetype in terms of what an individual bird is actually doing: *"we have birds that
are just basically acting in response to their neighbours... it's not a very long set of
rules that these individuals are following"* — the behavioural repertoire per agent is
small; the interesting behaviour is entirely a product of the interaction, not of any
individual's sophistication.

### Many parts, complicated rules → complex-but-reproducible, or centralised
`slides 14–16`

Biological development (the slide shows *C. elegans* cleaving from one cell into a
differentiated body plan), termite mound construction, evolution, societies and markets
share heterogeneous rules, specialisation, and hierarchy — and produce behaviour that is
complex, yet **reproducible and robust**: run development again and you get a viable
organism again. This is the case that separates complexity from unpredictability most
clearly — a complex system need not be one whose outcome varies wildly run to run.

Classical engineering systems (aircraft, spacecraft, robotic assembly) and centrally led
human groups (an orchestra, a military marching formation) also have many parts and
complicated rules, but their behaviour is deterministic or centralised **by
construction** — a leader, a plan, or a design specification governs the whole. The
lecture places this case deliberately opposite flocking and markets: the presence of
central design is precisely what removes a system from the "interesting to model
computationally" category, since its behaviour is already known by the act of designing
it.

### What is a complex system? — the working definition
`slide 17`

The lecture distils the four quadrants above into Sayama's definition, quoted with
attribution on the slide itself:

> Complex systems... are made up of several **components**... that **interact** with
> each other... typically, in a **nonlinear** fashion. Complex systems... may arise from
> and evolve through **self-organisation**... are neither completely regular nor
> completely random... exhibit **emergent** behaviour at macroscopic scales.
> — Hiroki Sayama, *Introduction to the Modeling and Analysis of Complex Systems*

This is the same definition developed at greater length in
[[sources/sayama-2015-modeling-and-analysis-of-complex-systems-ch1]] — see that source's
digest for the fuller argument (Weaver's three-way distinction, and the emergence/
self-organisation split) behind the one-slide version used here.

### Properties of complex systems: emergence, self-organisation, decentralisation, feedback
`slides 18–19`

Two properties are given short definitions on their own slide: **emergence** — the
system has properties the individual parts do not, these properties cannot be easily
inferred or predicted, and different properties can emerge from the same parts depending
on context or arrangement — and **self-organisation** — order increases without external
intervention, typically because of interactions between parts.

Two further properties get fuller treatment because they recur through the rest of the
subject. **Decentralisation** has three components: distribution (each part carries only
a subset of global information), bounded knowledge (no part has a full view of the
whole), and parallelism (parts act simultaneously). The lecture's example is market
prices: no central computer sets a price, yet the aggregate signal of buying and selling
moves it, including crashes driven by panic. **Feedback** is positive (amplifies
fluctuations in system state — the mechanism behind exponential growth) or negative
(dampens fluctuations — the mechanism behind settling into a steady-state plateau). This
ties back without naming it to the SIR dynamics from
[[sources/w02b-modelling-disease-spread]]: exponential outbreak growth is positive
feedback, and a system approaching herd immunity is negative feedback.

### The boids model of flocking behaviour
`slides 20–23`

[[craig-reynolds|Craig Reynolds]], a computer graphics and animation researcher (Electronic
Arts, DreamWorks Animation, Sony), built an early (1986) ABM of flocking he called
**boids**. Each boid has a bounded angular and distance-limited field of view — it senses
only other boids within some *angle* and *distance* of itself — and moves by three local
rules:

1. **Separation** — steer to avoid crowding nearby boids (collision avoidance).
2. **Cohesion** — steer toward the average position of nearby boids (safety in numbers).
3. **Alignment** — steer toward the average heading of nearby boids.

No rule mentions the flock; flock-level coherence is the model's entire emergent output.

### From simulator to science
`slide 24`

The lecture closes by reframing boids as a route from demonstration to testable science.
Once you pose a scientific question — *what assumptions about individual movement can
explain the emergent characteristics of real flocks?* — the model needs outputs
comparable against real bird or fish data, not just a pretty animation. The slide lists
four candidates: the number of agents that have flock-mates (other agents within a given
radius), the mean number of flock-mates per agent, the mean distance between an agent and
its nearest other agent, and the standard deviation of heading across the whole
population. This mirrors the move made for the SIR model in
[[sources/w03a-analysing-models]] — choosing summary statistics that map onto a real
question rather than reporting everything a simulation can emit.

---

## Recall Layer

> [!question]- Why does adding one body to a two-body orbital system destroy the
> analytical solution?
> The two-body problem (sun + planet) can be solved in closed form and produces a
> regular, predictable trajectory. Adding a third body keeps the rule (gravity)
> identical but makes the system's equations non-integrable — there is no closed-form
> solution, and the trajectories become chaotic: deterministic, but with no repeating
> structure and extreme sensitivity to initial conditions. `slides 7–8`

> [!question]- Is chaos the same as randomness? What's the actual definition used in the
> lecture?
> No. Chaos is deterministic behaviour that *looks* disorganised — the logistic map
> $x_{n+1}=rx_n(1-x_n)$ produces it with zero stochastic element. A chaotic system's
> future state is fully determined by its current state and the rule; the appearance of
> randomness comes from extreme sensitivity to initial conditions, not from any actual
> random process. `slides 9`

> [!question]- Why aren't a crystal and a gas in a sealed piston considered complex
> systems, despite having "many parts"?
> Both have many parts and simple rules, but neither produces genuinely emergent,
> unpredictable macroscopic behaviour: the crystal is fully ordered by its simple local
> rule (nothing "special" appears), and the sealed gas is disordered at the particle
> level but statistically homogeneous as a whole (isolated, so no external energy flow
> drives anything beyond equilibrium). Complexity requires sitting *between* full order
> and full randomness while still producing something not predictable from the rule
> alone. `slides 10–11`

> [!question]- What's the difference between "many parts, complicated rules → complex
> but reproducible" (development, markets) and "many parts, complicated rules →
> centralised" (orchestra, military)?
> The first has no central controller — behaviour emerges from local, heterogeneous
> interaction (specialisation, hierarchy) and is complex but robust and reproducible run
> to run. The second has behaviour governed by a central cause, leader, or design plan —
> the outcome is deterministic or centralised *by construction*, which is exactly why it
> isn't interesting to model computationally: you already know the answer by reading the
> design. `slides 14–16`

> [!question]- State Sayama's working definition of a complex system in full.
> Complex systems are made up of several components that interact with each other,
> typically in a nonlinear fashion; they may arise from and evolve through
> self-organisation; they are neither completely regular nor completely random; and they
> exhibit emergent behaviour at macroscopic scales. `slide 17`

> [!question]- Decentralisation is defined as having three components. Name them and give
> the market-price example for each.
> **Distribution** — each part carries only a subset of global information (no trader
> knows the whole market). **Bounded knowledge** — no part sees the whole (no trader sees
> every other trader's intent). **Parallelism** — parts act simultaneously (trades happen
> concurrently, not in a queue). No central computer sets the price; the aggregate of
> these decentralised actions produces price movements, including panic-driven crashes.
> `slide 19`

> [!question]- Positive and negative feedback: define each and name the mechanism each
> underlies.
> Positive feedback amplifies fluctuations in system state — the mechanism behind
> exponential growth (e.g. early-stage outbreak spread in the SIR model). Negative
> feedback dampens fluctuations — the mechanism behind a system settling into a
> steady-state plateau (e.g. an outbreak approaching herd immunity). `slide 19`

> [!question]- What are the three local rules in the boids model, and what does each one
> steer the agent toward or away from?
> Separation — steer to avoid crowding nearby boids (collision avoidance). Cohesion —
> steer toward the average position of nearby boids (safety in numbers). Alignment —
> steer toward the average heading of nearby boids. Sensing is bounded by an angle and a
> distance; no rule references the flock as a whole. `slides 21–22`

> [!question]- Boids "looks complex" on its own. What has to be added to turn it into
> science rather than a demonstration?
> A stated scientific question ("what assumptions about individual movement explain the
> emergent characteristics of real flocks?") plus model outputs that are directly
> comparable to real flock/school data: number of agents with flock-mates, mean
> flock-mates per agent, mean nearest-neighbour distance, and the standard deviation of
> heading across the population. Without these, the model demonstrates emergence but
> can't test any hypothesis about it. `slide 24`

> [!failure] Common failure modes
> - Treating "many parts" or "complicated rules" as sufficient for complexity on their
>   own — both crystals (many parts, simple rules, no emergence) and orchestras (many
>   parts, complicated rules, centralised) are explicit counterexamples in the lecture.
> - Confusing chaos with randomness — chaos is deterministic; a chaotic system run twice
>   from the *exact* same initial condition produces the exact same trajectory.
> - Assuming emergent behaviour implies unpredictability at the population level —
>   development and market dynamics are complex but reproducible, which is the whole
>   point of the "many parts, complicated rules, complex but reproducible" quadrant.

> [!exam] Exam surface
> Likely framed as: given a description of a system (number of parts, rule complexity,
> presence/absence of central control), classify it into one of the lecture's four
> quadrants and justify why, using the vocabulary of decentralisation and feedback where
> relevant. Also plausible: state and apply Sayama's definition to a novel example, or
> explain why a specific system (a sealed gas, a corporation, a starling flock) is or
> isn't a complex system.

> [!todo] Open threads
> The lecture doesn't formalise *how much* nonlinearity or interaction density is needed
> to cross from "complicated" into "complex" — the quadrant classification is heuristic,
> not a measurable threshold. [[w04b-2d-cellular-automata]] gives a more mechanistic,
> rule-countable example (elementary CA) that partially fills this gap.

---

## Topics covered

- [ ] `slides 1–3` — subject structure, week objectives → [[#What is a system?]]
- [ ] `slides 4–6` — definitions of "system" across disciplines → [[#What is a system?]]
- [ ] `slides 7–9` — two-body vs three-body problem, logistic map, deterministic chaos →
  [[#Few parts, simple rules → simple or complex behaviour]]
- [ ] `slides 10–11` — crystals and gases as many-parts/simple-rules limits →
  [[#Many parts, simple rules → order, disorder, or complexity]]
- [ ] `slide 12` — flocking, CA, pattern formation, complex networks as archetypes →
  [[#Many parts, simple rules → order, disorder, or complexity]]
- [ ] `slides 13–14` — biological development, termite mounds, evolution, markets →
  [[#Many parts, complicated rules → complex-but-reproducible, or centralised]]
- [ ] `slides 15–16` — classical engineering and centrally-led groups →
  [[#Many parts, complicated rules → complex-but-reproducible, or centralised]]
- [ ] `slide 17` — Sayama's working definition → [[#What is a complex system? — the working definition]]
- [ ] `slides 18–19` — emergence, self-organisation, decentralisation, feedback →
  [[#Properties of complex systems: emergence, self-organisation, decentralisation, feedback]]
- [ ] `slide 20` — Summary: complex systems in the real world, aims (understand, predict,
  control, design)
- [ ] `slides 21–24` — flocking recap, Reynolds, boids sensing and rules, from simulator
  to science → [[#The boids model of flocking behaviour]], [[#From simulator to science]]

## Connections

`See also:` [[complex-system]], [[emergence]], [[self-organisation]], [[decentralisation]],
[[feedback]], [[chaos]], [[flocking]], [[boids]],
[[sources/sayama-2015-modeling-and-analysis-of-complex-systems-ch1]] (Sayama's definition
in full), [[w04b-2d-cellular-automata]] (the lecture's other archetypal complex system).
