---
title: python script nbodyphysics vec2 (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'nbodyphysics vec2'

Functions in program: 
* `def random_galaxy(`
* `def move(galaxy, dt):`
* `def calc_force(amass, aposition, bmass, bposition, dt):`

Modules used in program: 
* `import numpy as np`

## python nbodyphysics vec2

Python example: nbodyphysics vec2

```python
#!/usr/bin/python
# -*- coding: utf-8 -*-

"""NBody in N^2 complexity
Note that we are using only Newtonian forces and do not consider relativity
Neither do we consider collisions between stars
Thus some of our stars will accelerate to speeds beyond c
This is done to keep the simulation simple enough for teaching purposes

All the work is done in the calc_force, move and random_galaxy functions.
To vectorize the code these are the functions to transform.
"""
import numpy as np

# By using the solar-mass as the mass unit and years as the standard time-unit
# the gravitational constant becomes 1

G = 1.0


def calc_force(amass, aposition, bmass, bposition, dt):
    """Calculate forces between bodies
    F = ((G m_a m_b)/r^2)*((x_b-x_a)/r)
    """
    dpos = (bposition - aposition[:,np.newaxis])

    r = np.sum((dpos ** 2),axis=0) ** 0.5
    dspeed = G * amass * bmass / r ** 2 * (dpos / r) / amass * dt
    return np.sum(dspeed,axis=1)


def move(galaxy, dt):
    """Move the bodies
    first find forces and change velocity and then move positions
    """

    # unpack galaxy into its components
    (mass,position,speed) = galaxy

    n = len(mass)
    
    # compute speed
    for i in xrange(n):
        all_others = np.hstack((np.arange(i),np.arange(i+1,n)))
        speed[:,i] += calc_force(mass[i], position[:,i], mass[all_others], position[:,all_others], dt)

    # advance position
    for i in xrange(n):
        position[:,i] += speed[:,i] * dt
    

def random_galaxy(
    x_max,
    y_max,
    z_max,
    n,
    ):
    """Generate a galaxy of random bodies"""

    max_mass = 40.0  # Best guess of maximum known star

    # We let all bodies stand still initially

    # initialize mass
    mass = np.random.random(n) * np.random.randint(1, max_mass, n) / (4 * np.pi ** 2)

    # initialize position
    position = np.zeros((3,n))
    position[0] = np.random.random(n)*2*x_max-x_max
    position[1] = np.random.random(n)*2*y_max-y_max
    position[2] = np.random.random()*2*z_max-z_max

    # initialize speed
    speed = np.zeros((3,n))

    return (mass,position,speed)


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
