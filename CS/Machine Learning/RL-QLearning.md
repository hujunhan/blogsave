---
title: RL:tabular Q-learning
author: Junhan Hu
tags: [ml,rl]
mathjax: true
categories:
- CS
- Machine Learning
date: 2019-4-27 20:42:00
---

## 1 Introduction

Q-Learning: method based on Q value

* Every *action* in a specific *state* will have a Q value $Q(s,a)$
* For example, if someone in state $s_1$ have 2 optional action $a_1$ and $a_2$, and $Q(s_1,a_1)>Q(s_1,a_2)$, then this agent will do $a_1$ rather than $a_2$ 

<!-- more -->

Main idea: 

1. Start with a bad Q-table that will guide our action
2. Do action based on Q-table
3. Calculate **estimated Q-value** before action and **real Q-value ** after action
4. Update the Q-table based the error between esti-Q-val and real-Q-val, make the Q-table better for action

## 2 Simple Game

### Q-table

index matches states, columns matches actions

start with 0

### Choose action

`epsilon`: e.g. $epsilon=0.9$

* 90% time choose the best action based on Q-table
* 10% time choose random action to explore the world

### Environment Feedback

AKA *reward*

e.g. Only when the agent reach the *goal point*, it will get reward $1$, else the reward is $0$. 

And *agent’s state* and *environment* update can also be done in this module. 

### Main loop

```pseudocode
initialize the Q-table
Repeat (for each episode):
	initialze the state
	while not is_end:
		action=choose_action(state,q-table)
		new_state,reward=env_feedback(state,action)
		q_estimate=q-table[S][A] #estimate Q value by Q-table
		if end:  # if reach the goal 
			q_real=reward #real Q value
			is_end=true
		else:
			q_real=reward+Gamma*q-table[n_state].max()
		update_q_table(q_real,q_estimate)
		update_env(S,A)
		state=new_state
```

## 3 Hyper Parameter

We update our Q-table by 
$$
Q(s, a) \leftarrow Q(s, a)+\alpha\left[r+\gamma \max _{a^{\prime}} Q\left(s^{\prime}, a^{\prime}\right)-Q(s, a)\right]
$$
There are 2 hyper parameter we can tune:

* $\alpha$ : learning rate, how much error we should learn. This value should be smaller than 1
* $\gamma$ : reduction value
  * if $\gamma=1$, the future can be totally estimated. So agent will calculate long term reward add up.
  * if $\gamma=0$, the future can **not** be estimated at all, so the agent will only value the next step’s reward.

