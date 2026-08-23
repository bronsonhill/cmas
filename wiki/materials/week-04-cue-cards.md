#flashcards/week-04

# Week 4 Cue Cards

Cards drawn from [[w04a-complex-systems-and-emergence]] and [[w04b-2d-cellular-automata]],
their digests, and Chapter 1 of [[sayama-2015-modeling-and-analysis-of-complex-systems-ch1]]
— what makes a system complex, and the two archetypal complex systems this course builds
on top of: flocking and cellular automata.

## Elaborative Interrogation

The three-body problem has exactly one more component than the exactly-solvable two-body problem, yet it has no closed-form solution and produces chaotic trajectories. Why does adding one component collapse tractability so completely?
?
Analytic solvability depends on the equations of motion decoupling into a form you can integrate directly, which the two-body problem's symmetry permits. A third mutually-interacting body breaks that symmetry: each body's motion now depends on the simultaneous positions of both others, and the resulting nonlinear coupling has no general closed-form solution. Complexity here comes from interaction structure, not particle count — the same jump appears in the [[logistic-map]] with no added components at all. See [[chaos]].
#card/cmas #card/week-04

The logistic map $x_{n+1} = rx_n(1-x_n)$ is a single deterministic equation with no random term anywhere in it. Why can its output still look chaotic?
?
Determinism only guarantees that the same input reproduces the same output — it says nothing about how sensitively output depends on input. Past a critical $r$, the map's nonlinearity causes nearby starting values to diverge exponentially under iteration (a bifurcation cascade), so long-run behaviour becomes practically unpredictable despite being, in principle, exactly computable. Chaos is a property of the dynamics, not evidence of stochasticity. See [[chaos]].
#card/cmas #card/week-04

An orchestra and a starling murmuration both consist of many interacting individuals producing coordinated collective motion. Why does the lecture treat only one of them as a complex system?
?
An orchestra's coordination comes from a conductor and a score — a central authority each player refers to, so the aggregate pattern is designed top-down and would be classified as deterministic/centralised behaviour. A murmuration has no leader: each bird reacts only to nearby birds, and the flock-level pattern is not represented anywhere in any single bird's rule. The distinguishing test is not "is the outcome coordinated" but "does anything in the system possess the global picture" — see [[decentralisation]] and [[complex-system]].
#card/cmas #card/week-04

Weaver's "problems of disorganized complexity" (an ideal gas, repeated coin tosses) also involve huge numbers of interacting components. Why doesn't Sayama's chapter classify them as complex systems?
?
Classical statistics handles disorganized complexity precisely because its components are treated as statistically independent — you can average over them and the aggregate is well described by a small number of macroscopic parameters (pressure, temperature) with no need to track interaction. A complex system's components are *interdependent*: what one does changes the local conditions for its neighbours. Sayama's "problems of organized complexity" is the space between full coupling (problems of simplicity, e.g. rigid-body mechanics) and full independence, which is exactly where classical tools stop working. See [[complex-system]].
#card/cmas #card/week-04

Sayama defines self-organisation as a system spontaneously developing macroscopic structure over time. Why doesn't that appear to violate the second law of thermodynamics?
?
The second law bounds *closed* systems, where total entropy cannot decrease. Self-organising systems are open: they exchange energy or matter with an environment, so local order can increase while the combined system-plus-environment entropy still rises. A crystal forming from solution, a flock coalescing, or a market forming a price all draw on external structure or energy rather than manufacturing order from nothing. See [[self-organisation]].
#card/cmas #card/week-04

