---
title: "Week 3a — Analysing Models"
type: material
source: [[sources/w03a-analysing-models]]
date: 2026-08-16
tags: [comp90083, week-03, digest, model-analysis, summary-statistics, stochasticity]
status: complete
---

# Week 3a — Analysing Models

> [!abstract] Orientation — read this first (~1 min)
> **The problem this lecture solves.** You can build a model and run it, but you have no
> principled way to get from "here are ten thousand simulation runs" to "here is what the
> model says". This lecture gives you the two halves of that: a purpose to analyse against
> (science or policy), and a discipline for compressing stochastic output into numbers that
> are actually true of the model.
>
> **Core claims**
> 1. Analysing a model means two things at once — establishing that it behaves correctly,
>    and using it on the problem it was built for.
> 2. Simulation is worth the trouble because real-world data collection is often costly,
>    slow, unethical or impossible, not because simulation is intrinsically superior.
> 3. Moving from playing with a model to experimenting on it requires stating what you want
>    to know *before* you touch a parameter.
> 4. Models used for science test whether hypothesised individual behaviours reproduce an
>    observed population-level pattern; models used for policy assume validation is done and
>    project the effects of candidate interventions.
> 5. Schelling's segregation model shows that a 30% same-type preference produces
>    neighbourhoods around 73% homogeneous — the aggregate pattern greatly exceeds the
>    individual rule that generates it.
> 6. Above roughly a 70% similarity threshold the same model stops converging altogether,
>    which is a qualitative change in behaviour rather than more of the same.
> 7. An ABM produces far more output than can be interpreted, so you must choose summary
>    measures, and for an outbreak those are final size, peak size and peak timing.
> 8. Repeated runs of an identical stochastic SIR configuration produce a **bimodal**
>    distribution of outcomes, and its mean describes no run that ever occurred.
>
> **Prerequisites.** [[sir-model]], [[stochasticity]], [[modelling-cycle]],
> [[agent-based-model]].
> **Where it sits.** Follows [[w02b-modelling-disease-spread]], which built the SIR model;
> this lecture analyses it rather than constructing it. Sets up
> [[w03b-reproduction-number]], which supplies the threshold quantity explaining why so many
> runs produce no outbreak. This is the last week of general modelling material before the
> subject moves to specific model families in Week 6.
> **Sources.** Deck (19 slides) + recording · **digest read time ~14 min**

> [!warning] A note on anchors
> The supplied transcript carries no time markers and the source page holds a Canvas course
> link rather than a recording URL, so sections below are anchored by slide number and by
> position in the lecture, not by timestamp. Every claim is traceable to a slide; the
> transcript-only material is marked but cannot be linked to a moment in the recording.

---

## The Spine

### Where this sits in the modelling cycle
`slides 2–3` · opening, after admin

The lecture opens on the [[modelling-cycle]] diagram that has run through the subject since
Week 1: formulate the question, assemble hypotheses, choose model structure, implement the
model, analyse the model, communicate the model. "Patterns!" is marked at two transitions —
entering the choice of structure, and leaving analysis for communication
([[pattern-oriented-modelling]]).

The lecturer's gloss on the diagram is the part worth keeping. It is not a fixed circuit
run once from start to end. At each point you may decide to go back and revise any earlier
element: the question may turn out not to be clear, the hypotheses may not be clear, the
implementation may reveal that something essential was omitted. The loop is a default
ordering, not a constraint.

The three stated objectives for the week:

1. Describe how models are used in the context of science and policy.
2. Design and apply appropriate summary measures of model behaviour.
3. Explain the significance of the reproduction number in infectious disease dynamics.

Objective 3 is discharged in [[w03b-reproduction-number]], not here.

> [!mic] Not on the slides — ODD recap questions
> The lecture opened with poll questions on the [[odd-protocol]] from Week 2, and the
> lecturer's answers correct a common misreading.
>
> **Which stage of the modelling cycle is ODD most useful at?** Most of the class answered
> "formulating the question". The lecturer disagreed: formulating the question and
> assembling hypotheses come *before* you start writing an ODD, because you need to know
> what you are going to build first. ODD is most useful when **choosing the model
> structure** (you are deciding on all the components), when **implementing** (it is the
> roadmap — "we have all the specifications and we are going to implement it"), and when
> **communicating** (it is the plain-language description you hand to someone else).
>
> **Which ODD section holds the description and justification of a specific process?**
> Either *process overview and scheduling* or *submodels*, and the difference is the amount
> of detail. Simple behaviour describable in a few lines goes in process overview and
> scheduling. Something more complicated — the lecturer's example was a machine learning
> model embedded in each agent — goes in a submodel.
>
> **Why not in entities, state variables and scales?** Because ODD is always a
> plain-language description, so it would not hold a code-level description. What that
> section *does* hold is the agent structure and the environment, including the environment's
> own state variables.
>
> **Design concepts** covers things like learning, optimisation and communication — the
> material the subject turns to from Week 6 onward.

