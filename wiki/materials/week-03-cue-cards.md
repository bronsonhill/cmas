#flashcards/week-03

# Week 3 Cue Cards

Cards drawn from [[w03a-analysing-models]] and [[w03b-reproduction-number]], and from the
digests [[w03a-analysing-models-digest]] and [[w03b-reproduction-number-digest]] — analysing
models rather than building them, and the reproduction number as the quantity that makes an
epidemic model into a decision tool.

## Elaborative Interrogation

Your model runs without errors and produces curves that look about right. Why is that not evidence that it has been analysed?
?
Analysis is two distinct activities and running cleanly addresses neither. The first is establishing that the model behaves correctly and is an adequate abstraction of the target system — a check against patterns, not against crashes. The second is using it on the problem it was built for. A model can be internally correct and still fail to reproduce what it was meant to explain, and it can do both and still be useless for the decision at hand. See [[model-analysis]].
#card/cmas #card/week-03

"We simulate because simulation is more rigorous than observing the real world." Why is that a misstatement of the lecture's argument for simulation?
?
The argument is about access, not rigour. Real-world study is limited to the data you can collect, and collecting more may be costly, slow, unethical or impossible — funding survey panels, travelling to wherever the animals you study live, or deliberately infecting people. Simulation buys freedom to manipulate the system and sample it without limit. Where data is cheap and ethical to collect, the case for simulating weakens accordingly, so it is contingent rather than general. See [[model-analysis]].
#card/cmas #card/week-03

Most of the class answered that the ODD protocol is most useful when *formulating the question*. Why did the lecturer disagree, and where is it actually most useful?
?
Formulating the question and assembling hypotheses come *before* an ODD is written — you need to know what you are going to build before you can describe it. ODD is most useful at three later points: choosing the model structure (you are deciding on all the components), implementing (it is the roadmap holding the specifications), and communicating (it is the plain-language description handed to someone else). See [[odd-protocol]] and [[modelling-cycle]].
#card/cmas #card/week-03

In Schelling's segregation model a 30% similarity threshold produces neighbourhoods around 73% homogeneous. Why is that gap the point of the model rather than an inconsistency in it?
?
Because it shows the aggregate outcome exceeding, not merely reflecting, the individual rule that generates it. No agent wants a 73%-homogeneous neighbourhood; the rule only says "move if fewer than 30% of my neighbours are like me". Segregation of that strength emerges from mild preferences with nobody holding a preference for segregation, which is precisely the claim about [[emergence]] the model exists to demonstrate. See [[schelling-segregation-model]].
#card/cmas #card/week-03

Schelling's model reproduces observed residential segregation. Why does the slide conclude only that the hypothesis is "plausible" rather than that it is correct?
?
Reproducing a pattern establishes that the hypothesised mechanism is *sufficient* to generate it, not that it is the mechanism actually operating in the real world. Some other process could produce the same pattern. This is the standard epistemic limit of generative explanation, and it is why the modelling cycle loops rather than terminating at a successful run. See [[modelling-for-science]].
#card/cmas #card/week-03

In the policy pipeline — problem, objectives, interventions, projections, decision analysis, implementation — the model is used at step 4 only. Why does that matter for how much authority a model's output carries?
?
Because objectives and the candidate intervention set come from engagement with decision-makers, and the decision analysis weighs merits against objectives the model did not choose. The model supplies projections under assumptions; it does not supply the value judgements encoded in the objectives. A claim of "we followed the science" conflates a projection with a decision about what to optimise. See [[modelling-for-policy]].
#card/cmas #card/week-03

Acceptability and restrictions on personal freedom were raised in class as genuine measures of COVID-19 policy success. Why does their being hard to quantify constrain the analysis before any modelling happens?
?
An objective that is not represented in the model cannot be projected, so it is absent from every projection the model produces. The choice of objectives therefore silently bounds what the analysis is capable of concluding — a scoping decision that looks administrative but is actually a modelling decision. See [[modelling-for-policy]].
#card/cmas #card/week-03

