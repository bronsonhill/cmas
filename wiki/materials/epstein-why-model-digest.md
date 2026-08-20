---
title: "Epstein (2008) — Why Model?"
type: material
source: [[sources/epstein-2008-why-model]]
date: 2026-08-20
tags: [comp90083, digest, reading, modelling-philosophy, explanation, prediction]
status: complete
---

# Epstein (2008) — Why Model?

> [!abstract] Orientation — read this first (~1 min)
> **The problem this paper solves.** Someone asks what your model is *for*, or challenges you
> to prove it predicts anything, and the honest answer — "it explains a mechanism" — sounds
> like a dodge. Epstein gives you the argument that it isn't one, and a list of sixteen
> defensible goals to point at.
>
> **Core claims**
> 1. Everyone who ventures a projection about a social dynamic is already running a model;
>    the only choice is whether it is explicit or implicit.
> 2. The demand "validate your model" applies with more force to the implicit model of the
>    person making the demand, who cannot even write theirs down.
> 3. Explicit models can be calibrated, replicated, swept for sensitivities, and used as a
>    focal point for a multidisciplinary team. Implicit ones can do none of this.
> 4. Prediction is one modelling goal among at least seventeen, and Epstein lists sixteen
>    others off the top of his head.
> 5. Explanation does not imply prediction — tectonics explains earthquakes and forecasts
>    none of them.
> 6. Generative explanation is the ABM-specific form: grow the macroscopic regularity from
>    heterogeneous agents following plausible local rules.
> 7. Theory precedes data as often as it follows it; without a model it is not clear what
>    data to collect.
> 8. All the best models are wrong, and are taught anyway, because they capture qualitative
>    behaviours of overarching interest.
>
> **Prerequisites.** [[model]], [[agent-based-model]], [[emergence]], [[abstraction]].
> **Where it sits.** Background reading for [[a1-project-specification]]. It supplies the
> justification layer under the science/policy split taught in [[w03a-analysing-models]], and
> it is the paper to cite when your assignment question explains rather than forecasts.
> **Source.** JASSS 11(4) 12, ~4 pages, 17 numbered paragraphs · **digest read time ~8 min**

---

## The Spine

JASSS numbers every paragraph, so the anchors below are paragraph numbers rather than
timestamps. Section headings are Epstein's own.

### Why model?
`¶1.1–1.7`

Epstein opens by dating the modelling enterprise to Archimedes, and its misunderstanding to
the same moment. The rhetorical question "why model?" usually arrives from someone who
believes they are not modelling. His retort: *you are a modeler*. Anyone who ventures a
projection, or imagines how an epidemic, war, or migration would unfold, is running some
model. It is simply an implicit one — assumptions hidden, internal consistency untested,
logical consequences unknown, relation to data unknown.

That reframes the question. The choice is not whether to build models; it is whether to build
explicit ones. In an explicit model the assumptions are laid out in detail, so you can study
exactly what they entail: on these assumptions, *this* happens; alter them and *that* happens.

The same move disposes of the validation challenge. Asked "can you validate your model?",
the appropriate retort is "can you validate yours?" At least an explicit model can in
principle be calibrated to data — Epstein notes he avoids the word "validate" entirely, being
a good Popperian, since a model that survives testing has not been proven, only not yet
falsified.

Four concrete advantages of explicitness follow, and they are worth holding separately
because they cover different failure modes:

| Advantage | What it buys |
|---|---|
| Calibration to historical cases | A check against data that exists, where it exists |
| Replication | Others can rebuild your result rather than take it on trust ([[reproducibility]]) |
| Rigorous incorporation of domain expertise | Biomedical or ethnographic knowledge enters as explicit structure, not vibes |
| Sensitivity analysis | Sweep a huge parameter range to find salient uncertainties, regions of robustness, and important thresholds ([[sensitivity-analysis]]) |

The last one carries the sharpest line in this section: "I don't see how to do that with an
implicit mental model." A mental model has no parameters to sweep.

