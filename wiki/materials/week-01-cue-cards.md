#flashcards/week-01

# Week 1 Cue Cards

Cards drawn from [[w01a-introduction]] and [[w01b-modelling-cycle]] — the definitional
chain, complex systems and emergence, and the modelling cycle.

## Elaborative Interrogation

A colleague defines a model as "a representation of a real system". Why does the subject insist on "a representation of a real system for a purpose"?
?
Because purpose is what licenses simplification. Every model discards most of the real system, and the only principled basis for deciding what to discard is the question being answered — in a disease-transmission model household size matters because it shapes contact structure, while supermarket basket size does not. Without a purpose there is no criterion for inclusion, and a model can only be judged adequate or inadequate *for* something, never right or wrong in the abstract.
#card/computational-modelling-and-simulation #card/week-01

Both the geocentric and heliocentric models were built for the same purpose — explaining observed planetary motion — and both could account for the observations. Why did the heliocentric model displace the geocentric one?
?
Not by explaining *more*, but by explaining the same observations with far less machinery. The geocentric model needed epicycles — secondary orbits layered on the main orbits — purely to account for planets appearing to reverse direction. Moving the Sun to the centre made that apparatus unnecessary. This is [[occams-razor]] as a design criterion, and the deeper lesson is that baroque complexity is often a symptom of a wrong structural assumption rather than a sign of thoroughness.
#card/computational-modelling-and-simulation #card/week-01

A cut-away diagram of the Earth's interior is labelled "not to scale" and draws the crust far thicker than it really is. Why is this a good model rather than a defective one?
?
Because the distortion serves the purpose. The crust is where we live and mine, so it is the part the diagram exists to show; drawing it to true scale would render it an invisible sliver. Abstraction is not a compromise forced by limited resources — it is the mechanism by which a model becomes usable, and a distortion is legitimate exactly when the purpose requires it.
#card/computational-modelling-and-simulation #card/week-01

Step 2 of the modelling cycle says to start simple and add detail later, in priority order. Why is that better than implementing everything you know about the system at once?
?
A simple behaviour may be two or three lines of code, whereas building everything simultaneously produces a mass of bugs with no working baseline to isolate them against. Implementation is also the step that reveals the consequences of your assumptions, so you want those consequences legible one at a time. Extra detail additionally costs compute and interpretability while often obscuring the very mechanism you were trying to isolate.
#card/computational-modelling-and-simulation #card/week-01

Beyond cost and convenience, why are agent-based models especially valuable in social science?
?
They allow behavioural interventions to be tested on simulated people rather than real ones. A policy can be checked for whether it is likely to help before being deployed on a population — an ethical advantage, not merely a practical one, since the corresponding real-world experiment would often be impermissible. This is the same [[counterfactual]] capability that let COVID compliance scenarios inform lockdown policy.
#card/computational-modelling-and-simulation #card/week-01

## Mechanism

Starting from a real-world problem and ending with an audience who can act on it, what are the six steps of the modelling cycle?
?
1. **Formulate the question** — clear, specific, non-trivial, answerable by a model; defines scope, and named the hardest step.
2. **Assemble hypotheses** for essential processes and structures — open-ended research and brainstorming, then filtering; start simple.
3. **Choose model structure** — scales, entities, state variables, processes, parameters; produce a written outline before code.
4. **Implement** — turn the written design into a runnable simulation.
5. **Analyse, test and revise** — the most time-consuming step; frequently forces reformulating the question.
6. **Communicate** — convey the insight to stakeholders.
#card/computational-modelling-and-simulation #card/week-01

The modelling cycle is drawn as a clean loop. In what way is that diagram misleading, and what does it imply about a first model?
?
Any step can send you back to *any* earlier step, not just the preceding one — you can reach implementation and discover the question itself was wrong, or begin choosing structure and realise something essential was omitted. The cycle therefore makes modelling an empirical practice rather than a one-shot translation from system to code, and it establishes that a first model is *expected* to be wrong.
#card/computational-modelling-and-simulation #card/week-01

