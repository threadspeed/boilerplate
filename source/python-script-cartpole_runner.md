---
title: python script cartpole runner (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'cartpole runner'


Modules used in program: 
* `import numpy as np`
* `import random`
* `import gym`

## python cartpole runner

Python mysql example: cartpole runner

```python
# import the gym stuff
import gym
# import other stuff
import random
import numpy as np
# import own classes
from deepq import DeepQ

env = gym.make('CartPole-v0')

epochs = 3000
steps = 100000
updateTargetNetwork = 5000
initialUpdateTargetNetwork = 1000
explorationRate = 1
minibatch_size = 128
learnStart = 128
learningRate = 0.00025
discountFactor = 0.99
memorySize = 1000000

last100Scores = [0] * 100
last100ScoresIndex = 0
last100Filled = False

deepQ = DeepQ(4, 2, memorySize, discountFactor, learningRate, learnStart)
# deepQ.initNetworks([24, 16, 12, 8])
# deepQ.initNetworks([6])
deepQ.initNetworks([30, 30, 30])

stepCounter = 0

# number of reruns
for epoch in xrange(epochs):
    observation = env.reset()
    print(explorationRate)
    # number of timesteps
    for t in xrange(steps):
        # env.render()
        qValues = deepQ.getQValues(observation)
        
        action = deepQ.selectAction(qValues, explorationRate)
        
        newObservation, reward, done, info = env.step(action)
        
        deepQ.addMemory(observation, action, reward, newObservation, done)

        if stepCounter >= learnStart:
            deepQ.learnOnMiniBatch(minibatch_size)

        observation = newObservation

        if done:
            last100Scores[last100ScoresIndex] = t
            last100ScoresIndex += 1
            if last100ScoresIndex >= 100:
                last100Filled = True
                last100ScoresIndex = 0
            print(last100Filled)
            if not last100Filled:
                print("Episode ",epoch," finished after {} timesteps".format(t+1))
            else :
                print("Episode ",epoch," finished after {} timesteps".format(t+1)," last 100 average: ",(sum(last100Scores)/len(last100Scores)))
            break

        stepCounter += 1
        if stepCounter < updateTargetNetwork:
            currentUpdateTargetNetwork = initialUpdateTargetNetwork
        else: 
            currentUpdateTargetNetwork = updateTargetNetwork
        if stepCounter % currentUpdateTargetNetwork == 0:
            deepQ.updateTargetNetwork()
            print("updating target network")

    explorationRate *= 0.995
    # explorationRate -= (2.0/epochs)
    explorationRate = max (0.05, explorationRate)

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