Epstein then concedes the point that policy modellers are usually accused of dodging. In the
policy sphere — unlike, he says, particle physics — models do *not* remove the need for
judgment. What they do is reveal tradeoffs, uncertainties and sensitivities, and thereby
**discipline the dialogue** about options, making unavoidable judgments more considered
([[modelling-for-policy]]).

### Can you predict?
`¶1.8`

The second reflexive challenge. The moment you posit a model, prediction — crystal-ball,
tell-me-the-future prediction — is presumed to be the goal.

Epstein's answer is deliberately two-sided. Prediction *might* be the goal, and might be
feasible, particularly where the regularities of interest are stationary distributions:
wealth distributions, epidemic sizes. He declines to rule out macroscopic prediction on
principle, noting that before Newton people would have said planetary orbits would never be
predicted.

### Sixteen reasons other than prediction to build models
`¶1.9`

The list, in Epstein's order, "off the top of my head and in no particular order":

1. Explain (very distinct from predict)
2. Guide data collection
3. Illuminate core dynamics
4. Suggest dynamical analogies
5. Discover new questions
6. Promote a scientific habit of mind
7. Bound (bracket) outcomes to plausible ranges
8. Illuminate core uncertainties
9. Offer crisis options in near-real time
10. Demonstrate tradeoffs / suggest efficiencies
11. Challenge the robustness of prevailing theory through perturbations
12. Expose prevailing wisdom as incompatible with available data
13. Train practitioners
14. Discipline the policy dialogue
15. Educate the general public
16. Reveal the apparently simple (complex) to be complex (simple)

Reproduced in full because the list *is* the paper's most-cited content, and because the
useful move in an assignment or exam is to name the specific one your model serves. The rest
of the essay elaborates six of them: 1, 2, 3, 4, 5 and 6.

> [!tip] Reading the list structurally
> Roughly: 1–8 are scientific goals — they change what you know. 9–16 are institutional —
> they change what an organisation or a public can do. The split is not Epstein's, but it
> maps onto the [[modelling-for-science]] / [[modelling-for-policy]] distinction the subject
> teaches, and it makes the list far easier to recall than sixteen flat items.

### Explanation does not imply prediction
`¶1.10`

The crucial distinction, and the one to get exactly right. Three examples, all from
established science:

- Plate tectonics explains earthquakes, but does not permit us to predict the time and place
  of their occurrence.
- Electrostatics explains lightning, but we cannot predict when or where the next bolt will
  strike.
- Evolution is accepted as explaining speciation, but we cannot predict next year's flu
  strain.

Note what the examples share: an accepted, mechanistically detailed theory, paired with
outcomes that remain unforecastable because they depend on unmeasurable initial conditions or
on chance.

In the social sciences Epstein's counterpart is **generative explanation**
([[generative-explanation]]): macroscopic *explananda* — large-scale regularities such as
wealth distributions, spatial settlement patterns, or epidemic dynamics — emerge in
populations of heterogeneous software individuals interacting locally under plausible
behavioural rules ([[emergence]]). His example is the agent-based computational
reconstruction of the Kayenta Anasazi in Long House Valley (Axtell et al., PNAS 2002; see
[[sugarscape]]). That work was data-driven, and he considers the model explanatory — but is
careful to say he would not insist it is predictive on that account, and that being
data-driven was not necessary for the explanatory claim.

### To guide data collection
`¶1.11`

The target here is what Epstein calls naïve inductivism: the belief that science proceeds
from observation, and models are then constructed to account for the data. In the social
science rendition, you collect a lot of data and run regressions on it.

He does not say this is useless — "this can be very productive" — but that it is not the rule
in science, where theory often precedes data collection. Maxwell's electromagnetic theory
implied the existence of radio waves, which were then sought and found. General relativity
predicted gravitational light deflection, confirmed only later by experiment. The conclusion
is practical rather than philosophical: without models it is not always clear what data to
collect.

### Illuminate core dynamics: all the best models are wrong
`¶1.12`

