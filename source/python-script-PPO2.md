---
title: python script PPO2 (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'PPO2'

Functions in program: 
* `def learn_model():`
* `def make_env(env_id, rank=0, seed=0):`
* `def linear_schedule(initial_value):`

Modules used in program: 
* `import numpy as np`
* `import os`
* `import gym`

## python PPO2

Python mysql example: PPO2

```python
import gym

from stable_baselines.common.policies import MlpPolicy
from stable_baselines.common.vec_env import SubprocVecEnv, DummyVecEnv, VecNormalize
from stable_baselines.bench import Monitor
from stable_baselines import PPO2
import os
import numpy as np
from stable_baselines.common import set_global_seeds

best_mean_reward, n_steps = -np.inf, 0


# ENV_NAME = 'Pendulum-v0'
# ENV_NAME = 'BipedalWalker-v2'
ENV_NAME = 'Acrobot-v1'
# ENV_NAME = 'LunarLander-v2'
# ENV_NAME = 'BipedalWalkerHardcore-v2'
# ENV_NAME = 'MountainCarContinuous-v0'
# ENV_NAME = 'MountainCar-v0'
log_dir = "./logs/"
os.makedirs(log_dir, exist_ok=True)
model_file = log_dir + ENV_NAME + '_best_model_2.pkl'
env_file = log_dir  # + ENV_NAME + '.env'
normalize = False
# normalize = True  # 到底什么时候需要？


def linear_schedule(initial_value):
    if isinstance(initial_value, str):
        initial_value = float(initial_value)

    def func(progress):
        return progress * initial_value

    return func


def make_env(env_id, rank=0, seed=0):
    def _init():
        set_global_seeds(seed + rank)
        env = gym.make(env_id)
        env.seed(seed + rank)
        env = Monitor(env, os.path.join(log_dir, str(rank)), allow_early_resets=True)
        return env

    return _init


def learn_model():
    def callback(_locals, _globals):
        print("Saving model...")
        _locals['self'].save(model_file)
        if normalize:
            print("Saving running average...")
            env.save_running_average(env_file)
        return True

    env = SubprocVecEnv([make_env(ENV_NAME, i, 0) for i in range(16)])
    if normalize:
        print("Using VecNormalize...")
        env = VecNormalize(env)

    args = dict(
        n_steps=2048,
        nminibatches=32,
        noptepochs=10,
        verbose=1,
        cliprange=linear_schedule(0.2),
        learning_rate=linear_schedule(2.5e-4),
        ent_coef=0.001,
    )

    if os.path.exists(model_file):
        if normalize:
            env.load_running_average(env_file)
            print("Loaded running average...")
        model = PPO2.load(
            model_file,
            env,
            **args,
        )
        print("Loaded file...", model_file)
        model.learn(total_timesteps=900000000, callback=callback)
    else:
        model = PPO2(
           MlpPolicy,
           env,
           **args,
        )
        model.learn(total_timesteps=900000000, callback=callback)


learn_model()


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