Emergence and self-organisation are routinely used interchangeably. What does Sayama's chapter say is actually different between them, and why does the difference matter for modelling?
?
Emergence is about *scale* alone — a nontrivial relationship between microscopic rules and a macroscopic property (Bar-Yam's definition), which can in principle be evaluated on a single static configuration. Self-organisation is about scale *and time* — it names the dynamical process by which that macroscopic pattern comes into being as the system evolves. Practically: emergence is what you check for in a model's output at a given moment; self-organisation is what you check for by watching the trajectory. A model can show emergent structure without ever demonstrating how it self-organised, and vice versa. See [[emergence]] and [[self-organisation]].
#card/cmas #card/week-04

A boid only senses other boids within a bounded angle and distance, and follows three purely local rules. Why is "no rule specifies the flock shape" the whole point rather than a limitation?
?
If flock-level behaviour is exactly what you're trying to explain, then coding it directly into each agent (e.g. "steer to maintain a wedge formation") would make the model circular — you'd be assuming the answer. Boids demonstrates that realistic, robust flocking patterns can arise purely from local sensing and three simple rules with no agent aware of, or aiming at, the group shape. That is the empirical claim being tested: individual-level rules are *sufficient* to generate the macroscopic pattern. See [[flocking]] and [[boids]].
#card/cmas #card/week-04

A CA's next state depends only on a small local neighbourhood, never the whole grid. Why does that restriction not prevent global, complex patterns from forming?
?
Locality constrains what a single cell's *update rule* can reference, not what patterns can propagate across many update steps. Information travels one cell per tick through the neighbourhood structure, so over enough generations, local interactions compound into structures spanning the whole grid — gliders traverse arbitrary distances, rule 30's triangle grows indefinitely. Complexity is generated by iteration, not by any single cell seeing more than its neighbours. See [[cellular-automaton]].
#card/cmas #card/week-04

Why does a CA rule table's *size* grow so much faster than its neighbourhood size?
?
An elementary 1D CA with $k=2$ states and neighbourhood size $K=3$ has $2^K = 8$ possible neighbourhood configurations, each independently mapped to an output state, giving $2^{2^K} = 2^8 = 256$ possible rule tables — a double exponential. Moving to a Moore neighbourhood (9 cells including self) with 2 states gives $2^{2^9} = 2^{512}$ possible rules. Rule-space size explodes far faster than neighbourhood size, which is why even $K=3$, 2-state CA already contain rules as behaviourally rich as rule 30 and rule 110. See [[cellular-automaton]].
#card/cmas #card/week-04

Conway designed Life's four rules (loneliness, overcrowding, survival, reproduction) by hand, with no proof they would be interesting. Why does the fact that Life turned out to be Turing complete matter, beyond being a curiosity?
?
Turing completeness means Life's cellular substrate — a grid of on/off cells with one fixed local rule — is expressive enough to implement any computable function, including logic gates and memory, given a suitable initial configuration (Gosper's glider gun and related constructions carry the signals). It establishes an upper bound on what "many parts, simple rule" systems can produce: not just visually rich patterns, but universal computation, with no rule change and no added structure. Rule 110 makes the same point for 1D CA. See [[game-of-life]] and [[turing-completeness]].
#card/cmas #card/week-04

The lecture is explicit that CA updates are synchronous and deterministic, and flags this as a limiting assumption. Why does that specifically limit CA as models of real systems, rather than being a neutral simplification?
?
Real physical, biological and social systems rarely update all components at exactly the same instant with a fixed rule — cells divide asynchronously, agents act on different clocks, and behaviour has stochastic variation. A CA that assumes synchronous, deterministic update can produce artefacts (e.g. patterns that depend on update order, or that are too regular) that don't correspond to anything in the target system. It's a modelling choice traded for tractability, not a discovered fact about how such systems actually behave — the same trade-off the [[deterministic-model]] concept flags for the [[sir-model]]. See [[cellular-automaton]].
#card/cmas #card/week-04

The Lotka-Volterra ODEs assume rabbits have unlimited food and grow exponentially absent foxes. Why is that assumption necessary for the model to produce sustained oscillation rather than a stable equilibrium?
?
Unlimited food removes any self-limiting term (no carrying-capacity term like in the logistic equation) from the rabbit growth rate, so rabbit population can regrow fully between fox-driven crashes. If rabbit growth were capped by food, the rabbit population would settle toward a fixed carrying capacity rather than overshoot and crash, damping the cycle rather than sustaining it. The out-of-phase hare/lynx cycles in the Hudson Bay data are the behaviour this specific (unrealistic) assumption is built to reproduce. See [[lotka-volterra-model]].
#card/cmas #card/week-04

## Mechanism

Walk through Wolfram's method for numbering an elementary 1D CA rule, using rule 90 as the anchor. What determines the rule's name?
?
1. Enumerate all $2^K = 8$ possible neighbourhood configurations for $K=3$ (cell plus two neighbours), ordered from `111` down to `000` as a 3-bit binary count.
2. For each configuration, the rule table specifies the resulting output state (0 or 1) for the centre cell.
3. Reading those 8 output bits in order as a single binary number gives the rule's decimal name — e.g. rule 90's output bits, read as binary, equal 90.
4. Applying that same lookup to every cell simultaneously each tick produces the next generation; a ring topology handles the boundary.
The rule number is purely a compact encoding of the lookup table, not a description of the pattern it produces. See [[cellular-automaton]].
#card/cmas #card/week-04