Simple models can be invaluable without being "right" in an engineering sense. Epstein's
formulation is that the best models are *fruitfully* wrong — illuminating abstractions. He
reaches for Picasso: "Art is a lie that helps us see the truth."

The examples are three models everybody is still taught: the Lotka-Volterra ecosystem model,
Hooke's Law, and the Kermack-McKendrick epidemic equations — the deterministic SIR system
covered in [[w03b-reproduction-number]]. Mature practitioners know full well how approximate
these are and still entrust the formation of a student's most basic intuitions to them,
because they capture qualitative behaviours of overarching interest: predator-prey cycles,
the nonlinear threshold nature of epidemics, herd immunity ([[tipping-point]],
[[herd-immunity-threshold]]).

The framing to take from this section: the issue is never idealisation, since all models are
idealisations ([[abstraction]]). The issue is whether the model offers a **fertile**
idealisation. Box's aphorism closes the paragraph — all models are wrong, but some are
useful.

### Suggest analogies
`¶1.13–1.14`

A large number of seemingly unrelated processes turn out to satisfy the same formalism, so
they can all be read as interpretations of one underlying model. Coulomb's electrostatic
attraction and Newton's gravitational attraction have the same algebraic form. The diffusive
processes satisfying the heat equation, and the oscillatory ones satisfying the wave
equation, are physically diverse and formally identical. Samuelson's Nobel lecture makes the
economic version: the monopolistic firm as a maximum system connects structurally to an
entropy-maximising thermodynamic system, with temperature and entropy standing in the same
relation as wage rate to labour, or land rent to acres of land. One diagram does double duty.

Epstein's claim about why this matters is stronger than aesthetic appreciation. Analogies are
"headlights in dark unexplored territory". There is a powerful theory of infectious diseases.
If revolutions, religions, or the adoption of innovations unfold like epidemics, and it is
useful to treat them as formal analogues, then that pre-existing theory transfers to the new
field and can produce rapid advance.

### Raise new questions
`¶1.15`

Short and pointed. Models surprise us, make us curious, and lead to new questions. The aside
attached is the memorable part: "This is what I hate about exams. They only show that you can
answer somebody else's question, when the most important thing is: Can you ask a new
question?" Hilbert's Problems are his example of new questions producing huge advances
([[research-question]]).

### From ignorant militance to militant ignorance
`¶1.16–1.17`

The essay's actual conclusion, and the reason it gets quoted outside methodology courses.
Epstein argues the most important contribution of the modelling enterprise — distinct from
any particular model or technique — is that it enforces a scientific habit of mind he calls
*militant ignorance*: an iron commitment to "I don't know."

The content of that commitment: all scientific knowledge is uncertain, contingent, subject to
revision, and falsifiable in principle. Falsifiable in principle does not mean readily
falsified; it means one can specify observations that, if made, would falsify the claim. One
does not base beliefs on authority, but ultimately on evidence.

He then makes the political turn explicitly. This is a dangerous idea, because it levels the
playing field and permits the lowliest peasant to challenge the most exalted ruler. Science
as a mode of inquiry is fundamentally antithetical to monolithic intellectual systems.
Citing Feynman's essay on the hard-won "freedom to doubt", he closes: intellectuals have a
solemn duty to doubt, and to teach doubt; education is not about a saleable skill set but
about freedom from inherited prejudice and argument by authority. The modelling enterprise
enforces habits of mind essential to freedom.

---

## Recall Layer

> [!question]- What is Epstein's answer to someone who says they don't build models?
> That they do — they are running an implicit model whose assumptions are hidden, whose
> internal consistency is untested, and whose logical consequences and relation to data are
> unknown. Anyone who imagines how an epidemic or a war will unfold is running some model.
> The choice is explicit vs implicit, not model vs no model. `¶1.2–1.3`

> [!question]- Why does Epstein avoid the word "validate"?
> He is a Popperian: a model that survives testing has not been proven correct, only not yet
> falsified. He will say a model can be *calibrated* to data. `¶1.4`