The antiviral stockpile study concluded that treatment alone was insufficient. Why is a negative result immediately useful in policy modelling in a way it might not be in a scientific study?
?
Policy modelling is a comparison between available actions, so eliminating one directly narrows the decision — this finding changed what the Australian pandemic plan relied on. A scientific negative result is also informative (the mechanism is insufficient to generate the pattern) but does not by itself indicate what to do instead. See [[influenza-antiviral-stockpile-model]].
#card/cmas #card/week-03

Why can't you simply record every agent's full trajectory and decide later which parts mattered?
?
Volume. 100 agents over 100 steps over 100 runs over 100 scenarios is $10^8$ observations — neither storable at scale nor interpretable. The choice of what to record is therefore forced rather than optional, and it must be driven by the question the model was built to answer rather than by what is convenient to log. See [[summary-statistic]].
#card/cmas #card/week-03

Why is it wrong to say "$R > 1$ means the outbreak will take off"?
?
The correct statement is that it *may* take off. $R_0$ is an average, and early on the infectious pool is tiny, so the realised number of onward infections is a small sample from a distribution with mean $R_0$ — and small samples can come out at zero. If the index case recovers before infecting anyone, the chain ends regardless of transmissibility. The reverse direction is not symmetric: below one, extinction is assured. See [[reproduction-number]] and [[stochastic-fadeout]].
#card/cmas #card/week-03

Why can't the reproduction number be measured directly, even with good surveillance data?
?
Measuring it would require a complete log of everyone each case contacted, plus attribution of each new infection to a specific transmitting contact. Neither is obtainable — contact patterns depend on unobserved behaviour and transmission attribution is usually impossible after the fact. $R$ is therefore inferred from case data, which is why published values for the same disease differ between sources and get revised. See [[reproduction-number]].
#card/cmas #card/week-03

Two diseases both have $R_0 = 8$. Why does that not tell you their outbreaks will look alike?
?
Because $R_0 = \beta/\gamma$ is a *ratio*, so the same value arises from a transmissible short infection or a milder long one. The lecture's chickenpox-like ($\gamma = 0.14$) and mumps-like ($\gamma = 0.07$) profiles share $R_0 = 8$ and a peak near 620, but peak at day 9 and day 18 respectively, and the mumps-like curve still has ~80 people infectious at day 50 where the other has finished. Same eventual reach, very different demand on a health system. See [[reproduction-number]].
#card/cmas #card/week-03

Raising $R_0$ from 4 to 16 barely changes how many people are eventually infected. Why, and what does it change instead?
?
Because the final attack rate saturates. The curve is zero below $R_0 = 1$, rises steeply to roughly 0.8 by $R_0 = 2$, and reaches ~0.98 by $R_0 = 4$; there is very little headroom left above that. What further increases change is the *speed* and *height* of the outbreak — how fast it arrives and how much simultaneous demand it creates. See [[reproduction-number]] and [[outbreak-summary-measures]].
#card/cmas #card/week-03

Why does the vaccination coverage requirement rise so steeply that measles leaves under 7% of slack while a disease at $R_0 = 2$ tolerates half the population being susceptible?
?
Because $v \ge 1 - 1/R_0$ is steep at low $R_0$ and flat at high $R_0$. At $R_0 = 2$ the threshold is 50%; at $R_0 = 16$ it is 93.75%. The policy consequence is that highly transmissible diseases are the first to return when coverage slips — the mechanism behind the Texas measles outbreak. See [[herd-immunity-threshold]].
#card/cmas #card/week-03

Why would anyone deliberately choose a deterministic model when stochastic models are more realistic?
?
Three reasons: you want the typical or average trajectory rather than a distribution; you need analytical tractability, since $R_0 = \beta/\gamma$, the attack-rate relation and $v \ge 1 - 1/R_0$ are all *derived* from the deterministic equations rather than measured from output; and it is cheap, running once instead of hundreds of times. What you accept is that tail events become unrepresentable. See [[deterministic-model]].
#card/cmas #card/week-03

