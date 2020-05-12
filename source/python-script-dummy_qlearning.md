---
title: python script dummy qlearning (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'dummy qlearning'

Functions in program: 
* `def rargmax(vector):`

Modules used in program: 
* `import matplotlib.pyplot as plt`
* `import random as pr`
* `import numpy as np`
* `import gym`

## python dummy qlearning

Python example: dummy qlearning

```python
import gym
import numpy as np
import random as pr
import matplotlib.pyplot as plt
from gym.envs.registration import register


def rargmax(vector):
    """ Argmax that choose randomly eligible maximu indices. """
    m = np.amax(vector)
    indices = np.nonzero(vector == m)[0]
    return pr.choice(indices)


register(
        id='Frozenlake-v3',
        entry_point='gym.envs.toy_text:FrozenLakeEnv',
        kwargs={'map_name':'4x4',
            'is_slippery':False
            }
        )

env = gym.make('Frozenlake-v3')

# Initialize table with all zeros
Q = np.zeros([env.observation_space.n,env.action_space.n]) # 4*4 tables and 4 action 16*4 for frozen lake
num_episodes = 2000

# create list to contain total rewards and steps per episodes
rList = []
for i in range(num_episodes):
    # Reset environment and get first new observation
    state = env.reset()
    rAll = 0
    done = False

    while not done:
        action = rargmax(Q[state, :])
        # Get new state and reward from env
        new_state, reward, done, _ = env.step(action)

        # Update Q-table with new knowldege using learning rate
        Q[state,action] = reward + np.max(Q[new_state,:])
        rAll += reward
        state = new_state
    rList.append(rAll)

print("Success rate: " + str(sum(rList)/num_episodes))
print("Final Q-Table Values")
print(Q)
plt.bar(range(len(rList)), rList, color="blue")
plt.show()

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