> [!question]- Name the four advantages of explicit over implicit models, and the one Epstein
> says is simply impossible without explicitness.
> Calibration to historical and current data; replication by others; rigorous incorporation of
> domain expertise, with the model as a focal point for a multidisciplinary team; and
> sensitivity analysis. The last is the impossible one — there is nothing to sweep in a mental
> model. `¶1.5–1.7`

> [!question]- Do models remove the need for judgment in policy? What do they do instead?
> No, explicitly not — in the policy sphere, if not in particle physics. They reveal tradeoffs,
> uncertainties and sensitivities, and thereby *discipline the dialogue* about options, making
> unavoidable judgments more considered. `¶1.7`

> [!question]- Give three examples where an accepted theory explains without predicting.
> Plate tectonics explains earthquakes but not when or where the next occurs; electrostatics
> explains lightning but not where the next bolt strikes; evolution explains speciation but
> cannot predict next year's flu strain. `¶1.10`

> [!question]- What is generative explanation, and what does Epstein decline to claim for it?
> Macroscopic regularities — wealth distributions, settlement patterns, epidemic dynamics —
> emerging in populations of heterogeneous agents interacting locally under plausible
> behavioural rules. He considers the Anasazi model explanatory but will not insist it is
> predictive on that account, and notes the data-driven part was not necessary. `¶1.10`

> [!question]- What is naïve inductivism, and what is Epstein's counter-example?
> The belief that science proceeds from observation, with models built afterwards to account
> for the data. Counter: Maxwell's equations implied radio waves before anyone looked, and
> general relativity predicted light deflection before it was measured. Without models it is
> not always clear what data to collect. `¶1.11`

> [!question]- In what sense are Lotka-Volterra, Hooke's Law and Kermack-McKendrick all wrong,
> and why are they still taught?
> Wrong in an engineering sense — none is accurate as a description of a real system. Still
> taught because they capture qualitative behaviours of overarching interest (predator-prey
> cycles, the nonlinear threshold nature of epidemics, herd immunity), which is what forms a
> student's basic intuitions. `¶1.12`

> [!question]- What separates a useful idealisation from a useless one, given that all models
> are idealisations?
> Whether the idealisation is *fertile* — whether it illuminates the core dynamics. Epstein's
> phrase is that the best models are "fruitfully wrong". `¶1.12`

> [!question]- Why does Epstein think formal analogies between models are more than elegant?
> Because a formal analogue lets an established theory transfer wholesale to an unexplored
> field — "headlights in dark unexplored territory". If innovation adoption or revolution
> unfolds like an epidemic, epidemic theory becomes available for it. `¶1.13–1.14`

> [!question]- Reconstruct the sixteen reasons in two groups.
> Scientific (roughly 1–8): explain; guide data collection; illuminate core dynamics; suggest
> dynamical analogies; discover new questions; promote a scientific habit of mind; bound
> outcomes to plausible ranges; illuminate core uncertainties. Institutional (9–16): offer
> crisis options in near-real time; demonstrate tradeoffs and suggest efficiencies; challenge
> the robustness of prevailing theory through perturbations; expose prevailing wisdom as
> incompatible with available data; train practitioners; discipline the policy dialogue;
> educate the public; reveal the apparently simple to be complex and vice versa. `¶1.9`

> [!question]- What is "militant ignorance" and why does Epstein call it dangerous?
> An iron commitment to "I don't know": all scientific knowledge is uncertain, contingent,
> revisable, and falsifiable in principle, and beliefs rest on evidence rather than authority.
> Dangerous because it levels the playing field — it permits the lowliest peasant to challenge
> the most exalted ruler, which is intolerable to monolithic intellectual systems. `¶1.16–1.17`