## Mechanism

Starting from an observation and ending at a conclusion, what are the six steps of using a model for scientific purposes, and what is distinctive about step 3 in an agent-based study?
?
1. **Observe** — what don't we understand?
2. **Question** — often beginning "why?" or "how?"
3. **Hypothesise** — alternative answers to the question.
4. **Predict** — what does each hypothesis imply?
5. **Test** — evaluate the predictions.
6. **Analyse and conclude**, or repeat from step 1.

Step 3 is distinctive because the hypothesis takes the form of an *individual-level behaviour* — a rule agents follow — proposed as an explanation for a population-level phenomenon, then implemented as an ABM and judged on whether it reproduces the observed pattern. See [[modelling-for-science]].
#card/cmas #card/week-03

Starting from a decision-maker's problem and ending at implementation, what are the six steps of using a model for policy, and where does the model enter?
?
1. **Problem** — engage with the decision-maker to identify it.
2. **Objectives** — identify the management objectives.
3. **Interventions** — define the actions that can be taken.
4. **Projections** — evaluate the impact of interventions on objectives.
5. **Decision analysis** — evaluate the relative merit of the interventions.
6. **Implementation** — put the chosen intervention into practice.

The model enters at step 4 and nowhere else. Projections may send the process backwards, prompting revised objectives or new candidate interventions, and post-implementation data feeds back into future projections. See [[modelling-for-policy]].
#card/cmas #card/week-03

Write the deterministic SIR difference equations, and say what the repeated terms are doing.
?
$$S_{t+1} = S_t - \beta S_t I_t$$
$$I_{t+1} = I_t + \beta S_t I_t - \gamma I_t$$
$$R_{t+1} = R_t + \gamma I_t$$

Each flow term appears exactly twice with opposite signs — $\beta S_t I_t$ leaves $S$ and enters $I$; $\gamma I_t$ leaves $I$ and enters $R$. That pairing is what conserves the total population, and a compartment model whose terms do not pair up this way is leaking people. See [[difference-equation]] and [[compartmental-model]].
#card/cmas #card/week-03

Give the continuous-time form of the SIR model and the normalisation that usually accompanies it.
?
$$\frac{dS}{dt} = -\beta S I, \qquad \frac{dI}{dt} = \beta S I - \gamma I, \qquad \frac{dR}{dt} = \gamma I$$

Rather than describing change in discrete steps, these describe it continuously. Models written this way commonly track the *fraction* of the population in each compartment, so that $S + I + R = 1$. See [[difference-equation]].
#card/cmas #card/week-03

Derive the herd immunity threshold $v \ge 1 - 1/R_0$ in one line.
?
If a fraction $v$ of the population is immune, only $(1-v)$ of a case's contacts are susceptible, so the effective reproduction number is $R_0(1-v)$. Requiring $R_0(1-v) < 1$ gives $1 - v < 1/R_0$, hence $v > 1 - 1/R_0$. A sanity check on the result: it must be 0 at $R_0 = 1$ and approach 1 as $R_0$ grows. See [[herd-immunity-threshold]].
#card/cmas #card/week-03

You have a stochastic model and one summary measure you care about. What is the correct order of operations for reporting a result, and where do people skip a step?
?
1. Choose what to measure, driven by the question.
2. Run the model many times.
3. **Plot the distribution of the measurement.**
4. Only then decide how to compress it.

Step 3 is the one that gets skipped. A mean is always computable and always looks like an answer, so nothing in the output signals that the compression was invalid. See [[summary-statistic]] and [[bimodal-distribution]].
#card/cmas #card/week-03

$\gamma = 0.07$ in a deterministic SIR model. Give both equivalent readings of what that means.
?
**Individual level:** the average infectious period is $D = 1/\gamma \approx 14$ days.
**Population level:** on any given day, about 7% of the infectious population recovers.

