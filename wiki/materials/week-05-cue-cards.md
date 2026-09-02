#flashcards/week-05

# Week 5 Cue Cards

Cards drawn from [[w05a-sensing]] and [[w05b-adaptation-and-objectives]], their digests, and
the prescribed reading [[kennedy-2012-modelling-human-behaviour]] — the ODD design concepts
that govern agent behaviour, the sensing experiments on the
[[business-investment-model]], and what to put inside a decision rule when the agent is
supposed to be a person.

## Elaborative Interrogation

A modeller doesn't know how people choose between four options, so they draw uniformly at random and call it a neutral placeholder for their ignorance. Why is Kennedy adamant that this is the opposite of neutral?
?
A uniform distribution is a specific empirical claim, not the absence of one. It asserts that all options are equally likely, that agents have no preferences, that they don't consider consequences, that they have no memory of previous choices, and that they are *more consistent* than the data shows. Kennedy's evidence that it's false: asked to pick a number between one and four, roughly 50% of people say "three" — people cannot produce randomness even when instructed to. See [[stochasticity]], [[rational-choice-theory]].
#card/cmas #card/week-05

In the business investment model, widening the sensing radius from 1 to 2 to 5 raised mean investor wealth each time. Widening it to 8 lowered it. Why does more information stop helping?
?
Two mechanisms compound. The landscape is uniformly random with no correlation between adjacent patches, so a wider view reveals more *options* but no **gradient** — nothing indicating which direction is better. And a larger radius is a larger effective step size, so agents reach a local optimum faster and then stop exploring. Muñoz labelled the effect the "paradox of choice" but explicitly marked that framing as an untested hypothesis. See [[imperfect-information]].
#card/cmas #card/week-05

Switching on a fully connected communication network gave every agent visibility of every other agent's situation — strictly more information than a radius-1 neighbourhood — yet final mean wealth did not beat the radius-1 baseline. Why not?
?
Knowing *how well* other agents are doing lets an agent compare itself against the average, but conveys nothing about *which direction to move*, because the uniform random landscape has no structure to point along. Agents also still move only one cell per tick, so the extra information cannot be acted on even where it would be informative. Information only helps to the extent the underlying landscape has exploitable structure. See [[agent-neighbourhood]], [[agent-interaction]].
#card/cmas #card/week-05

Watching the business investment model tick by tick, mean profit jumps sharply on the very first year and then flattens for the remaining 24. Why is the first step special?
?
Profit and risk are drawn from uniform distributions, so any given neighbouring patch has roughly a 50/50 chance of beating the agent's current one. Across eight neighbours, an agent is almost certain to find at least one that both raises profit and lowers risk — so the first move is essentially guaranteed to improve things. Later moves face the same odds but from a progressively higher baseline, so the achievable increment shrinks with every step.
#card/cmas #card/week-05

Agents in the business investment model become steadily *less* willing to switch as the run proceeds, even when more profitable opportunities are visible. Which term in the utility function causes this, and how?
?
The survival factor $(1-F)^T$. As the remaining horizon $T$ shrinks, the wealth term $(W+TP)$ contributes less while the penalty for a nonzero failure probability stays, so low-risk patches dominate the ranking. Because failure is catastrophic — wealth resets to zero — an agent late in the run has no time left to recover from one, so it settles on a local optimum and stagnates. See [[objective-function]].
#card/cmas #card/week-05

The business investment model's utility is $U = (W + TP)(1-F)^T$. Why are the wealth and survival terms multiplied rather than optimised as two separate objectives?
?
Because an opportunity is worth what it pays *times* the chance it survives to pay it — the two are not independent goods that can be traded off after the fact. Multiplying conflates them deliberately, so a high-profit patch with a high failure risk is automatically discounted. Handling them separately would require two equations and a different model, and would lose the risk-aversion-over-time behaviour the single product generates.
#card/cmas #card/week-05

The business investment model randomises which agent updates first on each tick, rather than iterating over agents in a fixed order. Why does that choice matter substantively rather than just cosmetically?
?
Opportunities are exclusive — one agent per patch — so whoever moves first claims the best available option. A fixed or wealth-ordered loop would let early movers compound their advantage every tick, and the resulting wealth distribution would be an artefact of the iteration order rather than a property of the model. Randomising ensures wealthier agents get no first-mover advantage. Simultaneous claims on a shared resource are a race condition, and resolving them is a [[scheduling]] decision. See [[agent-interaction]].
#card/cmas #card/week-05

