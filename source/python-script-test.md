---
title: python script test (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'test'


Modules used in program: 
* `import time`
* `import torch`
* `import numpy as np`
* `import gym`

## python test

Python example: test

```python
import gym
import numpy as np
import torch
from torch import nn
from model import Policy
import time

env = gym.make('PongNoFrameskip-v4')
env = gym.wrappers.Monitor(env, './tmp', video_callable=lambda ep_id: True, force=True)
env.reset()

policy = Policy()
policy.load_state_dict(torch.load('params.ckpt'))
policy.eval()

for episode in range(1):
    prev_obs = None
    obs = env.reset()
    for t in range(190000):
        #env.render()

        d_obs = policy.pre_process(obs, prev_obs)
        with torch.no_grad():
            action, action_prob = policy(d_obs, deterministic=False)
        
        prev_obs = obs
        obs, reward, done, info = env.step(policy.convert_action(action))
        
        if done:
            print('Episode %d (%d timesteps) - Reward: %.2f' % (episode, t, reward))
            break
        
        #time.sleep(0.033)

env.close()


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