These are the same statement about a rate, read at two levels, and moving between them fluently is the point of the slide. Note $D$ is a mean — in the stochastic version individual durations are distributed around it, not fixed. See [[difference-equation]].
#card/cmas #card/week-03

## Contrast

What is the key difference between modelling for science and modelling for policy?
?
Science seeks to *understand* a mechanism without intervening in the system; policy seeks to *act* on it. Schelling's model asks why segregation occurs; the policy version asks what a government could do about it. Policy modelling additionally assumes the model has already been validated, so validation is not part of its loop, and it compares actions rather than testing an explanation. The same model can serve both, but the experiments and summary measures differ. See [[modelling-for-science]] and [[modelling-for-policy]].
#card/cmas #card/week-03

$\beta$ has carried three distinct meanings across Weeks 2 and 3. State all three and say what goes wrong if you conflate them.
?
- **Week 2 ABM:** $q$ is the probability of transmission in a single contact between a susceptible and an infectious agent.
- **Week 3a stochastic:** $\beta$ = mean contacts per person per unit time $\times\, q$ — an effective contact rate carrying both behaviour and biology.
- **Week 3b deterministic:** $\beta$ = a per-capita *rate* of effective contact, appearing in the flow term $\beta S I$.

Carrying a numeric value across without re-deriving it produces wrong dynamics. A $q$ value is meaningless without the contact structure it sits in — $q = 0.2$ at 5 contacts per day and at 100 contacts per day describe entirely different diseases. See [[contact-rate]] and [[sir-model]].
#card/cmas #card/week-03

Distinguish $R$ from $R_0$, and say when the distinction starts to matter.
?
$R$ is the average number of secondary cases infected by a typical primary case. $R_0$ is the same quantity in a **totally susceptible** population. The distinction matters as soon as anyone is immune: with a fraction $v$ immune, the effective reproduction number falls to $R_0(1-v)$, which is exactly the mechanism behind the herd immunity threshold. $R_0$ is a property of disease-plus-population; $R$ changes as an outbreak depletes susceptibles. See [[reproduction-number]].
#card/cmas #card/week-03

A deterministic and a stochastic SIR model are run at identical parameters with $R_0 = 6.25$. How do their outputs differ, and which difference is the consequential one?
?
The deterministic model produces one smooth curve, identical on every run. The stochastic model produces a *distribution*: peak heights, timings and skews vary, and — the consequential difference — roughly 45% of runs produce no outbreak at all. The deterministic model generates an outbreak every time $R_0 > 1$, so the entire fadeout mode is invisible to it and no question about the *probability* of an outcome can be asked. See [[deterministic-model]] and [[stochastic-fadeout]].
#card/cmas #card/week-03

"Flattening the curve" and "reducing total infections" are not the same objective. Which outbreak summary measures does each target, and why does the distinction matter for a highly transmissible disease?
?
Flattening the curve targets **peak size** and **peak timing**; reducing total infections targets **final size**. The distinction matters because the attack rate saturates — above about $R_0 = 4$ nearly everyone is infected regardless — so for a transmissible disease the peak is often the only thing an intervention can realistically move. The smallpox-like profile still infects most people but peaks at day 38 rather than day 5, which is preparation time bought. See [[outbreak-summary-measures]] and [[epidemic-intervention]].
#card/cmas #card/week-03

Slide 13 (many overlaid trajectories) and slide 15 (a final-size histogram) contain the same information, yet the class could not see the dominant outcome in the first. Why not?
?
Every failed run lies along the zero axis superimposed on every other failed run, so 45% of the data renders as a single flat line indistinguishable from an axis. A histogram bins by outcome value and gives that mass its own visible bar. The general lesson: a trajectory overlay displays trajectories but not their *density*, so it systematically hides modes that coincide. See [[bimodal-distribution]].
#card/cmas #card/week-03

## Failure-Mode

