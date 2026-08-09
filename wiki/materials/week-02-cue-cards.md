#flashcards/week-02

# Week 2 Cue Cards

Cards drawn from [[w02a-describing-models]] and [[w02b-modelling-disease-spread]] — the ODD
protocol as a description standard, and the SIR model as the worked example of starting
simple and extending.

## Elaborative Interrogation

Your agent-based model is fully implemented, documented in comments, and the repository is public. Why is publishing the code not a substitute for writing an ODD description?

?
The audience for a model is usually multidisciplinary and non-programming — epidemiologists, ecologists, clinicians — so Python transfers no understanding to them. Code is also long and its meaning is entangled with coding style, whereas a plain-language description states the design at the level at which it can be criticised. See [[odd-protocol]] and [[model-communication]].
#card/cmas #card/week-02

The reproducibility crisis in medicine is usually framed as a problem of results not holding up. What does the ODD protocol's motivation say the underlying failure actually was?

?
The failures came from gaps in the *description of the process*, not from results being unavailable. If the design, assumptions and data that produced an outcome are not written down, nobody can rebuild the study to check it, so a standardised description is a direct remedy rather than a documentation nicety. See [[reproducibility]].
#card/cmas #card/week-02

Why is the ODD Purpose section described as the filter for everything else in the model, rather than just an introductory paragraph?

?
Purpose answers two separate questions — what the model is *of* and what it is *for* — and inclusion decisions follow from the second. A foraging model only needs soil moisture if the purpose makes moisture relevant. Without a purpose statement there is no criterion for what to leave out, and the model accumulates elements indefinitely (scope creep).
#card/cmas #card/week-02

The supplied Assignment 1 scaffolding distributes agents uniformly across an unstructured space. Why that distribution specifically?

?
A uniform distribution introduces no positional bias — every position is equally probable — so it functions as a [[null-model]] baseline. Any spatial pattern in the results is then attributable to the transmission mechanism rather than to structure smuggled in through the initial layout. Starting from a single infected agent has the analogous justification: outbreaks begin with a patient zero, not a cluster.
#card/cmas #card/week-02

Why does modelling disease spread require a simulation at all, rather than observation of real outbreaks?

?
The controlled experiment — deliberately infecting people to observe what happens — is unethical, and waiting for real outbreaks is slow and yields a single realised scenario rather than a comparison across policies. A model supplies the counterfactual: what *would* have happened under a different intervention.
#card/cmas #card/week-02

Both the mathematical SIR model and the agent-based SIR model use the same $S \to I \to R$ diagram. Why is that reuse a reinterpretation rather than the same thing?

?
In the original compartmental formulation the boxes hold *fractions of a population* with flows between them, so the diagram describes aggregate stocks. In the agent-based version the same diagram describes one individual's state sequence over time. See [[compartmental-model]] and [[compartmental-vs-agent-based]].
#card/cmas #card/week-02

## Mechanism

What are the seven sections of the ODD protocol, in order, and what does each contain?

?
**Overview:** (1) Purpose — what the model is of and for; (2) Entities, state variables and scales — agents and environment, their attributes, temporal and spatial [[model-scales]]; (3) Process overview and scheduling — behaviours, resulting state changes, and the ordered sequence of actions ([[scheduling]]).
**Design concepts:** (4) the ten-item checklist — basic principles, emergence, adaptation, objectives, learning/prediction, sensing, interaction, stochasticity, collectives, observation.
**Details:** (5) Initialisation — state at $t = 0$; (6) Input data — external series driving the run; (7) Submodels — equations, rules or algorithms too detailed to state inline.
#card/cmas #card/week-02

Starting from a population of $N$ agents and ending when the outbreak stops, what does the lecture's SIR implementation do on each simulated day?

?
1. For each susceptible agent $X$ and each infectious agent $Y$ it contacts, draw $n \sim U(0,1)$; if $n < q$ then $X$ becomes infected.
2. For each infectious agent $Y$, draw $n$; if $n < \gamma$ then $Y$ recovers.
3. Apply all these transitions on the *following* day, not immediately.
4. If no infectious agents remain, stop; otherwise advance a day.
#card/cmas #card/week-02

How do you decide the temporal resolution of an agent-based model, and what makes one-second steps wrong for an afternoon foraging excursion?

?
Resolution is set against how far an agent displaces per step relative to the size of the modelled space. In one second a forager cannot move meaningfully across the map, so almost every step is a no-op and the simulation costs compute without producing dynamics. The choice is constrained by agent movement and map size, not free.
#card/cmas #card/week-02

## Contrast