Gigerenzer's fast-and-frugal decision trees ask only three sequential questions. Kennedy singles them out as especially suited to agent-based modelling for two distinct reasons — what are they?
?
**Accuracy**: the ICU heart-attack tree outperformed both the heart disease predictive instrument and physicians, and the bail tree explained 92% of two UK magistrates' decisions — so simplicity costs nothing here. **Cost**: the trees are computationally trivial and scale to large agent populations, which [[cognitive-architecture|cognitive architectures]] like Soar and ACT-R do not. Empirically grounded, accurate, cheap and readable at once. See [[fast-and-frugal-heuristics]].
#card/cmas #card/week-05

NetLogo's Wolf Sheep Predation model runs away to exponential sheep growth when grass is switched off, but the Week 4 cellular-automaton predator-prey model never can. What structural difference explains this?
?
In the CA version the grid itself bounds the resource — a cell holds one occupant — so the model structure imposes a carrying capacity without anyone specifying one. In the NetLogo version sheep are turtles with no resource constraint at all: only wolves starve, so nothing limits sheep growth. Adding grass as a consumable resource introduces the missing bound and restores the coupled oscillations. Model *structure*, not parameters, determines which dynamics are even reachable. See [[model-structure]], [[lotka-volterra-model]].
#card/cmas #card/week-05

Kennedy says social insects and slime moulds can be modelled faithfully with fixed stimulus-response rules, but social mammals cannot. What capability makes the difference, and why does it matter for an ABM of people?
?
A **theory of mind** — the agent's own internal model of other agents' goals, knowledge and feelings. Insects appear fully driven by inherited instincts defining their responses to stimuli; mammals run general problem solving over a model of others, which is why their social behaviour is more complicated than a fixed instinct set could produce. A human ABM built purely on stimulus-response rules is choosing to omit the mechanism that makes human sociality what it is. See [[social-influence]].
#card/cmas #card/week-05

Surowiecki showed that groups can outperform every individual within them, yet Kennedy presents social influence as the thing that *destroys* this. Why are these consistent?
?
Collective accuracy comes from the **differences** between members' independent evaluations, aggregated afterwards — not from compromise or consensus. Social influence produces conformity, which removes exactly the independence and diversity the aggregation relies on. So the mechanism that makes a crowd social is the mechanism that makes it stop being wise. See [[social-influence]], [[collectives]].
#card/cmas #card/week-05

Why does COMP90083 require a DOI on every citation, with presentation marks deducted for missing ones?
?
Because fabricated references are the characteristic failure of AI-assisted writing, and the subject has caught it: students citing work that does not exist, and citing work referenced *by* other papers that turned out to be hallucinated in turn. A DOI makes verification cheap enough to do on every citation. The generative-AI policy permits use with disclosure, but responsibility for errors stays with the author.
#card/cmas #card/week-05

## Mechanism

Starting from a definition of the state set and the neighbourhood, derive the number of possible rule tables for a cellular automaton with $S$ states and $N$ cells in its neighbourhood.
?
1. Each cell in the neighbourhood can hold any of $S$ states, so there are $S^N$ distinct neighbourhood configurations.
2. A rule table maps each configuration independently to one of $S$ outputs.
3. So the number of rule tables is $S^{S^{N}}$.

Check: binary elementary CA, $S=2$, $N=3$ gives $2^{2^3} = 256$ — the familiar rule 30 / rule 90 / rule 110 numbering. Three states over the same neighbourhood gives $3^{27} \approx 7.6 \times 10^{12}$. The count is doubly exponential in $N$. See [[cellular-automaton]].
#card/cmas #card/week-05

Walk through one complete tick of the business investment model, from an agent standing on a patch to its updated wealth.
?
1. **Repositioning.** The agent evaluates its own opportunity and every *unoccupied* opportunity within its sensing radius, computing $U = (W+TP)(1-F)^T$ for each.
2. It moves to the best, or stays if its current patch wins. Only one agent may occupy an opportunity.
3. **Accounting.** With probability $F$ of its current business, the business fails and wealth $W$ resets to **zero**.
4. Otherwise $W$ increases by $P$.