You report that a simulated outbreak infects "on average about 3,000 of 10,000 people". The distribution is bimodal: ~45% of runs near zero, the rest near 5,200. What is wrong with your report, and what should it say?
?
The mean lands in the empty valley between the modes and describes no run the model produced — it is confidently wrong rather than merely imprecise, implying that a moderate outbreak is typical when moderate outbreaks essentially never occur. Anyone planning to that figure prepares for a scenario that cannot happen. The correct form is a mixture: "about 45% of the time the outbreak fails to establish; otherwise around 5,200 of 10,000 are infected." See [[bimodal-distribution]] and [[summary-statistic]].
#card/cmas #card/week-03

You accept that the mean is unusable on a bimodal distribution and switch to the median. Why is that not a fix?
?
The median tracks whichever mode holds more than half the probability mass, so it reports either "almost nobody infected" or "half the population infected" and jumps discontinuously between the two when the fadeout probability crosses 50%. A small parameter change flips the reported answer between extremes. Any single-number summary fails here; the distribution needs a mixture description. See [[bimodal-distribution]].
#card/cmas #card/week-03

An outbreak with $R_0 = 0.625$ keeps dying out, so you seed the population with 100 initial infectious agents instead of 1. What happens, and what does that establish?
?
It still dies out — all 25 trajectories decline monotonically to zero. Outbreak establishment is governed by the reproduction number, not by the size of the introduction: a hundred introductions each with $R_0 < 1$ is a hundred chains that each shrink generation by generation. The real-world analogue is H5N1 influenza, which spreads bird-to-human repeatedly but does not sustain human-to-human transmission. See [[reproduction-number]] and [[initial-conditions]].
#card/cmas #card/week-03

You scale a stochastic SIR model from 10,000 to 1,000,000 agents expecting the run-to-run variation to average away. What actually persists, and why?
?
Trajectories smooth out and peak height becomes highly predictable, but peak *timing* stays variable and — critically — the no-outbreak mode does not disappear. Population size damps variability only *within* an established outbreak, where the law of large numbers applies to a large infectious pool. Whether an outbreak establishes at all is decided in the first few generations, which involve a handful of individuals regardless of $N$. See [[stochastic-fadeout]].
#card/cmas #card/week-03

You increase Schelling's similarity threshold from 30% to 90% expecting sharper segregation. What actually happens, and what general phenomenon is this?
?
The model stops converging at all — too few households can be satisfied simultaneously, so agents relocate indefinitely and unhappiness never reaches zero. Convergence breaks down somewhere around a 70% threshold. This is a [[tipping-point]] or critical point: the system's qualitative behaviour changes either side of a parameter value rather than degrading smoothly. The epidemic instance is $R = 1$. See [[schelling-segregation-model]].
#card/cmas #card/week-03

You model vaccination by moving agents from $S$ directly to $R$ and describe the result as a vaccination model. What have you actually assumed, and what would representing an imperfect vaccine require?
?
You have assumed the vaccine is perfectly and immediately effective, and you cannot represent waning immunity or partial protection. The representation is adequate only for asking about coverage thresholds. An imperfect vaccine needs a *separate state* with a reduced infection probability rather than a transfer to $R$ — a structural change to the compartment diagram, and the one Assignment 1 requires, since it asks for an added state. See [[herd-immunity-threshold]] and [[model-extension]].
#card/cmas #card/week-03

The zombie state diagram has arrows $S \to Z$, $S \to D$, $Z \to D$ and $D \to Z$. What breaks, and what does fixing it require?
?
$Z \leftrightarrow D$ is a closed loop, so a destroyed zombie reanimates indefinitely and the population never resolves. The fix is a **permanently dead** state that cannot re-enter $Z$ — the same compartment-splitting move as distinguishing died-naturally from destroyed-after-reanimating. Note the fix is not to delete $D \to Z$, which is the mechanism the model exists to represent. See [[zombie-apocalypse-model-design]] and [[compartmental-model]].
#card/cmas #card/week-03