What is the difference between the temporal *extent* and the temporal *resolution* of a model, and why does ODD require both?

?
Extent is how long the model runs — a week of chaos versus years of adaptation in the zombie exercise. Resolution is the size of a time step, or whether time is continuous at all. They are set by different considerations: extent follows from the purpose, resolution from agent displacement and space size. Stating one without the other leaves the model unreproducible.
#card/cmas #card/week-02

SARS in 2003 and COVID-19 in 2020 were both respiratory outbreaks with international spread. What did their case curves look like, and what question did that contrast pose for modellers?

?
The SARS cumulative curve rose and then flattened after intervention around May 2003, with cases contained to the thousands in Hong Kong and Southeast Asia. COVID-19 grew exponentially instead ([[exponential-growth]]) and became endemic rather than eliminated. The open question for the 2020 modellers was what the 2003 response did differently, and it directly motivated the Australian ABM work at the [[doherty-institute]].
#card/cmas #card/week-02

## Failure-Mode

In the SIR implementation, agents are processed sequentially within a day. What goes wrong if an infection is applied to the agent's state immediately instead of on the next day?

?
Agents visited later in the sweep are evaluated against a population containing agents infected earlier in the same day, so more infections occur per step than the rules specify, and how many depends on the visiting order. This is a race condition in miniature. The fix is a synchronous update: compute all transitions against the state at the start of the step and apply them together. Deferring recovery has the mirror justification — applying it immediately would remove infectious agents before others were exposed to them.
#card/cmas #card/week-02

The everybody-meets-everybody contact assumption is defensible for the lecture's $N = 10$ population. What breaks when the same assumption is carried to a five-million-agent Melbourne?

?
With $q = 0.2$ and universal mixing, roughly a million agents are infected on day one, which is not an epidemic curve at all. The standard alternative is that a person meets a roughly fixed number $c$ of others per day regardless of population size, so local contact structure has to be introduced as $N$ grows. See [[contact-rate]].
#card/cmas #card/week-02

A student defends $q = 0.2$ on the grounds that it produces a realistic-looking epidemic curve. Why is that argument insufficient?

?
Parameter plausibility depends on the contact structure the parameter operates within, not only on the dynamics it produces. A per-contact infection probability of $0.2$ means something very different at 5 contacts per day than at 100 — at 100 it implies super-spreader behaviour. Parameters have to be assessed against the model setup as well as against the target dynamics.
#card/cmas #card/week-02

The basic SIR model assumes recovery is permanent. Which phenomena does that assumption, plus the three-state space, make impossible to represent?

?
No path from $R$ back to $S$ rules out waning immunity and reinfection. Three states are also too coarse for asymptomatic carriers or severity gradations, and there is no death state, so everyone recovers. Naming these gaps is the intended route to an Assignment 1 research question ([[model-extension]]).
#card/cmas #card/week-02

Two teams implement the same written model specification and get different epidemic curves, with identical rules and parameters. What is the most likely cause, and what does it imply about model documentation?

?
Different update schedules — one applies state changes in place, the other defers them to the end of the step. Because scheduling changes results without changing any rule or parameter, the schedule is part of the model rather than an implementation detail, which is why ODD requires it to be stated explicitly. See [[scheduling]].
#card/cmas #card/week-02

## Deck notes

**Coverage.** 16 cards over both Week 2 lectures. The split follows what the lectures treat
as load-bearing: ODD as a description standard and its motivations on the 2a side, and on
the 2b side the SIR mechanics plus the three assumptions that are most likely to be
misapplied — deferred update, universal mixing, and permanent immunity.

**Design choices.** The seven ODD sections get one full mechanism card rather than seven
recognition cards, since the sections are only useful as an ordered whole. The failure-mode
section carries the most weight because Week 2b is essentially an extended critique: the
race condition, the contact-rate scale break and the parameter-plausibility argument are all
posed as "what breaks", which is how they were taught.

**Excluded deliberately.** Assignment 1 administration (word count, template, marking
weights, GenAI policy) and the pandemic history figures — the Black Death and 1918 death
tolls are motivation, not examinable mechanism. The list of factors making epidemic dynamics
complex is also excluded as recognition material.

**Deferred.** The ten ODD design concepts are named here but unpacked in later lectures.
[[emergence]], [[agent-sensing]] and [[stochasticity]] get no Week 2 card of their own and
should be carded when their own lectures land. The zombie exercise is captured in
[[zombie-apocalypse-model-design]] rather than as cards, since it is a worked artifact
rather than recall material.

**Suggested starting interval.** 1–3 days, in whichever tool you review in.
