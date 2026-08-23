---
title: "Week 4b — 2D Cellular Automata"
type: material
source: [[sources/w04b-2d-cellular-automata]]
date: 2026-08-23
tags: [comp90083, week-04, digest, cellular-automata, game-of-life, lotka-volterra]
status: complete
---

# Week 4b — 2D Cellular Automata

> [!abstract] Orientation — read this first (~1 min)
> **The problem this lecture solves.** Week 4a argued from examples that complexity
> doesn't require many parts or complicated rules. This lecture proves it with a single
> minimal formalism: a grid of cells, each holding one bit, updated by a lookup table —
> and shows that formalism can freeze, oscillate, go chaotic, or perform universal
> computation, depending entirely on which of a very small rule space you pick.
>
> **Core claims**
> 1. A cellular automaton is nothing more than an array of automata whose "external
>    input" is the current state of nearby cells — locality is the entire mechanism.
> 2. With 2 states and a neighbourhood of 3 cells, there are exactly $2^{2^3}=256$
>    possible elementary 1D rules, only 88 of which are behaviourally distinct once
>    mirror and complement symmetry are factored out.
> 3. Wolfram's four behaviour classes (fixed / periodic / chaotic / complex-localised)
>    partition this tiny rule space, and which class a rule falls into is not obvious
>    from the rule number alone.
> 4. Rule 110 (1D) and Conway's Game of Life (2D) are both Turing complete — a handful
>    of local rules, with no notion of "computer" built in, can perform universal
>    computation.
> 5. CA are strictly weaker models of real systems than they look, because synchronous,
>    deterministic updates are strong assumptions almost no real system actually
>    satisfies.
> 6. The Lotka-Volterra ODE system is the classical explanation for the Hudson Bay
>    hare/lynx cycle, and it has a discrete, probabilistic reformulation that plugs
>    directly into the CA/ABM framework — the bridge from continuous population models to
>    agent-based ones.
>
> **Prerequisites.** [[complex-system]], [[emergence]], [[self-organisation]] (all from
> [[w04a-complex-systems-and-emergence]]).
> **Where it sits.** Follows directly from Week 4a's survey; CA is that lecture's second
> archetypal complex system, worked out formally rather than just gestured at. The
> Lotka-Volterra close sets up predator-prey modelling as an assignment/lab direction.
> **Sources.** Deck (15 slides) + recording (~35 min) · **digest read time ~10 min**

---

## The Spine

### Origins and the automaton → cellular automaton generalisation
`slides 3–5`

[[john-von-neumann]] and [[stanislaw-ulam]] developed cellular automata at Los Alamos in
the 1940s — the same lab, the same decade as the atomic bomb project, which the lecturer
notes in passing as historical colour rather than a technical point. Von Neumann's
motivation was self-replicating machines; Ulam's was crystal growth. Formally, an
**automaton** is a theoretical machine that updates its internal state from external
inputs and its own previous state. A **cellular automaton** generalises this to an array
of automata (cells), where the "external inputs" to any one cell are simply the current
states of its nearby cells — nothing more exotic than that.

Four structural choices define a CA:

- **Entities, state, and scales** — entities are cells; each holds a single state
  variable from a finite set (the running example uses binary, OFF/ON or 0/1).
- **Time** — discrete, abstract generations, never continuous.
- **Space** — discrete, typically a 1D or 2D grid, though higher dimensions or networks
  are possible.
- **Processes and scheduling** — update rules are local (a cell only sees its immediate
  neighbours) and, in the classical formulation, deterministic and synchronous (every
  cell updates at once, each generation).

[!mic] Asked implicitly by the deck's own framing, the lecturer states the purpose
directly before working any example: *"the purpose of this is just to demonstrate...
emergence of complex behaviour... because of very simple rules... a very specific
domain"* — CA is deliberately the minimal case, stripped of everything an ABM would add
(heterogeneous agents, memory, continuous state) so that whatever complexity appears is
attributable entirely to locality plus the rule.

### Elementary 1D cellular automata
`slides 6–11`

