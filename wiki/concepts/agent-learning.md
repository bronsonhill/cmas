---
title: Agent Learning
type: concept
tags: [abm, agent-behaviour, odd]
date: 2026-08-30
---

# Agent Learning

Learning, as an ODD design concept, is change in an agent's *behavioural rule* on the
basis of accumulated experience — as distinct from
[[adaptive-behaviour|adaptation]], which is a response to current conditions under a
fixed rule.

## How it works

The operational marker used in this subject is scope. Adaptation is within a simulation
run; learning carries information across runs, or across repeated episodes within a run.
An agent that learns has memory that outlives the state it was sensing.

The lecture's example is an evacuation model. Run a drill; the agents that reroute around
a blocked corridor mid-run are adapting. Now run the drill again and tell the agents to
retain what they found — where the exits are, which signage worked. That is learning, and
it changes the rule they enter the second run with.

Reinforcement learning fits the same frame: an action yields a reward, the reward is a
[[objective-function|utility]] signal, and the agent shifts its policy towards actions
that paid off. The vocabulary differs from ABM's but the machinery is the same.

Kennedy ([[kennedy-2012-modelling-human-behaviour]]) adds the knowledge-representation
side. Human learning covers declarative knowledge (facts) and, in some systems,
procedural knowledge (IF-THEN rules). Retention varies from architectures that never
forget to ones with almost no memory; how much to model depends entirely on the model's
purpose. [[soar]] and [[act-r]] both implement learning of both kinds.

Many models deliberately omit learning. The [[business-investment-model]] does, and
justifies it: the scenario is a one-off retirement decision, and there are no do-overs at
sixty.

## Relationships

- [[adaptive-behaviour]] — the within-run counterpart, and the distinction most often
  got wrong
- [[agent-prediction]] — the other half of the design concept in Grimm's 2010 grouping
- [[objective-function]] — reward and utility are the same signal
- [[cognitive-architecture]] — where learning mechanisms are supplied off the shelf
- [[odd-protocol]]

## Sources

- [[w05a-sensing]] — learning vs adaptation, flagged as an exam distinction; the
  evacuation-drill example and the reinforcement-learning connection
- [[kennedy-2012-modelling-human-behaviour]] — declarative and procedural knowledge,
  retention, and architecture support