One tick is one year; runs last 25 years. Agent order is randomised across the population each tick. See [[business-investment-model]].
#card/cmas #card/week-05

State the business investment model's objective function and say what each factor represents.
?
$$U = (W + TP)(1 - F)^{T}$$
- $(W + TP)$ — **projected wealth**: current wealth $W$ plus horizon $T$ years of annual profit $P$.
- $(1-F)^{T}$ — **probability of surviving** $T$ years given an annual failure probability $F$.

Multiplied, not summed: an opportunity is worth what it pays times the chance it survives to pay it. See [[objective-function]].
#card/cmas #card/week-05

When specifying sensing for an ODD description, what three sub-questions must be answered — and what is the standard four-way classification underneath the first of them?
?
The three questions: (1) **what information** — which state variables does the agent use? (2) **which entities** — which other agents and parts of the environment can it obtain them from? (3) **how** — is the information perfect, or subject to error or bias?

Variable scope, for question 1: **global** (varies over time only — interest rate, weather); **local environmental** (varies over space — a patch's elevation or resources); **agent** (own or another agent's wealth, bearing, type); **model parameters** (Interface sliders, what BehaviorSpace sweeps). See [[agent-sensing]].
#card/cmas #card/week-05

An agent's observation of its world can be imperfect in four distinguishable ways. Name them, and say which pair behaves differently under repeated observation.
?
1. **Range** — senses only out to some distance.
2. **Coverage of agents** — only a subset of other agents.
3. **Coverage of variables** — only some variables of the environment, itself, or others.
4. **Accuracy** — error on what it does observe.

Within (4), **random uncertainty averages out** over repeated observation while **consistent bias does not** — which is why they must be modelled separately, and why bias shifts a model's conclusions in a way noise does not. See [[imperfect-information]].
#card/cmas #card/week-05

Muñoz proposed rewriting the business investment model's agents as satisficers. Give the concrete rule, including what the agent loses.
?
1. Define a satisficing threshold: a **minimum rate of return, say 5% per year** over the horizon being considered.
2. If the agent's current investment clears the threshold, it stays — no evaluation of alternatives at all.
3. If it does not, the agent moves.
4. Crucially, the agent now has **no ability to sense other opportunities**, so it moves to a **randomly chosen available patch**.

The 5% figure is not arbitrary: investment products are commonly pitched as returning 4–5% *over inflation*. See [[satisficing]], [[threshold-rule]].
#card/cmas #card/week-05

State Latané's law of social impact, define its terms, and explain what the exponent implies.
?
$$I = sN^{t}$$
- $I$ — influence, as the percentage of subjects conforming or imitating.
- $s$ — a constant associated with the circumstances.
- $N$ — the number of others exerting influence.
- $t$ — a factor **less than one**, often near $\tfrac{1}{2}$.

Because $t<1$ the relationship is sublinear, so influence **saturates**: the tenth influencer adds far less than the second. The same mechanism produces bystander inhibition, by diffusing the responsibility to act across the group. See [[social-influence]].
#card/cmas #card/week-05

Kennedy sorts every approach to modelling human behaviour into three tiers. Name them in order, with examples, and state the axis they are ordered along.
?
1. **Mathematical approaches** — random draws (rejected), threshold rules, multi-parameter functions, stock-and-flow dynamic models. Coded directly in the simulation's own language.
2. **Conceptual frameworks** — BDI, PECS, fast-and-frugal trees. Reason in beliefs, motives and cues rather than parameter arithmetic.
3. **Cognitive architectures** — Soar, ACT-R. Research-grade models of an individual mind, some at millisecond resolution.

The axis is fidelity against cost. Most ABMs belong in tier 1 or 2: if the bulk of an agent's human behaviour is irrelevant to the model's purpose and the relevant part can be specified, a mathematical approach is the right answer. See [[cognitive-architecture]].
#card/cmas #card/week-05

