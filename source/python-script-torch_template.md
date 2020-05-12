---
title: python script torch template (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'torch template'


Modules used in program: 
* `import random`
* `import matplotlib.pyplot as plt`
* `import gym`
* `import numpy as np`
* `import random`
* `import torch.nn.functional as F`
* `import torch.optim as optim`
* `import torch.nn as nn`
* `import torch.nn.functional as F`
* `import torch.optim as optim`
* `import torch.nn as nn`
* `import torch`

## python torch template

Python mysql example: torch template

```python
# Reference: http://inoryy.com/post/tensorflow2-deep-reinforcement-learning/

import torch
import torch.nn as nn
import torch.optim as optim
import torch.nn.functional as F
import torch.nn as nn
import torch.optim as optim
import torch.nn.functional as F
from torch.distributions.categorical import Categorical

import random
import numpy as np
import gym
import matplotlib.pyplot as plt
from collections import deque
import random

# Hyperparameters
learning_rate = 1e-4
gamma = 0.98
seed = 1
num_episodes = 5000
batch_sz = 200

# Set up the env
env = gym.make("CartPole-v0")
np.random.seed(seed)
torch.manual_seed(0)
torch.backends.cudnn.deterministic = True
env.seed(seed)

class Policy(nn.Module):
    def __init__(self):
        super(Policy, self).__init__()
        self.fc1 = nn.Linear(4, 120)
        self.fc2 = nn.Linear(120, 84)
        self.fc3 = nn.Linear(84, env.action_space.n)

    def forward(self, x):
        x = torch.Tensor(x)
        x = F.relu(self.fc1(x))
        x = F.relu(self.fc2(x))
        x = F.relu(self.fc3(x))
        x = Categorical(logits=x)
        return x.sample()

class Value(nn.Module):
    def __init__(self):
        super(Value, self).__init__()
        self.fc1 = nn.Linear(4, 64)
        self.fc2 = nn.Linear(64, 1)

    def forward(self, x):
        x = torch.Tensor(x)
        x = F.relu(self.fc1(x))
        x = F.relu(self.fc2(x))
        return x

# TODO: initialize agent here:
pg = Policy()
vf = Value()

# start the game
ep_rews = np.zeros((num_episodes,))
next_obs = env.reset()
for update in range(num_episodes):
    # storage helpers for data
    actions = np.empty((batch_sz,), dtype=np.int32)
    rewards, dones, values = np.zeros((3, batch_sz))
    observations = np.empty((batch_sz,) + env.observation_space.shape)
    next_obs = env.reset()
    for step in range(batch_sz):
        observations[step] = next_obs.copy()
        
        # TODO: put action logic here
        action = pg.forward(observations[step])
        value = vf.forward(observations[step])
        
        # execute the game and log data.
        actions[step], values[step] = action, value
        next_obs, rewards[step], dones[step], _ = env.step(actions[step])
        if dones[step]:
            break
    
    ep_rews[update] = rewards.sum()

    if update % 10 == 0:
        print(f"update = {update}, rewards = {ep_rews[update]}")
    

p = Policy()
print(p)
p.forward(torch.Tensor(env.observation_space.sample()))

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