Give Wolfram's four CA behaviour classes in order, and one identifying feature of each you could use to classify an unfamiliar rule from its output.
?
1. **Class 1** — converges to a single fixed, homogeneous state (everything dies or freezes); identify by a pattern that stops changing entirely within a few steps.
2. **Class 2** — settles into periodic or limit-cycle behaviour; identify by a pattern that repeats with a fixed period, often localised.
3. **Class 3** — chaotic and aperiodic, sensitive to initial conditions; identify by an irregular, seemingly patternless output that never stabilises or repeats (rule 30).
4. **Class 4** — complex, neither fully ordered nor fully chaotic, with localised structures that interact and persist (rule 110, and Life by extension); identify by long-lived, moving or interacting local structures against an otherwise quiet background — the class associated with Turing completeness.
See [[wolfram-classes]].
#card/cmas #card/week-04

Starting from a live cell with two live neighbours and ending at the next generation, trace what Conway's Game of Life does on one update tick across a whole grid.
?
1. For every cell simultaneously, count live neighbours using the Moore neighbourhood (8 surrounding cells).
2. A **live** cell with fewer than 2 live neighbours dies (loneliness).
3. A **live** cell with 2 or 3 live neighbours survives.
4. A **live** cell with more than 3 live neighbours dies (overcrowding).
5. A **dead** cell with exactly 3 live neighbours becomes alive (reproduction).
6. All cells apply their computed next state at once — synchronous update — producing the next generation from the previous one, never from partially-updated cells.
See [[game-of-life]].
#card/cmas #card/week-04

State the three local rules a boid follows and, for each, what it is steering relative to.
?
1. **Separation** — steer away from nearby boids to avoid crowding, relative to their individual positions.
2. **Cohesion** — steer toward the average *position* of nearby boids.
3. **Alignment** — steer toward the average *heading* (direction of travel) of nearby boids.
All three are computed only over boids within a bounded angular field of view and sensing distance — never the whole flock. See [[boids]] and [[flocking]].
#card/cmas #card/week-04

Give the Lotka-Volterra ODE system for rabbits $R$ and foxes $F$, and say what each term represents.
?
$$\frac{dR}{dt} = \alpha R - \beta RF, \qquad \frac{dF}{dt} = \delta RF - \gamma F$$
$\alpha R$ is unconstrained exponential rabbit growth absent foxes. $\beta RF$ is predation loss, proportional to the *product* of both populations (an encounter-rate term, same structure as $\beta SI$ in the [[sir-model]]). $\delta RF$ is fox growth from those same encounters, scaled by a separate conversion efficiency $\delta$. $\gamma F$ is exponential fox decline absent rabbits. See [[lotka-volterra-model]].
#card/cmas #card/week-04

The lecture recasts Lotka-Volterra as a discrete, probabilistic, CA-compatible process. Walk through one step of that reformulation.
?
1. With probability $\alpha$, a rabbit is born.
2. With probability $\gamma$, a fox dies.
3. Each fox encounters a rabbit with probability proportional to the local rabbit count.
4. On encounter, the fox eats the rabbit with probability $\beta$.
5. After eating, the fox breeds with probability $\delta$.
Each of the four ODE rate constants ($\alpha, \beta, \gamma, \delta$) becomes a per-step probability governing a discrete, local event rather than a continuous population-level rate — the move that makes the same dynamics expressible as a CA or ABM rule. See [[lotka-volterra-model]] and [[cellular-automaton]].
#card/cmas #card/week-04

## Contrast

What is the key difference between the Von Neumann and Moore neighbourhoods in a 2D CA?
?
The Von Neumann neighbourhood is the 4 orthogonal neighbours (up, down, left, right) — no diagonals. The Moore neighbourhood is all 8 surrounding cells, orthogonal plus diagonal. The choice changes both the CA's rule-table size (fewer configurations under Von Neumann) and its qualitative behaviour: Conway's Game of Life is defined over the Moore neighbourhood, and substituting Von Neumann changes which configurations count as "crowded" or "isolated" even with the same numeric thresholds. See [[cellular-automaton]].
#card/cmas #card/week-04

