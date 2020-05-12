---
title: python script jump-walker (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'jump-walker'


Modules used in program: 
* `import random`
* `import math`
* `import numpy as np`
* `import gym`

## python jump-walker

Python mysql example: jump-walker

```python
import gym
from gym import spaces
import numpy as np
import math
import random
from gym.utils import seeding

LEN_OF_PACE = 20


class JumpWalkerEnv(gym.Env):
    """Custom Environment that follows gym interface"""
    metadata = {'render.modes': ['human']}

    def __init__(self):
        super(JumpWalkerEnv, self).__init__()
        # 0 left 1 right 2 jump
        self.action_space = spaces.Discrete(3)
        # 0100010002
        self.observation_space = spaces.Box(
            low=np.array([0 for _ in range(LEN_OF_PACE)]),
            high=np.array([3 for _ in range(LEN_OF_PACE)]),
            dtype=np.uint,
        )
        self.current_pos = 0
        self.state = self.make_map()
        self.seed()

    def step(self, action):
        reward = -1
        self.state[self.current_pos] = 0
        if action == 0:  # left
            self.current_pos -= 1
        elif action == 1:  # right
            self.current_pos += 1
        else:  # jump
            self.current_pos += 2
        current_pos = self.current_pos

        done = False
        if current_pos < 0 or current_pos >= LEN_OF_PACE or self.state[current_pos] == 1:
            reward = -100
            done = True
        elif current_pos == LEN_OF_PACE - 1:
            reward = 100
            done = True
        else:
            self.state[current_pos] = 2

        return self.state, reward, done, {}

    def reset(self):
        self.current_pos = 0
        self.state = self.make_map()
        return self.state

    def make_map(self):
        pace_map = []
        hole_count = random.randint(1, (LEN_OF_PACE - 2) / 2)
        for i in range(LEN_OF_PACE):
            if i == 0:
                pace_map.append(2)
            elif i == LEN_OF_PACE - 1:
                pace_map.append(0)
            elif hole_count > 0 and random.randint(0, 100) % 2 is 0 and pace_map[i - 1] != 1:
                pace_map.append(1)
                hole_count -= 1
            else:
                pace_map.append(0)
        return np.array(pace_map)

    def seed(self, seed=None):
        self.np_random, seed = seeding.np_random(seed)
        return [seed]

    def render(self, mode='human', close=False):
        plot = ""
        for n in self.state:
            if n == 0:
                plot += "_"
            elif n == 1:
                plot += "o"
            else:
                plot += "v"
        print(plot)


ACTIONS_NAME = ["LEFT", "RIGHT", "JUMP"]

if __name__ == "__main__":
    env = JumpWalkerEnv()

    while True:
        ok = False
        env.reset()
        print("TRY==============================")
        env.render()
        while True:
            action = env.action_space.sample()
            action_name = "LEFT"
            print("Action -> ", ACTIONS_NAME[action])
            obs, done, reward, _ = env.step(action)
            print("Reward -> ", reward)
            if reward == 100:
                ok = True
            env.render()
            if done:
                break
        if ok:
            break


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
