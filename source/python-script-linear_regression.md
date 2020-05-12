---
title: python script linear regression (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'linear regression'

Functions in program: 
* `def rand():`

## python linear regression

Python mysql example: linear regression

```python
# TODO: shuffle dataset before gradient descent?

# import random libraries
from random import random, shuffle

# this function scales down from [0,1) to [0,0.16) in order to reduce the amount of "wobble"
def rand():
    return random()/6

# main regressor class
class Regressor(object):
    # requires us to give an interval of test values and slope and y-intercept values
    def __init__(self, m, b, interval):
        self.dataset = {}
        self.theta = [rand(), rand()]
        for x in xrange(interval[0], interval[1]):
            self.dataset[x] = (m+rand())*x+(b+rand())
        self.length = len(self.dataset)
        print("Regressor instantiated, dataset generated")

    # calling the regressor on a real number returns the y-value for that point
    def __call__(self, x):
        return self.theta[0] + self.theta[1]*x

    # loss function uses squaring for simple differentiation
    # shows numerical error in estimate
    def loss(self):
        sum = 0
        for x, y in self.dataset.iteritems():
            sum += pow(y-self(x),2)
        return sum / (2*self.length)

    # gradient descent is used to minimize the error by adjusting weights/parameters
    # uses partial derivative formula and learning rate alpha, completing given number of steps
    def gradientDescent(self, alpha=0.01, steps=1000):
        print("Beginning gradient descent")
        alpha /= self.length
        for n in xrange(steps):
            if n % (steps/4) == 0:
                print("Completed {} steps; loss: {}".format(steps/4, self.loss()))
            sum0 = 0
            sum1 = 0
            for x, y in self.dataset.iteritems():
                sum0 += self(x)-y
                sum1 += x*(self(x)-y)
            self.theta[0] -= alpha*sum0
            self.theta[1] -= alpha*sum1
        print("Gradient descent complete, parameters adjusted")

if __name__ == "__main__":
    r = Regressor(3, 4, (1,20))
    r.gradientDescent(0.01, 1000)


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