Distinguish an "automaton" from a "cellular automaton" as the lecture defines them.
?
An automaton is a single theoretical machine that updates its internal state as a function of external inputs and its own previous state. A cellular automaton extends this into an *array* of automata (cells) arranged in a discrete space, where each cell's "external input" is specifically the current states of its nearby cells rather than some arbitrary external signal. A CA is many automata coupled only through spatial locality, not a different kind of object. See [[cellular-automaton]].
#card/cmas #card/week-04

Both a starling murmuration and Conway's Game of Life are offered as archetypal complex systems, but one is built from continuous agents with steering behaviour and the other from a fixed grid of binary cells. What do they share that makes both count?
?
Both have many components, local (not global) interaction, deterministic-or-simple rules per component, and no central controller — satisfying [[decentralisation]]'s distribution/bounded-knowledge/parallelism criteria — and both produce macroscopic pattern (flock shape, gliders/oscillators) that is not directly specified by any single component's rule, i.e. [[emergence]]. The substrate (continuous positions vs discrete cell states) differs, but the structural conditions that make a system "complex" in Sayama's sense are substrate-independent. See [[complex-system]].
#card/cmas #card/week-04

Positive and negative feedback are both "amplification/damping of a fluctuation" mechanisms. Name one concrete phenomenon this course has already used to illustrate each, and state the qualitative difference in outcome.
?
**Positive feedback** amplifies a fluctuation — the exponential growth phase of the [[sir-model]], where more infections produce more contacts-with-infecteds, producing still more infections; the outcome diverges away from the starting state. **Negative feedback** damps a fluctuation — a system settling toward a steady-state plateau (e.g. susceptible depletion eventually halting the epidemic's growth); the outcome converges toward an equilibrium. The mechanism in both cases is a change feeding back into its own rate of change; only the sign differs. See [[feedback]].
#card/cmas #card/week-04

Rule 30 and rule 110 are both single elementary 1D CA rules capable of producing complex-looking output, but they sit in different Wolfram classes. What distinguishes them?
?
Rule 30 is Class 3: its output is chaotic and aperiodic with no persistent localised structure — the pattern looks patternless throughout, resembling *Conus textile* shell pigmentation. Rule 110 is Class 4: its output contains localised structures ("gliders" analogous to Life's) that persist, move, and interact against a quieter background, and it is this structured local interaction — not mere irregularity — that makes rule 110 Turing complete. Chaotic ($\ne$) complex: chaos lacks the stable local structures computation needs to encode and transmit information. See [[wolfram-classes]] and [[turing-completeness]].
#card/cmas #card/week-04

## Failure-Mode

You build a CA rule for tumour growth using the Moore neighbourhood and a rule you tuned to look qualitatively "cancer-like" in a demo. What did the lecture's own caveat about CA modelling say you haven't established?
?
Producing plausible-looking output is not the same as validating the model against real growth-pattern data or establishing that the local rule corresponds to actual cell-level biology, and the model still carries the deterministic/synchronous-update assumption real tumour growth doesn't satisfy. A CA that merely "looks right" has demonstrated the framework is expressive, not that this particular rule is a correct account of the target system — the same gap [[model-analysis]] flags for ABMs generally: a model producing plausible output has established sufficiency, not correctness. See [[cellular-automaton]].
#card/cmas #card/week-04

You set the boid sensing radius to effectively infinite (every boid senses every other boid) and expect "better" flocking. What actually happens to the model, and what property have you broken?
?
Removing the bounded sensing radius removes the *local* interaction structure boids depends on: cohesion and alignment now average over the entire population every step, and any subgroup structure or realistic flock-splitting behaviour disappears, since every boid effectively has global information. You have broken [[decentralisation]]'s bounded-knowledge condition, turning a locally-driven emergent system into one with an implicit global signal each agent can access — the model no longer tests the hypothesis it was built to test. See [[boids]] and [[decentralisation]].
#card/cmas #card/week-04

You update a CA asynchronously, cell by cell in raster order, using rules designed for synchronous update, and don't account for it. What breaks, using Life as the concrete case?
?
A cell updated later in the sweep reads neighbours that have *already* been updated for the current tick, coupling the outcome to arbitrary scan order rather than to the previous generation alone. Patterns designed assuming simultaneous update — a glider, an oscillator — rely on every cell seeing the *same* prior-generation snapshot; under raster-order asynchronous update, gliders distort or collapse because part of their neighbourhood has already moved. See [[game-of-life]] and [[cellular-automaton]].
#card/cmas #card/week-04

You reduce Lotka-Volterra's four parameters to two by setting $\beta = \delta$ (predation loss rate equals fox growth-from-predation rate), reasoning that "a fox eaten rabbit becomes a fox". What assumption does that conflate, and why is it usually wrong?
?
$\beta$ is the probability an encounter results in the rabbit being eaten; $\delta$ is a separate conversion efficiency — how much that predation event contributes to fox reproduction, which depends on caloric conversion, gestation limits and more. Setting them equal assumes perfect, immediate energy conversion from prey to predator offspring, which no real predator-prey system exhibits. Collapsing the two independent biological processes into one parameter removes exactly the flexibility the model needs to fit different species' actual dynamics. See [[lotka-volterra-model]].
#card/cmas #card/week-04

You claim a system is "self-organising" because you observe emergent structure in a single snapshot of its state. What has been shown, and what hasn't?
?
A single snapshot can support a claim of [[emergence]] — that the macroscopic property doesn't reduce simply to the microscopic rule — but self-organisation additionally requires evidence about the *trajectory*: that the structure developed spontaneously over time from a less-structured state, without external imposition. A pattern could equally have been present in the initial condition rather than having self-organised into being. Emergence is checkable from statics; self-organisation requires dynamics. See [[self-organisation]] and [[emergence]].
#card/cmas #card/week-04

## Deck notes

**Coverage.** 24 cards across both Week 4 lectures and Sayama Ch. 1 — deliberately weighted
toward mechanism and contrast over pure recall, since this week is where the subject moves
from epidemic-specific machinery to the general vocabulary (complex systems, emergence,
self-organisation, decentralisation, feedback) and formal toolkit (CA, Wolfram classes,
Lotka-Volterra) the rest of the course builds on. Per the brief for this deck, technical
cards (rule numbering, Wolfram-class identification, the Life update algorithm, the
Lotka-Volterra ODEs and their discrete reformulation) sit alongside conceptual ones
(emergence vs self-organisation, why locality doesn't prevent global pattern, why an
orchestra isn't a complex system) at roughly even weight.

**Design choices.** Emergence and self-organisation get three cards between them (one
elaborative, one contrast, one failure-mode) because Sayama's chapter treats their conflation
as the single most common conceptual error in the field, and the scale-vs-scale+time
distinction is easy to state but easy to blur under exam pressure. Wolfram's four classes get
a dedicated mechanism card asking for an *identifying feature* per class rather than just the
names, since classification-from-output is the actually testable skill. The CA rule-numbering
mechanism card is included because it's the one piece of Week 4 with a genuine step-by-step
algorithm behind a "just a number" fact (rule 90, rule 30, rule 110) that's otherwise easy to
memorise without understanding.

**Excluded deliberately.** Sayama's seven-cluster taxonomy of complex systems science
(nonlinear dynamics / systems theory / game theory / pattern formation / evolution &
adaptation / networks / collective behaviour) is recognition material with no mechanism or
contrast behind it at this stage — a single card would either be a bare list (banned by the
skill's no-definition-only rule) or artificially inflate the deck; revisit if a later lecture
develops one of the seven clusters further. The specific boids output metrics (mean
flock-mates, nearest-neighbour distance, heading standard deviation) are noted in the source
page but are measurement definitions rather than examinable mechanism, so no card was written
for them. The full count of 88 essentially-distinct elementary rules (vs 256 total) isn't
carded on its own — folded into the neighbourhood-size mechanism card instead, since isolating
it would be a bare-number recall card.

**Deferred.** Assignment 1 asks for a compartmental model extension, not a CA or boids model,
so no assignment-application cards were written for Week 4 material — revisit if a later week
connects CA/ABM design explicitly back to the assignment. The predator-prey CA mentioned as a
"lab/assignment direction" isn't developed enough yet to card its actual implementation.

**Suggested starting interval.** 1–3 days, in whichever tool you review in.