In the NetLogo Flocking model, what rules is each [[boids|boid]] actually given, and what appears at the level of the population?
?
Each boid perceives only neighbours within a **vision** radius and follows three local rules — **separation** (keep a minimum distance), **alignment** (steer towards neighbours' heading), and **cohesion** (move towards the local group) — bounded by a maximum turn rate and speed. Clustering and a common heading appear across the population, and neither is stated anywhere in the rules. No boid has global information and nothing coordinates the flock.
#card/computational-modelling-and-simulation #card/week-01

You have a clear research question and a set of hypotheses. What five things must step 3 of the cycle pin down, and what is the deliverable?
?
**Scales** (how big a world, over what time span), **entities** (what exists — and, implicitly, what does not), **state variables** (what each entity must remember, e.g. a searcher's current mode), **processes** (sensing, moving, consuming, reproducing), and **parameters** (detection radius, step size, agent count — the quantities you later sweep and calibrate). The deliverable is a **written outline in plain language, not code**, so a domain expert who cannot read code can review the mechanisms.
#card/computational-modelling-and-simulation #card/week-01

## Contrast

An ABM and a machine-learning model both produce predictions about a system. What is the fundamental difference in where their content comes from?
?
An ML model is *fitted from training data* — the relationships are learned. An ABM *encodes hypothesised rules* specified from theory or domain knowledge about how individuals behave, and is then tested against observed patterns. The ABM's rules are an input asserting a mechanism; in ML the relationships are an output of the fitting procedure.
#card/computational-modelling-and-simulation #card/week-01

Two agents face the same choice. One optimises, the other satisfices. What is the difference, and why is satisficing often the more defensible modelling assumption?
?
An optimiser searches for the **best possible** option given an objective and constraints; a satisficer sets an aspiration level and takes the **first option that meets it**, stopping there without guaranteeing no better option exists. Satisficing is often more defensible because real people, firms and animals act under limited information, time and computation — modelling them as perfect optimisers imports a rationality the system does not have. The choice is substantive: it can change the emergent outcome.
#card/computational-modelling-and-simulation #card/week-01

What distinguishes a simulation from a model, and why does that distinction make simulation the method for studying complex systems?
?
A model is a purposeful representation; a **simulation adds time** — it is an approximate imitation of the system's *operation*, its behaviour as it evolves step by step, usually as a computational implementation of a model. That matters because emergent properties are discovered by *running* the model rather than by inspecting its code: if system behaviour were a simple sum of component behaviour you could compute it directly, and no simulation would be needed.
#card/computational-modelling-and-simulation #card/week-01

Your ABM's output curve doesn't match the historical data point-for-point. Under pattern-oriented modelling, when is this a real problem and when is it not?
?
It is not a problem if the model reproduces the right *patterns* — cycles where the data shows cycles, spikes where it shows spikes, thresholds where it shows thresholds. Exact numerical agreement is neither achievable nor the target for a stochastic system, and tuning until the curve matches encourages overfitting: a model that reproduces one dataset and explains nothing. It *is* a problem if a pattern known to exist fails to appear, which points at a mechanism that is missing, wrong, or uncontrolled.
#card/computational-modelling-and-simulation #card/week-01

## Failure-Mode

A student models truffle foraging with a greedy search: on finding a target, search intensively nearby. Why does this strategy fail here, and what does the failure show about research questions?
?
Greedy search exploits spatial correlation — it only works if targets are **clustered**. Truffles grow underground and do not cluster, so intensive local search after a find is wasted effort. The failure shows that narrowing "mushrooms" to "truffles" did real design work: it invalidated a whole class of strategies and forced a smell-based [[agent-sensing]] mechanism with an explicit detection radius. A vaguer question would not have constrained the design at all.
#card/computational-modelling-and-simulation #card/week-01

You run your ABM once at 70% compliance and once at 80%, see different outcomes, and report a tipping point between them. What is wrong with this?
?
ABMs are stochastic by construction — initial placement, activation order and agent choices are randomised — so a single run is one draw from a distribution, not *the* outcome. A difference between two single runs is not yet evidence of a threshold; it may be run-to-run noise. The claim requires **replication** at each setting and reasoning over distributions, plus **sensitivity analysis** to separate genuine parameter effects from noise.
#card/computational-modelling-and-simulation #card/week-01

What goes wrong downstream when the research question is left vague, and why is this the step students most often lose marks on?
?
A vague question leaves no principled basis for inclusion or exclusion, so the model sprawls — there is no way to answer "should this element be in?" because nothing decides it. Almost every downstream decision (scales, entities, which processes matter) traces back to the question, so the damage compounds through the whole cycle. It is named the hardest step, and the one previous cohorts struggled with most.
#card/computational-modelling-and-simulation #card/week-01

## Deck notes

**Coverage.** 16 cards over both Week 1 lectures. The weighting follows what the lectures
treat as load-bearing rather than what is easiest to test: the purposeful-representation
definition, abstraction and Occam's razor, the six-step cycle, and the truffle exercise as
the worked demonstration that question specificity constrains design.

**Design choices.** No definition-only cards — "what is a model?" is recast as *why* purpose
belongs in the definition, and model-versus-simulation is posed as a contrast so the
time/dynamics distinction has to be produced rather than recognised. The Earth cut-away,
geocentric/heliocentric and truffle cards all embed a concrete situation before asking for
the cause, so the answer is a judgement rather than a recalled sentence.

**Excluded deliberately.** Subject administration (assessment weights, GenAI policy, staff),
the history-of-ABM timeline, and the application-domain lists — recognition material that
inflates a deck without building understanding. Also excluded: [[netlogo]] and [[mesa]] tool
details, which are better learned by use than by recall.

**Deferred.** [[pattern-oriented-modelling]], [[optimisation]] and [[model-communication]] are
named in Week 1 but developed in weeks 4–12; they get one card each here, at Week 1 depth
only, and should be re-carded when the later material lands.

**Suggested starting interval.** 1–3 days, in whichever tool you review in.
