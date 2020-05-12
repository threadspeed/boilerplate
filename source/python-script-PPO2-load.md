---
title: python script PPO2-load (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'PPO2-load'

Functions in program: 
* `def load_model():`

Modules used in program: 
* `import time`
* `import numpy as np`
* `import os`
* `import gym`

## python PPO2-load

Python example: PPO2-load

```python
import gym

from stable_baselines.common.policies import MlpPolicy
from stable_baselines.common.vec_env import SubprocVecEnv, DummyVecEnv
from stable_baselines.bench import Monitor
from stable_baselines import PPO2
from stable_baselines.results_plotter import load_results, ts2xy
import os
import numpy as np
import time
from stable_baselines.common.vec_env import VecNormalize, VecFrameStack

# ENV_NAME = 'Pendulum-v0'
# ENV_NAME = 'BipedalWalker-v2'
# ENV_NAME = 'Acrobot-v1'
# ENV_NAME = 'LunarLander-v2'
# ENV_NAME = 'BipedalWalkerHardcore-v2'
ENV_NAME = 'MountainCarContinuous-v0'
# ENV_NAME = 'MountainCar-v0'
# log_dir = "./rl-baselines-zoo/logs/ppo2"
log_dir = "./logs/"
model_file = log_dir + ENV_NAME + '_best_model_2.pkl'
env_file = log_dir  # + ENV_NAME + '.env'
os.makedirs(log_dir, exist_ok=True)
# normalize = False
normalize = True

# model_file = log_dir + "/" + ENV_NAME + "_2/" + ENV_NAME + '.pkl'
# env_file = log_dir + "/" + ENV_NAME + "_2/" + ENV_NAME

print(model_file, env_file)

env = gym.make(ENV_NAME)
env = DummyVecEnv([lambda: env])
if normalize:
    env = VecNormalize(env)


def load_model():
    while True:
        obs = env.reset()
        print("Loading saved model...")
        model = PPO2.load(model_file)
        if normalize:
            print("Loading running averaing...")
            env.load_running_average(env_file)
        n = 0
        while n < 2000:
            action, _states = model.predict(obs)
            obs, rewards, dones, info = env.step(action)
            env.render()
            if dones:
                print("DONE==>")
                break
            n += 1
        time.sleep(5)


load_model()


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