Write a threshold rule in Kennedy's notation, and explain why the threshold form is fully general.
?
```
IF <hunger> is below  <hungerThreshold1>                          THEN agent-dies.
IF <hunger> is above  <hungerThreshold2>                          THEN address-another-goal.
IF <hunger> is between <hungerThreshold1> and <hungerThreshold2>  THEN search-for-food.
```
Generality: thresholding and comparison are the same operation. Comparing `function1` with `function2` is comparing `(function1 - function2)` against a threshold of **0** — so every comparison can be rewritten in threshold form, which is why Kennedy uses it as the common notation for all sample rules. See [[threshold-rule]].
#card/cmas #card/week-05

An agent on a square grid has a sensing radius of $r$ cells. How many cells can it see, and what does that imply about widening the radius?
?
$(2r+1)^2 - 1$ — the square block of side $2r+1$ centred on the agent, minus the agent's own cell. So radius 1 sees 8 (the Moore neighbourhood), radius 2 sees 24, radius 5 sees 120, radius 8 sees 288. The option set grows quadratically in $r$, which is why "widen the radius a bit" escalates an agent's decision problem fast — and why the sensing radius is usually one of a model's most consequential parameters. See [[agent-neighbourhood]].
#card/cmas #card/week-05

## Contrast

An evacuation model's agents reroute around a corridor that has just become blocked. In a second version, agents begin each drill remembering where the exits were in the previous drill. Which is adaptation and which is learning, and what is the general test?
?
Rerouting mid-run is **adaptation**; carrying knowledge between drills is **learning**. The test is scope: adaptation operates *within* a simulation run — state at $t$ determines action at $t$, and nothing survives the run — while learning operates *across* runs, with the agent carrying experience forward so the rule itself changes. Muñoz flagged this as the concept most often confused and stated it appears in the exam. See [[adaptive-behaviour]], [[agent-learning]].
#card/cmas #card/week-05

Two agents face the same set of investment opportunities. One evaluates every visible option and takes the best; the other takes the first that clears a 5% return. Name each strategy and give the argument for why the second may end up better off.
?
The first **optimises**, the second **satisfices**. The optimiser settles onto the best patch it can see, becomes risk-averse as the horizon shortens, and stagnates at a local optimum. The satisficer keeps moving while below aspiration, accepts short-term decreases, and explores more of the landscape — so greedy strategies tend to be suboptimal. No guarantee attached: more movement also means more exposure to the failure probability. See [[optimisation]], [[satisficing]].
#card/cmas #card/week-05

In the business investment model no agent ever communicates with, attacks, or transfers anything to another. In what sense do the agents interact at all, and how does this differ from direct interaction?
?
They interact **indirectly**, through competition for a shared exclusive resource: only one agent may occupy an opportunity, so taking a patch denies it to everyone else. Every agent's option set is determined by where the others went, without any agent acting on another. **Direct** interaction is one agent acting on another — a predator eating prey, an infection transmitting, information passing along a network link. Stigmergy (ants following pheromone trails) is the other classic indirect case. See [[agent-interaction]].
#card/cmas #card/week-05

A house-hunter talks to the neighbours on a street, and separately gets a call from a broker about an off-market listing across the city. Which kind of neighbourhood is each, and what can only one of them do?
?
Talking to neighbours is a **radius** (spatial) neighbourhood — agents within a distance, or within grid positions. The broker's call is a **network** neighbourhood — a nominated set of agents who need not be spatially close. Only the network can deliver information that no amount of local sensing would reach. The two can coexist in one model; the business investment model has a sensing radius with an optional network layered on top. See [[agent-neighbourhood]].
#card/cmas #card/week-05

Soar and ACT-R are the two cognitive architectures Kennedy says have real communities behind them. What are they each *for*, and which one would you not reach for if your agents need explicit goals?
?
**Soar** aims to meet or exceed human performance on problem-solving tasks; it maintains an internal world model, always pursues a goal, and exposes internal state variables — which makes it readable as a BDI implementation. **ACT-R** aims to *closely match human performance data* on low-level cognition over very short periods, using symbolic and sub-symbolic representations, and has been linked to functional brain regions. ACT-R does **not** represent beliefs, desires or intentions explicitly, so it is the wrong choice when agents need explicit goals. See [[soar]], [[act-r]].
#card/cmas #card/week-05

