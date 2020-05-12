---
title: python script bulls-cows (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'bulls-cows'


Modules used in program: 
* `import random`
* `import math`
* `import numpy as np`
* `import gym`

## python bulls-cows

Python example: bulls-cows

```python
import gym
from gym import spaces
import numpy as np
import math
import random
from gym.utils import seeding


class BullsCowsEnv(gym.Env):
    def __init__(self):
        super(BullsCowsEnv, self).__init__()
        self.action_space = spaces.Box(
            low=np.array([0, 0, 0, 0]),
            high=np.array([9, 9, 9, 9]),
            dtype=np.int,
        )
        self.observation_space = spaces.Box(
            low=0,
            high=9,
            shape=(10, 8),
            dtype=np.uint,
        )
        self.guess_count = 0
        self.state = []
        self.solution = []
        self.old_guess = []
        self.reset()
        self.max_right_count = 0
        self.max_position_count = 0
        # self.seed()

    def step(self, action):
        assert self.action_space.contains(action)
        action = [int(round(x)) for x in action]
        done = False
        reward = -1
        if len(action) > len(set(action)) or np.array_equal(action, self.old_guess):
            done = True
            reward = -100
        else:
            prompt = self.get_prompt(action)
            self.state[self.guess_count] = np.concatenate((
                action, prompt
            ))
            right_count = prompt[0]
            position_count = prompt[2]
            reward += (right_count - self.max_right_count) * 10
            reward += (right_count - self.max_position_count) * 3
            self.max_right_count = max(right_count, self.max_right_count)
            self.max_position_count = max(position_count, self.max_position_count)
            if prompt[0] == 4:
                reward = 100
                done = True
        self.old_guess = action
        self.guess_count += 1
        if self.guess_count > 9:
            done = True
        return self.state, reward, done, {}

    def get_prompt(self, guess):
        right_count = 0
        position_count = 0
        for i, num in enumerate(guess):
            if guess[i] == self.solution[i]:
                right_count += 1
            if num in self.solution:
                position_count += 1
        return np.array([right_count, 1, position_count - right_count, 2])

    def seed(self, seed=None):
        self.np_random, seed = seeding.np_random(seed)
        return [seed]

    def reset(self):
        self.guess_count = 0
        self.solution = self.new_solution()
        self.old_guess = np.zeros(shape=[1, 4])
        self.max_right_count = 0
        self.max_position_count = 0
        self.state = self.init_state()
        return self.step(self.new_solution())[0]

    def init_state(self):
        # return np.random.randint(0, 9, size=(10, 8))
        return np.zeros(shape=(10, 8), dtype=np.uint)

    def new_solution(self):
        solution = np.random.randint(0, 9, size=4)
        while len(solution) != len(set(solution)):
            solution = np.random.randint(0, 9, size=4)
        return solution

    def render(self, mode='human', close=False):
        print(self.solution)
        for i, row in enumerate(self.state):
            s = ""
            for j, num in enumerate(row):
                num = int(num)
                if j <= 3:
                    s += str(num)
                else:
                    if j % 2 == 0:
                        s += str(num)
                    else:
                        if num == 1:
                            s += "A"
                        elif num == 2:
                            s += "B"
                        else:
                            s += "_"
            print(s)


if __name__ == '__main__':
    env = BullsCowsEnv()
    action = env.action_space.sample()
    print(action)
    obs, reward, done, _ = env.step(action)
    env.render()


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
