---
title: python script stocks (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'stocks'


Modules used in program: 
* `import random`
* `import tensorflow as tf`
* `import random`
* `import numpy as np`

## python stocks

Python mysql example: stocks

```python
#Stock prices
from google_finance import Share
#visualization
from matplotlib import pyplot as plt
#matrix math
import numpy as np
import random
#machine learning
import tensorflow as tf
import random


if __name__ == '__main__':
    prices = get_prices('GOOG', '2000-07-01', '2017-07-01', 'resource/stock_prices.npy')
    actions = ['Buy', 'Sell', 'Hold']
    hist = 200
    # TBD
    # policy = RandomDecisionPolicy(actions)
    # policy = QLearningDecisionPolicy(actions)
    budget = 1000.0
    num_stocks = 0
    avg, std = run_simulations(policy, budget, num_stocks, prices, hist)
    print(avg, std)

class DecisionPolicy:
    def select_action(self, current_state, step):
        pass

    def update_q(self, state, action, reward, next_state):
        pass

class RandomDecisionPolicy(DecisionPolicy):
    def __init__(self, actions):
        self.actions = actions

    def select_action(self, current_state, step):
        action = self.actions[random.randint(0, len(self.actions) - 1)]
        return action


class QLearningDecisionPolicy(DecisionPolicy):
    def __init__(self, actions, input_dim):
        self.epsilon = 0.5
        self.gamma = 0.001
        self.actions = actions
        output_dim = len(actions)
        h1_dim = 200

        #3 layer neural network
        self.x = tf.placeholder(tf.float32, [None, input_dim])
        self.y = tf.placeholder(tf.float32, [output_dim])
        W1 = tf.Variable(tf.random_normal([input_dim, h1_dim]))
        b1 = tf.Variable(tf.constant(0.1, shape=[h1_dim]))
        h1 = tf.nn.relu(tf.matmul(self.x, W1) + b1)
        W2 = tf.Variable(tf.random_normal([h1_dim, output_dim]))
        b2 = tf.Variable(tf.constant(0.1, shape=[output_dim]))
        self.q = tf.nn.relu(tf.matmul(h1, W2) + b2)

        #measuring error
        loss = tf.square(self.y - self.q)
        #updating weights
        self.train_op = tf.train.GradientDescentOptimizer(0.01).minimize(loss)

    def select_action(self, current_state, step):
        threshold = min(self.epsilon, step / 1000.)
        if random.random() < threshold:
            # Exploit best option with probability epsilon
            action_q_vals = self.sess.run(self.q, feed_dict={self.x: current_state})
            action_idx = np.argmax(action_q_vals)  # TODO: replace w/ tensorflow's argmax
            action = self.actions[action_idx]
        else:
            # Explore random option with probability 1 - epsilon
            action = self.actions[random.randint(0, len(self.actions) - 1)]
        return action

    def update_q(self, state, action, reward, next_state):
        action_q_vals = self.sess.run(self.q, feed_dict={self.x: state})
        next_action_q_vals = self.sess.run(self.q, feed_dict={self.x: next_state})
        next_action_idx = np.argmax(next_action_q_vals)
        action_q_vals[0, next_action_idx] = reward + self.gamma * next_action_q_vals[0, next_action_idx]
        action_q_vals = np.squeeze(np.asarray(action_q_vals))
        self.sess.run(self.train_op, feed_dict={self.x: state, self.y: action_q_vals})

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