> [!failure] Common failure modes
> - **Reading "explanation does not imply prediction" as "prediction is bad."** Epstein
>   explicitly allows that prediction might be a goal and might be feasible, especially for
>   stationary distributions, and refuses to rule out macroscopic prediction in principle.
>   The claim is about implication, not about worth.
> - **Reading the implication backwards.** The paper argues explanation does not imply
>   prediction. It does not argue that prediction implies explanation — though that
>   direction also fails, which is what a well-fitted regression with no mechanism is.
> - **Treating "all models are wrong" as permission.** The sentence has a second half. The
>   test is fertility: does the idealisation illuminate core dynamics? A model that is wrong
>   and illuminates nothing fails on Epstein's own terms.
> - **Citing the sixteen reasons as a fixed taxonomy.** He wrote them off the top of his head,
>   in no particular order, and says so. The list is an existence proof that alternatives to
>   prediction abound, not a classification scheme.
> - **Confusing "falsifiable in principle" with "readily falsified".** Epstein flags this
>   parenthetically. It means observations can be specified that would falsify the claim.

> [!exam] Exam surface
> The explanation/prediction distinction with the tectonics or electrostatics example is the
> most examinable single item. Beyond that: the implicit/explicit reframing as an answer to
> "why model at all"; sensitivity analysis as the advantage unavailable to a mental model;
> "discipline the dialogue" as the account of what models do for policy; generative
> explanation as the ABM-specific form of explanation; and "all models are wrong, but some
> are useful" attached to the fertility criterion rather than left as a slogan. Expect the
> sixteen reasons as a "name three, other than prediction" prompt rather than a recall-all.

> [!todo] Open threads
> - Epstein offers no criterion for *which* of the sixteen goals a given model should be
>   judged against, or what to do when a sponsor wants prediction and the model explains.
> - Generative sufficiency is asserted, not defended against the obvious objection: several
>   different rule sets can generate the same macroscopic pattern. Grimm's
>   [[pattern-oriented-modelling]] is the answer the modelling literature gives, and it is
>   not in this essay — see [[grimm-2020-odd-second-update-digest]].
> - "Fertile idealisation" is doing heavy lifting with no test attached. How do you know
>   before the fact whether an abstraction will be fruitful?

---

## Topics covered

- [x] `¶1.1` — Archimedes; the enterprise and its misunderstanding → [[#Why model?]]
- [x] `¶1.2–1.3` — "You *are* a modeler"; implicit models → [[#Why model?]]
- [x] `¶1.4` — The validation retort; Popper → [[#Why model?]]
- [x] `¶1.5–1.6` — Explicit models: entailment, replication, calibration, domain expertise → [[#Why model?]]
- [x] `¶1.7` — Sensitivity analysis; disciplining the policy dialogue → [[#Why model?]]
- [x] `¶1.8` — Prediction as a possible but non-mandatory goal → [[#Can you predict?]]
- [x] `¶1.9` — The sixteen reasons → [[#Sixteen reasons other than prediction to build models]]
- [x] `¶1.10` — Explanation vs prediction; generative explanation; Anasazi → [[#Explanation does not imply prediction]]
- [x] `¶1.11` — Naïve inductivism; Maxwell; general relativity → [[#To guide data collection]]
- [x] `¶1.12` — Fruitfully wrong models; Picasso; Box → [[#Illuminate core dynamics: all the best models are wrong]]
- [x] `¶1.13–1.14` — Formal analogies; Coulomb/Newton; Samuelson; headlights → [[#Suggest analogies]]
- [x] `¶1.15` — Models raise new questions; the exam complaint; Hilbert → [[#Raise new questions]]
- [x] `¶1.16–1.17` — Militant ignorance; Feynman; freedom to doubt → [[#From ignorant militance to militant ignorance]]

Acknowledgements and references carry no argumentative content and are not digested; the
funding note (NIH MIDAS, NIH Director's Pioneer Award) is recorded on
[[joshua-epstein]] instead.

## Connections

`See also:` [[sources/epstein-2008-why-model]] · [[explanation-vs-prediction]] ·
[[generative-explanation]] · [[sensitivity-analysis]] · [[model]] · [[abstraction]] ·
[[modelling-for-science]] · [[modelling-for-policy]] · [[occams-razor]] ·
[[research-question]] · [[joshua-epstein]] · [[sugarscape]] ·
[[grimm-2020-odd-second-update-digest]] · [[a1-project-specification]]