You propose "how can I maintain a sustainable ratio of humans to zombies?" as your research question and it is rejected as intractable. What is missing, and what does a usable version look like?
?
No measurement answers it and no bound tells you when you have succeeded. Usable versions bound the scope and name a measurable: what safe-zone *capacity* is needed to hold the human population above some level, or what *impact* does cremating corpses have on the zombie population. The transferable pattern is a triple — bound the question, identify the state or mechanism it requires, name the variable that answers it. That triple is what the assignment rubric marks. See [[research-question]].
#card/cmas #card/week-03

You design an experiment by moving sliders until something interesting happens, then report it. What discipline is missing, and what does it require you to do first?
?
This is playing, not experimenting — the lecturer's "fishing experiment". Two questions must be answered *before* anything is varied: what do I want to know about the model's behaviour, and how can I design experiments to learn it. The variation itself must then be systematic — a baseline seed value with structured variations up and down across parameters, initial conditions and random seeds — rather than opportunistic. See [[model-analysis]].
#card/cmas #card/week-03

You quote from the Week 3b recording that COVID-19 delta had $R_0 \approx 6$, that the fadeout example used $\gamma = 1.4$, and that measles requires about 90% coverage. Why is each of these a risk, and what should you have used?
?
All three differ from the slides, which are authoritative: the fadeout example uses $\gamma = 0.4$ (the spoken 1.4 would make $R_0 = 0.18$, not 0.625); the chart band for delta is roughly 5–8; and measles at $R_0 = 16$ requires 93.75%, chickenpox 87.5%. The recording also calls the attack-rate curve "logarithmic" when it is a saturating curve from the final-size relation. When slides and recording disagree, the deck wins. See [[w03b-reproduction-number]].
#card/cmas #card/week-03

## Deck notes

**Coverage.** 38 cards over both Week 3 lectures — substantially larger than the 16-card
Week 1 and Week 2 decks, because Week 3 carries more genuinely examinable mechanism than
either. The 3a material is mostly conceptual (two purposes, one statistical trap) while 3b is
the subject's only quantitative lecture, so the formulas, their derivations and their
interpretations all need separate cards.

**Design choices.** The bimodal-mean problem gets four cards rather than one — the failure
itself, why the median is not a fix, why the overlay plot hid it, and the correct order of
operations — because it is the single idea both lectures are built around and it is the one
most likely to be tested by being disguised in a new scenario. The $\beta$/$\gamma$ meaning
shift also gets its own contrast card despite not being stated as a lecture point anywhere,
because three formulations in three weeks is the most error-prone thing in the epidemic
material.

Formulas are asked for by derivation or interpretation rather than recall wherever possible.
The herd immunity card asks you to derive $v \ge 1 - 1/R_0$ in one line rather than state it,
since the derivation is short and someone who can produce it will not invert the formula
under pressure.

**The last card is unusual and deliberate.** It cards the slide/recording discrepancies
themselves. Three of the four are numbers plausibly examinable, and the failure mode —
quoting a spoken figure that contradicts the deck — is one this specific cohort is exposed to
because the transcripts are available.

**Excluded deliberately.** The assignment marking rubric and administration; the
disease-band table from the herd immunity chart (recognition material, and the bands are
wide); the individual histogram bin values from 3a beyond the two modes; the response-surface
plots from the antiviral study, which cannot be read at slide resolution. The Schelling model
gets two cards rather than four — the 73% result and the non-convergence — since the six-step
pipeline is carded generically.

**Deferred.** The effective reproduction number $R_t$ is implied by the $R$/$R_0$ distinction
but never developed in the lecture, so there is no card for it; if a later lecture picks it
up, card it there. Sensitivity and uncertainty analysis, which is where "how many replicates
is enough" gets answered, lands in weeks 10–12. Where $R_0 = \beta/\gamma$ actually comes from
is asserted rather than derived in the lecture, so no derivation card exists for it.

**Suggested starting interval.** 1–3 days, in whichever tool you review in.