The worked construction: a 1D grid of binary cells arranged in a ring (a **torus**, so
the last cell neighbours the first — this sidesteps having to define special-case
behaviour at the edges). Each cell's next state depends on a **neighbourhood** of $K=3$
cells: itself and its two adjacent neighbours. Time advances in discrete **generations**;
every cell in a generation is updated simultaneously from the previous generation's
neighbourhood states, never from states already updated in the current step.

Because a $K=3$ binary neighbourhood has $2^3=8$ possible configurations (000 through
111), and each configuration maps to one of 2 possible next-states for the centre cell,
a rule is fully specified by an 8-bit lookup table — one output bit per input
configuration. Reading those 8 output bits as a binary number gives the rule a name.
Worked example, **rule 90**: the lookup table

$$
\begin{array}{c|cccccccc}
\text{neighbourhood} & 111 & 110 & 101 & 100 & 011 & 010 & 001 & 000 \\\hline
\text{output} & 0 & 1 & 0 & 1 & 1 & 0 & 1 & 0
\end{array}
$$

read as the binary string $01011010$ converts to decimal as
$(0{\times}128)+(1{\times}64)+(0{\times}32)+(1{\times}16)+(1{\times}8)+(0{\times}4)+(1{\times}2)+(0{\times}1)=90$.

With 2 states and $K=3$ neighbours, the total number of possible elementary rules is
$2^{2^3} = 2^8 = 256$. Many of these are trivially equivalent under two symmetries:
**mirror** (reflection of the whole pattern through a vertical axis — left/right
relabelling) and **complement** (swapping the roles of 0 and 1 throughout the
definition). Factoring these out leaves **88 essentially distinct** elementary rules —
[!mic] the lecturer arrived at this by elimination live, working through examples:
*"if I have the 1111 all 1s it's sort of equivalent to the 0000... there might be some
of them that are just reflections of each other... if we start to get rid of this kind of
compliments [sic] reflections... we will end up with about 88."*

Two rules are demonstrated directly in NetLogo. **Rule 90** produces a highly regular,
self-similar geometric pattern (visually a Sierpinski-triangle-like structure) that,
once started, repeats indefinitely without collapsing — [!mic] *"the pattern is
self-reproducing... even though I can keep running and running, the pattern is kind of
infinitely happening."* **Rule 30**, by contrast, produces an irregular, seemingly
patternless triangular field that spreads from the initial seed; a student in the room
observed the edges stayed regular even as the interior looked chaotic, which the
lecturer confirmed was a genuine feature that only disappears once the pattern reaches
the grid boundary. Rule 30's pattern strikingly resembles the pigment pattern on the
shell of the cone snail *Conus textile* — [!mic] the lecturer's own framing: *"some
people hypothesise that perhaps a similar sort of concept is happening [in the shell]...
something related about how the tiles are connected between each other that produces
this sort of similar pattern."* This is offered as a hypothesis about the biological
mechanism, not a proven claim.

### Wolfram's four classes and universal computation
`slide 12`

[[stephen-wolfram|Wolfram]] (creator of Mathematica and Wolfram Alpha) proposed in 1984 that CA
behaviour sorts into four classes, illustrated on rules 160, 108, 126, and 110
respectively:

1. **Class 1** — evolves to a **fixed homogeneous state**: the system freezes into a
   fixed state after a short time.
2. **Class 2** — evolves to a **fixed inhomogeneous state**: periodic or limit-cycle
   behaviour, repeating patterns that don't die out but also don't change qualitatively.
3. **Class 3** — evolves to **chaotic or aperiodic** behaviour: continuous, unpredictable
   change, in some cases with sensitive dependence on initial conditions.
4. **Class 4** — evolves to **complex, localised structures**: patterned but unstable,
   with complex interactions between local structures. This class has drawn the most
   research attention for its computational properties.

**Rule 110** is a Class 4 rule and is **Turing complete** — capable of universal
computation from nothing but a 1D binary array and a fixed lookup table. No notion of
"program" or "processor" is built into the CA definition; universality is a discovered
property of iterating a specific 8-bit rule, not a designed one.

CA applications named beyond seashell pigmentation: tumour growth, bushfire spread, and
urban growth models — each a case where local, rule-governed spatial spread is a
reasonable model of a real physical process.