### What it means to analyse a model
`slide 4` · early

Two activities, stated on the slide:

- Studying the model to understand how it behaves, ensure it is **correct**, and perhaps
  improve its performance.
- Using it to solve the problem it was designed to explain.

The lecturer expanded both. Is the model representing the real-world system we are trying
to abstract, and is it abstracting it in enough detail? Perhaps we want to tune it so the
target patterns can be reproduced. And separately: is it fit for purpose? "We don't just
want to build models to play with them even though right now this is what we have been
doing — we want models to solve an actual real world problem."

The slide's justification for simulating at all is about access to data. When we study
systems in the real world we are limited to the data we can collect, and obtaining
additional data may be costly, time-consuming, unethical or simply impossible. With a
simulation model we have much more freedom to manipulate the system and to collect any data,
and as much of it as we like.

> [!mic] Not on the slides — why data is expensive
> The lecturer grounded "costly" in research practice rather than leaving it abstract.
> Flyers around campus recruiting survey volunteers are usually PhD students collecting data
> for their projects, offering $10–20 as a token; a marketing research panel company might
> pay $100 for the same survey, because participants' time and effort cost money. And for
> field science the cost is logistical: studying bats in China, ants in the Amazon or
> spiders in Australia means travelling to where the animals are, with trips, food and
> equipment to fund.
>
> His framing: "even though data can be cheap to collect in certain areas, it might be
> costly in others." The case for simulation is contingent on which area you are in, not
> universal.

### From playing to controlled experiments
`slide 5` · early-middle

Up to this point the subject has engaged with models by **playing** with them: running them
to see what happens when parameter values, initial conditions and so on are varied. The
slide poses the two questions that mark the transition to experiment:

1. What do I want to know about the model's behaviour?
2. How can I design experiments to learn what I want to know?

The order matters. Both questions are asked before anything is varied. The lecturer
described the undisciplined version as "a fishing experiment — you just move knobs around
and see what happens", and contrasted it with a structured protocol producing results that
mean something.

What gets varied: parameter values, initial conditions, random seeds, and other elements of
the model. How it gets varied is the substance of the discipline — "it's not just I move
this value in this direction, it's more of a systematic process of starting with a seed
value and then making maybe a couple of variations either up or down to understand how the
system is changing based on that value."

This is [[model-analysis]] as a designed activity rather than an exploratory one, and it is
what [[reproducibility]] requires: a stochastic result is reproducible only with the seed or
with enough replicates.

### Modelling for science
`slides 6–7` · middle

Using models for scientific purposes follows the inductive approach, six steps as stated on
the slide:

1. **Observe** — what don't we understand?
2. **Question** — often beginning "why?" or "how?"
3. **Hypothesise** — alternative answers to our question.
4. **Predict** — what predictions does each hypothesis make?
5. **Test** — evaluate our predictions.
6. **Analyse and conclude** — or repeat steps 1 to 5.

The agent-based specialisation is on the same slide and is the load-bearing sentence: *we
pose hypotheses in the form of individual-level behaviours that can explain population-level
phenomena, then implement these hypotheses as ABMs and evaluate their ability to reproduce
observed patterns of behaviour.* Step 3 is where an ABM differs from any other modelling
approach — the hypothesis is a rule about what individuals do, not a claim about aggregates
([[emergence]]).

