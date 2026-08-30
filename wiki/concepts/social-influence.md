---
title: Social Influence
type: concept
tags: [cognition, agent-behaviour, social-simulation]
date: 2026-08-30
---

# Social Influence

Social influence is the shaping of an individual's behaviour by others. Kennedy identifies
two mechanisms: a **theory of mind**, by which people model what others intend, know and
feel; and direct influence, by which behaviour is pulled towards that of the surrounding
group.

## How it works

**Theory of mind** is the internal model each agent keeps of other agents. It is what
makes social mammals' behaviour more complicated than a fixed instinct set could produce
— social insects and slime moulds, by contrast, appear fully driven by inherited
responses to stimuli. Shared concepts between agents' models of each other is what
language is, and the exchange of information, goods and services that follows is what
builds culture and economies. In modelling terms, a theory of mind is
[[agent-prediction|prediction]] aimed at other agents rather than at the environment.

**Direct influence** has a quantitative form. Latané's (1981) law of social impact:

$$I = sN^t$$

where $I$ is the percentage of subjects conforming or imitating, $s$ a constant of the
circumstances, $N$ the number of others exerting influence, and $t$ a factor below one,
often near $\tfrac{1}{2}$. The sublinear exponent is the content: the tenth influencer
adds far less than the second. The same mechanism produces **bystander inhibition** — a
larger group distributes the responsibility to act, so each member is less likely to act.

## Formula

$$I = sN^{t}, \qquad t < 1,\ \text{often} \approx 0.5$$

## Where group influence lands

Friedkin and Johnsen (1999) found that mutual influence within a group can settle on the
group's mean, on a compromise displaced from the mean, on the position of a dominant
member, or on no consensus at all. All four are possible outcomes of the same mechanism,
which is a useful caution against assuming convergence.

Surowiecki (2005) cuts the other way. Groups can outperform every individual in them, but
only under conditions: the good results come from *differences* between members'
independent evaluations, aggregated afterwards — not from compromise or consensus. Social
influence, by producing conformity and destroying independence, is what degrades them. His
crowd example: some are willing to riot, some never would, and most decide by watching
the others.

## Relationships

- [[collectives]] — where group structure is represented
- [[agent-interaction]] — the mechanism influence travels along
- [[agent-neighbourhood]] — who counts as "the others"
- [[decentralisation]] — aggregate signals without a central authority
- [[emergence]] — riots and market panics as influence-driven collective outcomes

## Sources

- [[kennedy-2012-modelling-human-behaviour]] — theory of mind, Latané's law, Friedkin and
  Johnsen on convergence, Surowiecki on when crowds are wise
