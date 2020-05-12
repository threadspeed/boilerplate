---
title: python script conditional-q (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'conditional-q'

Functions in program: 
* `def mkdir(base, name):`

Modules used in program: 
* `import torchvision.transforms as T`
* `import torch.nn.functional as F`
* `import torch.nn as nn`
* `import torch`
* `import random`
* `import numpy as np`
* `import gc`
* `import time`
* `import random`
* `import os`
* `import pdb`
* `import numpy as np`
* `import gym`
* `import argparse`

## python conditional-q

Python mysql example: conditional-q

```python
#!/usr/bin/env python

import argparse
import gym
from gym import wrappers
import numpy as np
import pdb
import os
import random
import time
import gc

import numpy as np
import random
import torch
import torch.nn as nn
from torch import optim
import torch.nn.functional as F
import torchvision.transforms as T
from torch.autograd import Variable

class ReplayMemory(object):
    """ Facilitates memory replay. """
    def __init__(self, capacity):
        self.capacity = capacity
        self.memory = []

    def push(self, event):
        self.memory.append(event)
        if len(self.memory)>self.capacity:
            del self.memory[0]

    def sample(self, batch_size):
        samples = zip(*random.sample(self.memory, batch_size))
        return map(lambda x: Variable(torch.cat(x, 0)), samples)



class VG(nn.Module):
    def __init__(self, size, nb_action):
        super(VG, self).__init__()
        hsize=200
        self.c = nn.Sequential(nn.Linear(size,hsize),nn.ReLU())
        #self.g = [nn.Sequential(nn.Linear(hsize,size),nn.ReLU(),nn.Linear(size,hsize),nn.ReLU()) for _ in range(nb_action)]
        self.g = [nn.Sequential(nn.Linear(hsize,hsize),nn.ReLU()) for _ in range(nb_action)] 
        #self.v = nn.Sequential(nn.Linear(size, hsize),nn.ReLU(),nn.Linear(hsize,1)) # best
        self.v = nn.Linear(hsize, 1)
        self.na = nb_action

    def forward(self, input):
        return torch.stack([self.v(self.g[a](self.c(input))) for a in range(self.na)])


class IA():
    def __init__(self, screen, init_action=0):
        self.state = torch.from_numpy(screen).float().unsqueeze(0)
        self.last_action = init_action
        self.batch_size = 320
        self.gamma = 0.999
        self.t = 0
        self.na = 2
        self.memory = ReplayMemory(10000)
        size = self.state.size()[1]
        #self.c = C(size)
        self.vg = VG(size, self.na)
        self.criterion = nn.MSELoss()
        #self.optimizer_c = optim.RMSprop(self.c.parameters(),lr=0.00025, eps=0.001, alpha=0.95)
        #self.optimizer_c = optim.Adam(self.vg.parameters(), lr=1e-2)
        self.optimizer_vg = optim.Adam(self.vg.parameters(), lr=1e-2)
        self.td_loss = 0
        self.c_loss = 0
        self.z_loss = 0

    def select_action(self):
        vals = self.vg(Variable(self.state, volatile=True))
        probs = F.softmax(7*vals.squeeze())
        action = probs.multinomial()
        return action.data[0]

    def learn(self,batch_state, batch_next_state, batch_reward, batch_action, batch_done):
        batch_hidden = batch_state
        batch_next_hidden = batch_next_state
        all_vals =  self.vg(batch_hidden)

        next_vals = self.vg(batch_next_hidden)
        next_vals = next_vals.max(0)[0] * (1 - batch_done)
        vals = all_vals.squeeze().gather(0, batch_action.unsqueeze(0)).squeeze()
        target_v = self.gamma*next_vals.detach() + batch_reward

        td_loss = self.criterion(vals, target_v)
        self.optimizer_vg.zero_grad()
        td_loss.backward()
        self.optimizer_vg.step()

    def update(self, screen, reward, done):
        new_state = torch.from_numpy(screen).float().unsqueeze(0)
        self.memory.push((self.state, torch.LongTensor([int(self.last_action)]),
            torch.Tensor([reward]), new_state, torch.Tensor([done])))
        self.state = new_state
        self.last_action = self.select_action()
        if len(self.memory.memory)>self.batch_size:
            batch_state, batch_action, batch_reward, batch_next_state, batch_next_done = self.memory.sample(self.batch_size)
            self.learn(batch_state, batch_next_state, batch_reward, batch_action, batch_next_done)
        self.t+=1
        return self.last_action

def mkdir(base, name):
    path = os.path.join(base, name)
    if not os.path.exists(path):
        os.makedirs(path)
    return path

if __name__=="__main__":

    work_dir = mkdir('exp', 'Cartpole-expes')
    monitor_dir = mkdir(work_dir, 'monitor')
    env = gym.make('CartPole-v0')
    env = wrappers.Monitor(env, monitor_dir, force=True)

    screen = env.reset()

    ia = IA(screen)
    action = ia.last_action
    mean = []

    for epoch in range(10000):

        done = False
        score = 0

        while not done:

            screen, reward, done, _ = env.step(action)
            action = ia.update(screen,reward, done)
            score += 1

        _ = env.reset()

        mean.append(score)
        if len(mean)>100:
            del mean[0]
        avg = sum(mean)/100.

print('epoch',epoch,"score",score,"mean",avg)

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