BDI and PECS are both conceptual frameworks for modelling human decision-making, and PECS was proposed explicitly to replace BDI. What does each represent, and what was the complaint that motivated the replacement?
?
**BDI** — beliefs (the world as the agent perceives it), desires (goals), intentions (deliberative states); implemented by building a decision tree, turning it into a possible-worlds model, and deliberating. **PECS** — physical, emotional, cognitive and social factors, with an explicit pipeline from environment to internal state to drives/needs/desires to **motives** whose intensity determines behaviour. The complaint: BDI is so general that it provides little more than a way of *thinking* about cognition, with no implementation guidance. See [[bdi-architecture]], [[pecs-framework]].
#card/cmas #card/week-05

Zoom into the Mandelbrot set and the large-scale structure reappears at every scale. Muñoz used this as the *wrong* answer to "what is emergence". Why, and what is the right characterisation?
?
Self-similarity across scales is fractal structure — one scale replicating another — and says nothing about the relationship between component rules and collective behaviour. Emergence is that observing an individual does not let you *deduce* what the group will do: watch one ant or one bird and the colony's or flock's behaviour is not derivable from its rule. "Non-trivial relationships" is the operative phrase — non-trivial meaning not mathematically deducible from the individual rule. See [[emergence]].
#card/cmas #card/week-05

Rational choice theory and bounded rationality both describe agents trying to decide well. State the three assumptions rational choice makes, and what bounded rationality replaces them with.
?
**Rational choice** assumes: all possible actions are known; agents have perfect knowledge of the environment; preferences are well behaved (complete ordering, transitivity). **Bounded rationality** ([[herbert-simon|Simon]]) replaces these with limited information, limited cognitive ability and limited time — plus limits on how many variables a person can weigh and how mathematically sophisticated the weighing can be. The behavioural consequences are satisficing and fast-and-frugal heuristics. See [[rational-choice-theory]], [[bounded-rationality]].
#card/cmas #card/week-05

A flocking model produces visible flocks, and a demographic model has agents belonging to households. Only one of these counts as a "collective" in the ODD sense. Which, and what is the test?
?
The **household**. The test is whether the group has causal standing in the model: does anything reference it, does it hold state, does its state feed back into member behaviour? A household does — shared budget, membership, feedback into individual decisions. A flock does not: no boid holds a reference to it, and it exists only as a pattern an observer names. An emergent pattern is not automatically a collective. See [[collectives]], [[emergence]].
#card/cmas #card/week-05

## Failure-Mode

Your ABM of evacuation behaviour grants every agent perfect, instantaneous knowledge of the whole building. What has this quietly done to the question the model can answer?
?
It has converted a question about behaviour under uncertainty into an arithmetic exercise. The stated purpose of an ABM here is to evaluate the implications of *imperfect* decision-making on system behaviour — with perfect sensing there is no imperfection left to evaluate, and the model's output describes an optimisation problem rather than a crowd. Perfect information is a strong assumption, not a neutral default, and is a prime candidate for [[sensitivity-analysis]]. See [[imperfect-information]].
#card/cmas #card/week-05

A model adds sensing error as zero-mean Gaussian noise, and the modeller reports that it "doesn't change the results much" after averaging over runs. What kind of sensing imperfection has been silently excluded, and why does it matter?
?
**Systematic bias**. Random noise averages out over repeated observation, which is exactly why it changed little — but a consistent bias does not average out, and shifts every agent's decisions in the same direction. Real sensing errors are frequently biased rather than noisy (buyers systematically misread other bidders' seriousness), so testing only noise gives false confidence that sensing imperfection is unimportant. See [[imperfect-information]].
#card/cmas #card/week-05

An ODD description simply says nothing about learning or collectives, because the model has neither. What is wrong with this, and what should it say instead?
?
Silence is ambiguous: the reader cannot tell whether the concept was considered and excluded, or forgotten. Design concepts that genuinely do not apply should be **declared unused** — the business investment model's ODD says explicitly "learning and collectives are not used". This is the same discipline as reporting a null result: it distinguishes a decision from an omission, and it is what makes the description reproducible. See [[odd-protocol]].
#card/cmas #card/week-05

A student writes in their report: "The paradox of choice explains why sensing radius 8 underperforms radius 5." What is over-claimed here, and what could be asserted instead?
?
Muñoz offered the paradox of choice as a **label** and explicitly marked it as an untested hypothesis he had not fully worked out. What is supported is the empirical result (wealth falls at radius 8) plus the structural argument: the landscape is uniformly random with no gradient, so a wider view adds options without direction, while the larger effective step reaches a local optimum sooner. Assert the mechanism you can defend; report the label as the lecturer's framing.
#card/cmas #card/week-05