### 2D cellular automata and Conway's Game of Life
`slides 13–15`

2D CA redefine neighbourhood and update rule for a grid rather than a ring. Two standard
neighbourhood choices: the **Von Neumann neighbourhood** — the four orthogonal
neighbours, $\{(0,0),(\pm1,0),(0,\pm1)\}$ — and the **Moore neighbourhood** — all eight
surrounding cells, $\{-1,0,1\}\times\{-1,0,1\}$.

The worked 2D example is [[conways-game-of-life|Conway's Game of Life]] (1970), invented by
British mathematician John Conway and explicitly inspired by von Neumann's earlier
self-replication work. Each cell is alive or dead; the update rule, applied to every cell
simultaneously each generation, is:

- A live cell with **fewer than two** live neighbours dies (loneliness).
- A live cell with **more than three** live neighbours dies (overcrowding).
- A live cell with **two or three** live neighbours survives.
- A dead cell with **exactly three** live neighbours becomes alive (reproduction).

Despite this four-rule specification, Life produces a taxonomy of long-term pattern
behaviour: **stable** patterns (still-lifes, unchanged generation to generation),
**periodic** patterns (oscillators, cycling between a small number of states), and
**mobile** patterns (gliders, which translate across the grid over successive
generations while preserving their shape). Gosper's glider gun — a configuration that
emits a steady stream of gliders — and related constructions can implement
information-carrying signals and logic gates entirely from Life's four rules, which is
what makes Life, like rule 110, **Turing complete**.

The lecture is explicit about the cost of this formalism: synchronous, deterministic
updates are strong assumptions that real systems rarely satisfy exactly. This bounds how
directly CA can stand in as a model of a real-world system rather than as a
demonstration of what local rules can produce in principle — the summary slide names
this directly as the trade-off for CA's simplicity.

### Building a CA model of a real system: predator-prey dynamics
`slides 16–19`

Motivating data: 90 years of hare and lynx population counts from Hudson Bay Company
trapping records (1845–1935) show sustained, out-of-phase oscillation — hare and lynx
populations cycle with lynx troughs and peaks lagging hare troughs and peaks.

The classical continuous-time account is the **[[lotka-volterra-model|Lotka-Volterra model]]**,
independently formulated by [[alfred-lotka]] (a US mathematician and chemist) and
[[vito-volterra]] (an Italian mathematician and physicist) in 1925–26, both building on
Verhulst's logistic equation. Assumptions: rabbits have unlimited food and grow
exponentially in the absence of foxes; foxes eat only rabbits and decline exponentially
in the absence of rabbits; the environment is static and has no independent effect on
growth or decay rates. Given rabbit population $R$ and fox population $F$:

$$\frac{dR}{dt} = \alpha R - \beta RF \qquad\qquad \frac{dF}{dt} = \delta RF - \gamma F$$

$\alpha$ is the rabbit birth rate, $\beta$ the predation rate, $\delta$ the conversion
efficiency of eaten rabbits into new foxes, and $\gamma$ the fox death rate. Both
equations can be read as inflows minus outflows, with population sizes as stocks and the
rate parameters as (here, deterministic) flow probabilities.

The lecture's bridge into CA territory is a **discrete, stochastic reformulation** of the
same dynamics, event by event rather than as a continuous rate: at each time step, a
rabbit is born with probability $\alpha$; a fox dies with probability $\gamma$; each fox
meets a rabbit with a probability proportional to the current rabbit count, and with
probability $\beta$ eats it, after which the fox breeds with probability $\delta$. Recast
this way, the model is expressible as a local-interaction, CA/ABM-style process rather
than a system of ODEs — setting up predator-prey CA as an assignment/lab direction, and
connecting this lecture's formalism back to the [[sir-model]]/[[compartmental-model]]
machinery built in [[sources/w02b-modelling-disease-spread]], which is the same move
(continuous compartmental ODE ↔ discrete stochastic agent rules) applied to a different
domain.

---

## Recall Layer

> [!question]- What makes an update rule "local" in the CA sense, and why does that
> matter for the automaton → cellular automaton generalisation?
> Local means a cell's next state depends only on the current states of its immediate
> neighbours (its neighbourhood), never on cells further away or on global information.
> This is the entire content of the generalisation from a single automaton (state
> updates from external input + own previous state) to a cellular automaton (an array of
> automata whose external input is just their neighbours' states) — no new mechanism is
> introduced, only locality of the input. `slides 4–5`

> [!question]- Derive the count: how many possible elementary 1D CA rules are there with
> 2 states and $K=3$, and how many are essentially distinct?
> $2^K = 2^3 = 8$ possible neighbourhood configurations, each mapped independently to one
> of 2 output states, gives $2^{2^K} = 2^8 = 256$ total rules. Factoring out mirror
> symmetry (left/right reflection) and complement symmetry (swapping 0 and 1) leaves 88
> essentially distinct rules. `slides 8, 11`

> [!question]- How do you convert a rule's lookup table into its rule number? Work rule
> 90's derivation.
> Order the 8 neighbourhood configurations from 111 down to 000, read off the
> corresponding output bits as a binary string, and convert that string to decimal. Rule
> 90's table gives outputs $0,1,0,1,1,0,1,0$ for configurations
> $111,110,101,100,011,010,001,000$, i.e. binary $01011010$, which equals
> $64+16+8+2=90$. `slide 10`

> [!question]- List Wolfram's four CA behaviour classes and name a rule shown as an
> example of each.
> Class 1 — fixed homogeneous state (rule 160). Class 2 — periodic/limit-cycle,
> fixed-inhomogeneous behaviour (rule 108). Class 3 — chaotic/aperiodic (rule 126).
> Class 4 — complex, unstable, interacting local structures (rule 110). `slide 12`

> [!question]- What does it mean for rule 110 and Conway's Game of Life to be "Turing
> complete", and why is this a striking claim given how each is specified?
> Turing complete means the system, given the right initial configuration, can perform
> universal computation — simulate any computable function. It's striking because
> neither system's *definition* mentions computation at all: rule 110 is an 8-bit lookup
> table over a binary array, and Life is four neighbour-count rules on a 2D grid.
> Universality is a discovered emergent property of iterating simple local rules, not a
> feature anyone designed in — demonstrated concretely via constructions like Gosper's
> glider gun implementing signals and logic gates. `slides 12, 17–18`

> [!question]- State the four rules of Conway's Game of Life precisely (the neighbour
> thresholds, not just the names).
> A live cell with fewer than two live neighbours dies (loneliness). A live cell with
> more than three live neighbours dies (overcrowding). A live cell with two or three live
> neighbours survives. A dead cell with exactly three live neighbours becomes alive
> (reproduction). All cells update simultaneously each generation. `slide 15`

> [!question]- Name the three long-term pattern classes Life produces and what
> distinguishes them.
> Stable (still-life) — unchanged from one generation to the next. Periodic (oscillator)
> — cycles through a small fixed set of states, repeating indefinitely. Mobile (glider) —
> translates across the grid over successive generations while preserving its shape.
> `slide 16`

> [!question]- What two assumptions does the lecture flag as limiting how well CA can
> model real systems, and why do they matter?
> Synchronous updates (every cell changes state at exactly the same instant) and
> deterministic updates (no randomness in the rule). Almost no real physical, biological,
> or social system updates its components in perfect lockstep with no noise — so a CA
> that matches a real system's qualitative pattern (e.g. spatial spread) may still
> misrepresent its timing or exact trajectory. `slide 18`

> [!question]- Write the Lotka-Volterra equations and state what each of the four
> parameters represents.
> $\dfrac{dR}{dt}=\alpha R-\beta RF$, $\dfrac{dF}{dt}=\delta RF-\gamma F$. $\alpha$:
> rabbit birth rate (exponential growth absent foxes). $\beta$: predation rate (rabbits
> lost per fox-rabbit encounter). $\delta$: conversion of eaten rabbits into new foxes.
> $\gamma$: fox death rate (exponential decline absent rabbits). `slides 21–22`

> [!question]- How does the lecture reformulate Lotka-Volterra as a discrete, stochastic,
> CA-compatible process, event by event?
> At each time step: a rabbit is born with probability $\alpha$; a fox dies with
> probability $\gamma$; each fox meets a rabbit with probability proportional to the
> rabbit count, eats it with probability $\beta$, then breeds with probability $\delta$.
> This replaces the continuous-rate ODE view with discrete probabilistic events per
> agent, which is exactly the form a CA or ABM update rule needs. `slide 20`

> [!failure] Common failure modes
> - Assuming rule complexity predicts CA behaviour class — rules 90 and 30 differ by only
>   a few bits in their lookup tables yet produce a highly regular self-similar pattern
>   versus an irregular chaotic-looking one; class membership is not visible from the
>   rule number without running or classifying it.
> - Forgetting the toroidal (ring) boundary convention when reasoning about edge cells —
>   without it, boundary cells have an undefined neighbourhood, and the observed "always
>   colored" edge effect in rule 30 near a finite boundary is an artefact of running out
>   of grid, not a property of the rule.
> - Treating "Turing complete" as meaning "useful as a general-purpose computer" — it
>   only means universal computation is *possible* in principle with the right initial
>   configuration; it says nothing about efficiency or practicality.

> [!exam] Exam surface
> Likely to test: computing a rule number from a lookup table (or the reverse), counting
> the rule space ($2^{2^K}$) for a given $K$ and number of states, classifying a
> described CA behaviour into one of Wolfram's four classes, stating Life's four rules
> precisely, and converting between the continuous Lotka-Volterra ODEs and their discrete
> stochastic reformulation (a strong candidate for a "translate this model" question,
> echoing the SIR ↔ ABM translation from earlier weeks).

> [!todo] Open threads
> The lecture doesn't derive Lotka-Volterra's equilibrium or oscillatory behaviour
> mathematically (no phase-plane analysis, no discussion of why the system cycles rather
> than converging) — that analysis is deferred, consistent with this being a "designing"
> rather than "analysing" week. The mean-field or continuum limit connecting the discrete
> stochastic CA reformulation back to the ODEs is also not shown.

---

## Topics covered

- [ ] `slides 1–2` — title, section divider
- [ ] `slides 3–4` — von Neumann, Ulam, Los Alamos origins; automaton → CA generalisation
  → [[#Origins and the automaton → cellular automaton generalisation]]
- [ ] `slide 5` — CA purpose, entities/state/scales, processes and scheduling →
  [[#Origins and the automaton → cellular automaton generalisation]]
- [ ] `slides 6–11` — 1D elementary CA: space/state/neighbourhood/time, update rule,
  lookup table, rule 90 worked, rule 30 and *Conus textile* →
  [[#Elementary 1D cellular automata]]
- [ ] `slide 11` — rule space counting (256 → 88) → [[#Elementary 1D cellular automata]]
- [ ] `slide 12` — Wolfram's four classes, rule 110 and Turing completeness →
  [[#Wolfram's four classes and universal computation]]
- [ ] `slide 13` — CA applications (seashells, tumours, bushfires, cities)
- [ ] `slide 14` — summary of 1D material
- [ ] `slides 15–16` — 2D neighbourhoods (Von Neumann, Moore), Conway's Game of Life
  origin and rules → [[#2D cellular automata and Conway's Game of Life]]
- [ ] `slide 17` — Life pattern classes (stable, periodic, mobile) →
  [[#2D cellular automata and Conway's Game of Life]]
- [ ] `slide 18` — Gosper's glider gun, Turing completeness, CA limiting assumptions →
  [[#2D cellular automata and Conway's Game of Life]]
- [ ] `slides 19–22` — Hudson Bay hare/lynx data, Lotka-Volterra assumptions and ODEs,
  discrete stochastic reformulation → [[#Building a CA model of a real system: predator-prey dynamics]]

## Connections

`See also:` [[cellular-automaton]], [[game-of-life]], [[wolfram-classes]],
[[turing-completeness]], [[lotka-volterra-model]], [[compartmental-model]], [[sir-model]],
[[w04a-complex-systems-and-emergence]] (this lecture's companion),
[[sources/w02b-modelling-disease-spread]] (the ODE ↔ stochastic-agent translation applied
to disease rather than predation).