> [!example] Worked example — the Schelling segregation model through all six steps
> Reproduced as the slide states it, with the lecturer's live demonstration results.
>
> | Step | Content |
> |---|---|
> | **Observe** | Residential segregation occurs, even among populations who profess not to discriminate. |
> | **Question** | How do we explain this? |
> | **Hypothesise** | Even mild individual preferences regarding their neighbourhood may lead to population-level segregation (Schelling's model). |
> | **Predict** | Mild preferences will lead to increasingly homogeneous neighbourhoods. |
> | **Test** | Run scenarios, varying the strength of preference and measuring homogeneity. |
> | **Conclude** | The hypothesis is plausible. |
>
> **The model.** A grid representing a geographical area. Each occupied cell holds a
> household of one of two types; white cells are vacancies. One parameter: a similarity
> threshold, the percentage of same-type neighbours a household requires to be content.
> Discontented households move to a vacant cell — which is why vacancies are necessary for
> the model to run at all. Reported outputs are the percentage of unhappy agents and the
> average percentage of similar neighbours.
>
> **Run 1, threshold 30%.** Starts completely random. Converges quickly. Unhappiness falls
> to zero. A student observed the average similarity settling around 73%, well above the
> 30% anyone demanded, and the lecturer confirmed: "73% similar even if my threshold is
> really low — actually they end up very concentrated." Clearly defined clusters are visible.
>
> **Run 2, threshold 90%.** The lecturer's framing: "let's make it very aggressive — my
> hypothesis is if I become a bigot, this is going to become very messy." A student predicted
> it would simply take longer to converge. It does not converge. The system never settles,
> because too few households can be satisfied simultaneously.
>
> **Where it breaks.** Asked where convergence would return, students guessed 50–60%. The
> lecturer's answer: "it's somewhere around 70 that it just converges." Below that threshold
> the system settles into segregated clusters; above it, nothing settles.
>
> **The conclusion.** You don't need much to produce this kind of separation. A little is
> enough, and it results in households splitting by whatever characteristic the similarity
> metric compresses — socioeconomic, cultural, or anything else. The model does not commit
> to which; it compresses all of it into one number, "how similar is the neighbour to me".

The epistemic status of "plausible" deserves attention. Reproducing the pattern establishes
that the hypothesised mechanism is *sufficient* to generate it. It does not establish that
this is the mechanism actually operating in the real world. That is the standard limit of
generative explanation, and it is why the cycle loops rather than terminating.

Note also what the science framing does *not* do: "in here, we are not trying to modify what
the system is trying to do. We are just trying to understand it."

### Modelling for policy
`slides 8–9` · middle

Models used for policy have typically already been validated, and are now being used to
inform decision-making. Six steps, as stated:

1. **Problem** — engage with the decision-maker to identify the problem.
2. **Objectives** — identify the management objectives.
3. **Interventions** — define the actions that can be taken.
4. **Projections** — evaluate the impact of interventions on objectives.
5. **Decision analysis** — evaluate relative merit of interventions.
6. **Implementation** — put the intervention into practice.

The model enters at step 4 and nowhere else. The slide is explicit that projections may lead
to revision of objectives, or to consideration of alternative interventions, and that data
collected after implementation feeds back to improve future projections.

Two steps carry the difficulty. **Interventions** means enumerating the available levers;
the class recalled lockdowns, vaccines, mask mandates, social distancing, quarantines and
airport closures, and the lecturer's framing was to "imagine that we have a lever for each
one of them" and test them individually or in combination
([[epidemic-intervention]]). **Objectives** means naming metrics of success, and the class
proposed reduced case numbers, lower mortality and minimised economic impact.

> [!mic] Not on the slides — objectives you cannot measure
> The lecturer pushed on the ethics dimension and it is the sharpest point in this section.
> Some people opposed lockdowns because of the impact on their freedom. Is that a legitimate
> measure of success? "Those are harder to measure... maybe that's a bit harder to measure
> with hard numbers, but that can be a measure of success somehow if you can measure it and
> you can quantify it."
>
> The consequence he drew: "whether that you mould into your system or not is also defines
> whether you will be able to track it." A consideration that is not represented in the model
> cannot be projected, so the choice of objectives silently bounds what the analysis is
> capable of saying. This is a modelling decision that looks like a scoping decision.

> [!example] Worked example — the influenza antiviral stockpile study
> The policy pipeline applied to a real Australian decision. Reproduced as the slide states
> it.
>
> **Problem.** Reduce the impact of a pandemic, given a limited stockpile of antiviral drugs.
>
> **Objectives.** Delay the peak of the outbreak, and minimise the number of infections.
>
> **Interventions.** Use the drugs for prophylaxis (protection) or for treatment.
>
> **Projections.** Model projections of outbreaks run for different epidemiological scenarios
> and interventions. Presented as response surfaces — number of infections plotted against
> time and a second varied parameter, for each intervention setting.
>
> **Analysis.** Treatment alone is insufficient to delay the peak or reduce the number of
> infections, across a range of outbreak scenarios.
>
> **Implementation.** Implemented in the pandemic plan.
>
> The lecturer's expansion on the objective: the aim was to "delay as much as possible the
> impact or the peak of the infection such that at some point we can have some vaccines," and
> the question behind it was whether drugs alone could substitute for harsher measures — "just
> try not to make more harsh mandates, avoid the lockdowns or avoid the social distancing, but
> can we just use the drugs to do that?" The finding was that it "did help to kind of move a
> little bit the peak around but it didn't just completely disappear," so the decision was not
> to rely on treatment alone.
>
> **Why this example is here.** A negative result changed policy. Establishing that an
> intervention does not achieve the objectives is a usable conclusion, because policy
> modelling is a comparison between actions rather than a prediction of one.

> [!mic] Not on the slides — the handoff problem
> The lecturer's aside on implementation is worth recording verbatim in substance: the
> politician "is gonna come out and say, OK, we are going to do a mass mandate because the
> model tells us. And then they are gonna wash their hands and they say, oh we follow
> science."
>
> His actual position is more careful than the cynicism suggests: "it's hard when you do some
> policy decisions because there is no way to measure everything that you can have, but at
> least you have a reasoning of why you should do it." The model supplies projections under
> assumptions. It does not supply the value judgements encoded in the objectives, and
> presenting it as though it does misrepresents what was computed.

### Statistical analysis of simulation models
`slide 10` · middle-late

Four activities, stated as a bare list on the slide:

1. Quantifying simulation outputs in terms of summary statistics.
2. Using these summary statistics to compare alternative simulation scenarios.
3. Quantifying relationships between model parameters and summary statistics.
4. Comparing these summary statistics to observed data.

Activity 4 is the constraint that ties back to [[pattern-oriented-modelling]]: a summary
statistic is only usable for validation if the real world also reports something comparable.

### Choosing what to record
`slide 11` · middle-late

Agent-based models can generate a vast amount of output if we record the trajectory of every
agent and environment state variable over the duration of a simulation. More often we choose
some observation(s) of interest to record, and what we choose depends on the question or
problem we are interested in ([[research-question]]).

The lecturer's arithmetic makes the scale concrete: 100 agents, over 100 steps, over 100
simulations, over 100 different scenarios — "so quickly we have way too many data points."
That is $10^8$ observations before anyone has asked a question of them.

The slide then defines the parameter used for the rest of the lecture:

$$\beta = (\text{average contacts per person per unit time}) \times q$$

where $q$ is the probability of disease transmission in a contact. This is the **effective
contact rate**, and it is a different quantity from the per-contact probability $q$ used in
the Week 2 agent-based implementation. Keep them separate ([[contact-rate]]).

### A single run, and then many
`slides 12–13` · late

Baseline configuration: $N = 10{,}000$, $\beta = 2.5$, $\gamma = 0.4$. (These give
$R_0 = \beta/\gamma = 6.25$, though the lecture does not name $R_0$ until Thursday.)

**Slide 12 — one run.** The number infectious over 100 time steps: a jagged trajectory rising
slowly through the first 25 steps, climbing steeply from around step 30, peaking near 440
around step 55, then declining with a long noisy tail. The slide's caption is the point:
"But this is just one possible model outcome."

**Slide 13 — many runs.** Roughly twenty overlaid trajectories at identical settings. The
slide's framing: "In the real world, only one possible future will come to pass. Stochastic
models can help us to estimate what the most likely sequence of future events might be."

What varies across the runs, as elicited from the class: the timing of the peak, the height
of the peak, the skew (some are fatter earlier), and the width. Peaks range from roughly 400
to 620 and occur anywhere from step 35 to step 95.

> [!mic] Not on the slides — the flat line at zero
> This is the most important exchange in the lecture and it is entirely transcript-only. The
> lecturer asked repeatedly whether anyone noticed anything about the zero axis. A student
> eventually spotted a curve with no infections — "there is a straight line, right?" — and
> when asked whether that outcome was common, answered "no."
>
> The lecturer's response: "you will be surprised." The flat line is not an outlier. It is
> the single most common outcome at these settings, and it is invisible in the overlay plot
> because all such runs sit on top of each other along the axis. The histograms on the next
> three slides exist to make it visible.
>
> This is a lesson about plot choice as much as about epidemics: a trajectory overlay hides
> exactly the mode that a histogram reveals.

### Summarising an outbreak
`slide 14` · late

Three observations of interest, stated on the slide with their decision-relevance
([[outbreak-summary-measures]]):

- **Final size** — the number of people infected by the end of the outbreak.
- **Peak size** — the number infected at the height of the outbreak, which tells us how much
  demand there may be on the health system.
- **Peak timing** — the time at which the peak occurs, which tells us how much time we have
  to prepare for this period of peak demand.

Each maps to a decision someone has to make. That correspondence is the test of a good
summary measure.

The slide then proposes the obvious approach and immediately undercuts it: "One intuitive
approach could be to measure the average (mean or median) of these values across multiple
runs. However, this could be misleading..."

### The three distributions
`slides 15–17` · late

> [!example] Worked example — reading the three histograms
> All at $N = 10{,}000$, $\beta = 2.5$, $\gamma = 0.4$, across many replicates. Reproduced
> in full because the shapes are the content.
>
> **Slide 15 — final size.** Horizontal axis: total number infected, 0 to 6,000. Two features
> and nothing between them. A spike at approximately zero holding about **45%** of
> simulations, with a small adjacent bar around 1%. Then an empty range across most of the
> axis. Then a roughly normal cluster from about 4,500 to 5,800, centred near **5,200**, with
> a peak density around 6%.
>
> **Slide 16 — peak size.** Horizontal axis: size of peak, 0 to ~700. The same structure. A
> spike at zero holding about 37%, a second bar near 10% just above it, then an empty range,
> then a broad cluster from roughly 300 to 680 centred near **500**.
>
> **Slide 17 — peak timing.** Horizontal axis: time of peak, 0 to ~110. Bimodal again but
> much noisier. A sharp early spike at $t \approx 1$–3 reaching 12% density and decaying fast
> through $t \approx 10$ — these are the failed outbreaks, whose "peak" is the first step or
> two before extinction. Then a broad, ragged mode from about $t = 30$ to $t = 70$ centred
> near **$t = 45$**, with a scattering of late outliers past $t = 90$.
>
> **Why the mean fails.** Asked where the mean of the final-size distribution would fall, the
> class identified the problem immediately. The lecturer: "if I take the mean, it's gonna be
> around 3000 infected and it just tells us nothing."
>
> **The honest summary.** "About 50% of the cases there is almost no outbreak, but in those
> outbreaks that it happens, the total number of infected is gonna be around 5000" — so with
> 10,000 agents, "in about 50% of the cases, you get about half of the people infected."
> Two numbers and a probability, not one number.

The mechanism producing this shape is [[stochastic-fadeout]]: early in an outbreak the
infectious pool is tiny, so the realised number of onward infections is a small sample from a
distribution whose mean is $R_0$, and small samples can come out at zero. If the first case
recovers before infecting anyone, the chain terminates regardless of how transmissible the
disease is in aggregate. [[w03b-reproduction-number]] supplies the quantity that makes this
precise.

Note that the median is no better here. It depends entirely on which side of 50% the fadeout
probability sits, so it flips between "almost nobody infected" and "half the population
infected" under small parameter changes.

### Scaling the population
`slide 18` · late

Same parameters, $N = 1{,}000{,}000$. Hundreds of overlaid trajectories. The slide asks:
what is predictable across each of these outbreaks? What remains variable? Why is this?

What changes: the trajectories become smooth rather than jagged, and the peak height becomes
highly predictable, clustering tightly just below 50,000 infectious (about 4.8% of the
population, consistent with the 5.2% final-size mode scaled up).

What does not change: the timing still varies substantially, with peaks spread from roughly
$t = 60$ to past $t = 120$. And — the lecturer pressed the class on this — the flat line at
zero is still there. "It doesn't matter the size of the population, there is still a
probability that it doesn't go well."

> [!mic] Not on the slides — why population size doesn't fix it
> The lecturer's phrasing was that with a million agents the curves "are smoother, but they
> go all the way" to the same peak. The reasoning to hold onto: population size damps
> variability *within* an established outbreak, because the law of large numbers applies once
> the infectious pool is large. It does nothing to the first few generations, which involve a
> handful of individuals whatever $N$ is. Fadeout is decided before population size becomes
> relevant.

### Summary
`slide 19` · close

Three statements, as given:

- We analyse models to understand how they behave, ensure they are correct, and use them to
  solve a problem.
- Models can produce vast amounts of information, but some might not be relevant to answer
  our question. Instead, we focus on summary statistics that represent elements of interest.
- Care must be taken when selecting summaries, as these may lead us into incorrect
  conclusions.

The lecturer's stated takeaway, which is slightly stronger than the slide: once we have
determined which data points we are interested in, do **not** blindly compress them — try to
represent them and understand the implications of what we are observing.

---

## Recall Layer

> [!question]- A colleague says their agent-based model is "validated" because it runs without
> errors and produces plausible-looking curves. What two distinct activities has analysis been
> collapsed into one of, and why does the distinction matter?
> Analysis is both establishing that the model behaves correctly and is an adequate
> abstraction, *and* using it on the problem it was built for. Running without errors
> addresses neither: it is a claim about the implementation, not about the abstraction or the
> application. A model can be internally correct and still fail to reproduce the pattern it
> was built to explain, and it can do both and still be useless for the decision at hand.
> `slide 4`

> [!question]- Why is "we simulate because simulation is more rigorous than observation" a
> misstatement of the lecture's argument?
> The argument is about access, not rigour. Real-world study is limited to collectable data,
> and collecting more may be costly, slow, unethical or impossible — paying survey
> participants, funding fieldwork, or deliberately infecting people. Simulation buys freedom
> to manipulate and to sample without limit. Where data is cheap and ethical to collect the
> argument weakens correspondingly, so it is a contingent case rather than a general claim
> about method. `slide 4`

> [!question]- What has to happen before you touch a parameter, and what distinguishes an
> experiment from playing?
> Two questions get answered first: what do I want to know about the model's behaviour, and
> how can I design experiments to learn it. The distinguishing feature is systematicity —
> starting from a baseline seed value and making structured variations up and down, across
> parameters, initial conditions and random seeds — rather than moving knobs opportunistically
> to see what happens. `slide 5`

> [!question]- In an agent-based study, what form does a scientific hypothesis take, and what
> counts as testing it?
> The hypothesis is a statement about individual-level behaviour — a rule agents follow — not
> a claim about aggregate quantities. Testing it means implementing the rule as an ABM and
> evaluating whether the resulting population-level output reproduces an observed pattern.
> `slide 6`

> [!question]- Schelling's model with a 30% similarity threshold converges to around 73%
> average similarity. Why is that gap the whole point rather than an inconsistency?
> Because it shows the aggregate outcome exceeding, and not merely reflecting, the individual
> rule that generates it. Nobody in the model wants a 73%-homogeneous neighbourhood; the rule
> only says "move if fewer than 30% of my neighbours are like me". Segregation of that
> strength emerges from mild preferences without any agent holding a preference for
> segregation, which is exactly the claim about [[emergence]] the model exists to demonstrate.
> `slide 7`

> [!question]- Raising Schelling's threshold from 30% to 90% does not produce stronger
> segregation. What does it produce, and what general phenomenon is this an instance of?
> The model stops converging at all — too few households can be satisfied simultaneously for
> the system to settle, so agents keep moving indefinitely. Convergence breaks down somewhere
> around a 70% threshold. This is a [[tipping-point]] or critical point: the qualitative
> behaviour of the system changes either side of a parameter value rather than degrading
> smoothly. [[w03b-reproduction-number]] gives the epidemic instance at $R = 1$. `slide 7`

> [!question]- Both the science and policy pipelines have six steps. At which step does the
> model actually get used in the policy pipeline, and what follows from that being the only
> one?
> Step 4, projections. Objectives and the candidate intervention set come from engagement
> with decision-makers, not from the model, and the decision analysis weighs merits against
> objectives the model did not choose. It follows that the model cannot supply the value
> judgements — a claim of "we followed the science" conflates a projection under assumptions
> with a decision about what to optimise. `slide 8`

> [!question]- Why does the choice of policy objectives bound what the analysis can conclude,
> before any modelling happens?
> Because an objective that cannot be measured cannot be projected. The COVID-19 discussion
> raised acceptability and restrictions on freedom as genuine success criteria that resist
> quantification. If they are not represented in the model they are absent from every
> projection it produces, so the objective list silently determines the analysis's scope.
> `slide 8`

> [!question]- The antiviral stockpile study concluded that treatment alone was insufficient.
> Why is a negative result useful here in a way it might not be in a scientific study?
> Policy modelling is a comparison between available actions, so eliminating one narrows the
> decision. The finding changed what the Australian pandemic plan relied on. A scientific
> negative result is also informative — the mechanism is insufficient to generate the pattern
> — but it does not by itself tell you what to do instead, whereas ruling out an intervention
> directly advances a choice among a known set. `slide 9`

> [!question]- Why can't you simply record everything an ABM produces and decide what matters
> later?
> Volume. 100 agents over 100 steps over 100 runs over 100 scenarios is $10^8$ observations,
> which is neither storable at scale nor interpretable. The choice of what to record is
> therefore forced, and it is driven by the question the model was built to answer rather than
> by what is convenient to log. `slide 11`

> [!question]- $\beta$ in this lecture is not the same quantity as $q$ from Week 2. State both
> and say why conflating them causes errors.
> $q$ is the probability of transmission in a single contact between a susceptible and an
> infectious agent. $\beta$ is the average number of contacts per person per unit time
> multiplied by $q$ — an effective contact rate, carrying both behaviour and biology. A
> $q$ value is meaningless without knowing the contact structure it sits in; $q = 0.2$ at 5
> contacts per day and at 100 contacts per day describe wildly different diseases.
> `slide 11`

> [!question]- Name the three standard outbreak summary measures and the decision each one
> informs.
> Final size — total burden, how many people are infected in the end. Peak size — peak demand
> on the health system, how many beds and staff are needed simultaneously. Peak timing — how
> much preparation time is available before that demand arrives. A disease with a modest final
> size can still overwhelm a system by arriving all at once, which is why peak size is
> tracked separately. `slide 14`

> [!question]- The final-size distribution at $N=10{,}000$, $\beta=2.5$, $\gamma=0.4$ has a
> mean near 3,000. Why is reporting that number worse than reporting nothing?
> Because it is confidently wrong rather than merely imprecise. The distribution is bimodal:
> about 45% of runs near zero and the rest clustered near 5,200, with almost nothing between.
> A mean of 3,000 points at the empty valley between the modes, implying that a moderate
> outbreak is typical when moderate outbreaks essentially never occur. Someone planning to
> that number prepares for a scenario the model never produced. `slides 15, 14`

> [!question]- What is the correct way to summarise a bimodal outcome distribution?
> As a mixture: the probability of each regime plus a summary within each. "About 45% of the
> time the outbreak fails to establish; otherwise around 5,200 of 10,000 are infected." Note
> that the median is no better than the mean here — it depends on which side of 50% the
> fadeout probability falls, so it flips discontinuously between the two modes under small
> parameter changes. `slide 15`

> [!question]- Going from 10,000 to 1,000,000 agents makes the trajectories smooth and the
> peak height predictable. Why does it not remove the no-outbreak mode?
> Because population size damps variability only *within* an established outbreak, where the
> law of large numbers applies to a large infectious pool. Whether an outbreak establishes at
> all is decided in the first few generations, which involve a handful of infectious
> individuals regardless of $N$. Fadeout is settled before population size becomes relevant.
> `slide 18`

> [!question]- The overlay plot of many trajectories (slide 13) contains the same information
> as the histograms (slides 15–17), yet the class could not see the dominant outcome in it.
> Why?
> Every failed run lies along the zero axis, superimposed on every other failed run, so 45% of
> the data renders as a single flat line indistinguishable from an axis. A histogram bins by
> outcome value and therefore gives that mass its own visible bar. The lesson generalises: an
> overlay plot displays trajectories but not their density, so it systematically hides modes
> that coincide. `slides 13, 15`

> [!failure] Common failure modes
> - **Taking the mean of a bimodal distribution.** The single error this lecture is built
>   around. Always plot the distribution of a summary measure before compressing it; the mean
>   is always computable and always looks like an answer, so nothing in the output signals
>   that the compression was invalid.
> - **Reaching for the median as the fix.** It is not one. Under bimodality the median tracks
>   whichever mode holds more than half the mass and jumps discontinuously when that changes.
> - **Reading a trajectory overlay as if it showed density.** Coincident runs stack invisibly.
>   The 45% fadeout mode is present in slide 13 and effectively unreadable there.
> - **Confusing $\beta$ with $q$.** $\beta$ absorbs the contact rate; $q$ does not. This gets
>   worse in Week 3b, where $\beta$ changes meaning again in the deterministic formulation.
> - **Treating a single run as the model's behaviour.** It is one sample. This was already
>   flagged in Week 2 with the $|I| = 1,1,1,2,3,1,0$ trace, and slide 12 restates it.
> - **Assuming stronger parameters give more of the same behaviour.** Schelling at 90%
>   produces qualitatively different behaviour (non-convergence), not intensified segregation.
> - **Answering "ODD is most useful when formulating the question."** The majority class
>   answer, and the lecturer's stated correction: it is most useful at structure,
>   implementation and communication.
> - **Claiming a mechanism is *the* explanation because the model reproduced the pattern.**
>   Sufficiency is not necessity. "Plausible" is the word the slide uses, and it is doing
>   deliberate work.

> [!exam] Exam surface
> - **Given a described scenario, classify it as science or policy modelling and justify.**
>   The discriminator is whether the study seeks to understand the system or to act on it.
>   Expect a scenario that could plausibly be read either way.
> - **Given a histogram or a description of an output distribution, state why a proposed
>   summary statistic is inappropriate and supply a better one.** This is the most likely
>   quantitative question from this lecture, and the expected answer is the mixture
>   description.
> - **Given a model and a question, propose summary measures and justify them by the decision
>   each informs.** The three outbreak measures are the template; the skill is transferring it
>   to a non-epidemic model.
> - **Explain the Schelling result and what it demonstrates about emergence.** Likely to be
>   paired with a request to identify the tipping point and explain what changes there.
> - **Design an experiment to answer a stated question about a model's behaviour** — naming
>   what is varied, what is held fixed, and how many replicates are needed and why.
> - **Assignment relevance.** The lecturer positioned the whole week as preparation for the
>   assignment, and the marking rubric weights abstraction, question formulation, experiment
>   design and presentation of results over volume of code. Everything in this lecture is
>   directly assessable there.

> [!todo] Open threads
> - **The reproduction number** is named in objective 3 but not defined; deferred entirely to
>   [[w03b-reproduction-number]]. The fadeout phenomenon is demonstrated here without the
>   quantity that explains it.
> - **How many replicates are enough** is never addressed. The lecture shows that replication
>   is necessary and that distributions must be inspected, but gives no criterion for
>   sufficiency. The subject defers sensitivity and uncertainty analysis to weeks 10–12.
> - **The 45% fadeout figure is read off a histogram**, not derived. Whether the subject
>   expects students to be able to compute an extinction probability is unclear; nothing in
>   Week 3 provides the branching-process machinery to do so.
> - **The tipping point in Schelling's model** is asserted at "somewhere around 70" and the
>   lecturer explicitly deferred showing it — "that tipping point I will show it to you in a
>   different lecture." Watch for it later.
> - **Whether the segregation result is robust** to grid size, vacancy density and
>   neighbourhood definition is not examined. The live demo is a single configuration.
> - **The response surfaces on slide 9** are shown without axis labels legible at slide
>   resolution; the specific antiviral study is not cited by name or reference, so the result
>   cannot currently be traced to a paper. See [[influenza-antiviral-stockpile-model]].

---

## Topics covered

- [x] `slide 1` — Title → *(no content)*
- [x] `slide 2` — Modelling cycle diagram, Patterns! at two transitions → [[#Where this sits in the modelling cycle]]
- [x] `slide 3` — Three weekly objectives → [[#Where this sits in the modelling cycle]]
- [x] `slide 4` — What it means to analyse; the data-cost argument → [[#What it means to analyse a model]]
- [x] `slide 5` — From playing to controlled experiments → [[#From playing to controlled experiments]]
- [x] `slide 6` — The inductive approach, six steps; ABM specialisation → [[#Modelling for science]]
- [x] `slide 7` — Segregation model worked through the six steps → [[#Modelling for science]]
- [x] `slide 8` — Policy pipeline, six steps; feedback loops → [[#Modelling for policy]]
- [x] `slide 9` — Influenza antiviral stockpile study → [[#Modelling for policy]]
- [x] `slide 10` — Four purposes of statistical analysis → [[#Statistical analysis of simulation models]]
- [x] `slide 11` — Output volume; definition of $\beta$ → [[#Choosing what to record]]
- [x] `slide 12` — Single stochastic run, $N=10{,}000$ → [[#A single run, and then many]]
- [x] `slide 13` — Many runs overlaid; only one future occurs → [[#A single run, and then many]]
- [x] `slide 14` — Three outbreak observations; the averaging warning → [[#Summarising an outbreak]]
- [x] `slide 15` — Final-size histogram (bimodal) → [[#The three distributions]]
- [x] `slide 16` — Peak-size histogram (bimodal) → [[#The three distributions]]
- [x] `slide 17` — Peak-timing histogram (bimodal, noisy) → [[#The three distributions]]
- [x] `slide 18` — $N = 1{,}000{,}000$; what changes and what doesn't → [[#Scaling the population]]
- [x] `slide 19` — Summary, three statements → [[#Summary]]

Transcript-only material not on any slide, all captured above: the ODD recap questions and
answers, the cost-of-data anecdotes, the unmeasurable-objectives discussion, the
"we-followed-the-science" aside, the zero-axis exchange, and the reasoning on why population
size does not eliminate fadeout.

## Connections

`See also:` [[sources/w03a-analysing-models]] · [[sources/w03b-reproduction-number]] ·
[[w03b-reproduction-number-digest]] · [[model-analysis]] · [[modelling-for-science]] ·
[[modelling-for-policy]] · [[summary-statistic]] · [[outbreak-summary-measures]] ·
[[bimodal-distribution]] · [[stochastic-fadeout]] · [[schelling-segregation-model]] ·
[[influenza-antiviral-stockpile-model]] · [[tipping-point]] · [[stochasticity]] ·
[[sir-model]] · [[modelling-cycle]] · [[compartmental-vs-agent-based]]
