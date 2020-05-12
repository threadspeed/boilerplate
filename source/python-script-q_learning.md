---
title: python script q learning (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'q learning'


Modules used in program: 
* `import random`

## python q learning

Python mysql example: q learning

```python
import random

class QLearner:
	def __init__(self, num_actions):
	  #play around with these parameters for different results
		self.learning_rate = 0.03
		self.discount_factor = 0.65
		self.num_actions = num_actions
		self.last_state = None
		self.last_action = None
		self.explore = 0.25
		#the lookup table for q-func
		self.q_table = {}
	#evaluates an input given a state and whether or not that state is final
	def evaluate(self, state, final, reward, should_learn):
		max_q = -10000
		best_action = 0
		#have we seen this state before?
		#if not add it to the q_table
		if state not in self.q_table.keys():
			self.q_table[state] = []
			for action in xrange(self.num_actions):
				self.q_table[state].append(0)
		#occasionally head of the beaten path
		if random.random() < self.explore and should_learn:
			best_action = random.randint(0,self.num_actions - 1)
			self.last_state = state
			self.last_action = best_action
			return best_action
		#search through the action space to find the best next action
		for action in xrange(self.num_actions):
			q = self.q_func(state, action)
			if q >= max_q:
				max_q = q
				best_action = action
		if self.last_state is not None and should_learn:
			#learn
			old_q = self.q_func(self.last_state,self.last_action)
			new_q = (1-self.learning_rate) * old_q + self.learning_rate * (reward + self.discount_factor * self.q_func(state, best_action))
			self.update_q_func(self.last_state, self.last_action, new_q)
		self.last_state = state
		self.last_action = best_action
		return best_action
	#in a basic q-learner, the q_func is a table lookup
	def q_func(self, state, action):
		if state in self.q_table.keys():
			return self.q_table[state][action]
	def update_q_func(self, state, action, new_val):
		self.q_table[state][action] = new_val
	def reset(self):
		self.last_state = None
		self.last_action = None





```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