The lecture reports final mean wealth of about 140,000 at radius 1 and 165,000 at radius 5. What is wrong with quoting these as measurements, and what would produce quotable numbers?
?
Each figure is a **single run**, read off a live plot, on a landscape re-drawn between runs — so the difference is confounded with sampling variation in the landscape itself. A quotable claim needs a BehaviorSpace parameter sweep over the radius with **replicates** at each setting, reported as a distribution rather than a point. The pattern was described as stable across repeats, but no distribution was shown. See [[model-analysis]], [[stochasticity]].
#card/cmas #card/week-05

An ABM of consumer choice models the decision as "pick uniformly at random among the products in stock", on the grounds that no data on real choices was available. What has the modeller actually committed to, and what is the cheapest defensible alternative?
?
They have committed to the claim that all products are equally likely, that consumers have no preferences, no memory of past purchases and no regard for consequences — a strong claim, and demonstrably false for humans. The cheapest defensible alternative is a **threshold rule**: an IF-THEN test on an observable variable, which is simple and crude but *explainable* and criticisable, unlike a random draw. See [[threshold-rule]], [[rational-choice-theory]].
#card/cmas #card/week-05

## Deck notes

**Coverage.** 37 cards over three sources. The split is deliberate and matches the balance
requested for the Week 4 deck: 12 elaborative-interrogation cards carrying the *why*, 10
mechanism cards carrying the formalism and procedures that are actually derivable under exam
conditions, 9 contrast cards for the pairs this material invites confusing, and 6
failure-mode cards drawn mostly from the lecturer's own caveats and from what the live demo
did not establish.

**Weighted toward mechanism, on purpose.** Week 5's examinable surface is unusually
procedural for a "concepts" week: the $S^{S^N}$ rule count, the utility function and what
each factor does, the tick sequence, the four variable scopes, the four failure modes of
observation, Latané's law, and the $(2r+1)^2-1$ neighbourhood count are all things you either
can or cannot reproduce. Those get their own cards rather than being folded into prose.

**The adaptation/learning card is the one that matters most.** Muñoz stated outright that it
is examined and that it is the concept most often confused. It is written as a scenario
(evacuation drills) with the general test stated afterwards, so answering it requires
applying the distinction rather than reciting it.

**Kennedy's material is carded for transfer, not recall.** The pick-a-number statistics are
not carded as numbers — Kennedy himself says there is no serious study behind them. What is
carded is the *argument* those statistics support: what a uniform random draw actually
asserts. That argument reappears as a failure-mode card applied to a fresh scenario
(consumer choice), because the point of the reading is that you recognise the mistake in your
own model, not in Kennedy's example.

**Two cards deliberately teach epistemic caution.** The paradox-of-choice card and the
"140,000 vs 165,000" card both ask what is *over-claimed*. The lecture's headline result is
genuinely interesting and genuinely under-evidenced — one run per setting, landscape re-drawn
each time, mechanism admitted to be unresolved — and a deck that presented the result without
that caveat would be teaching the wrong lesson about reading model output.

**Excluded deliberately.** Maslow's hierarchy is not carded: as presented in the chapter it is
a five-item list with one modelling use (arbitrating competing agent priorities), and a card
would either be a bare list (banned by the no-definition-only rule) or a restatement of that
single use, which is already covered by the PECS contrast card. The basic-emotions list and
appraisal theory are likewise not carded — Kennedy states there is "wide variance of thought
on what the dimensions are", so there is nothing stable enough to test. The academic-integrity
material got one card (the DOI requirement) because it has a mechanism behind it; the rest is
policy, not content.

**Deferred.** The satisficing variant of the business investment model was never actually run
— its predicted result is a hypothesis stated at the end of Week 5b and deferred to Week 6.
The card on satisficing therefore asks for the *rule and the argument*, not for a result.
Revisit once the experiment has been run. Alternative objective functions (ignore risk;
ignore wealth and only avoid ruin) are covered in the source page but deferred here for the
same reason.

**Suggested starting interval.** 1–3 days, in whichever tool you review in.
