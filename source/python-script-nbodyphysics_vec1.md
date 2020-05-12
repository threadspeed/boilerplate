---
title: python script nbodyphysics vec1 (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'nbodyphysics vec1'

Functions in program: 
* `def random_galaxy(`
* `def move(galaxy, dt):`
* `def calc_force(amass, aposition, bmass, bposition, dt):`

Modules used in program: 
* `import numpy as np`

## python nbodyphysics vec1

Python example: nbodyphysics vec1

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

    # get data from `galaxy`
    position = galaxy[['x','y','z']].view(('f8',3)).T
    speed = galaxy[['vx','vy','vz']].view(('f8',3)).T

    n = len(galaxy)

    # compute speed
    for i in xrange(n):
        # get indices of all other galaxies than the first one (`i`)
        all_others = np.hstack((np.arange(i),np.arange(i+1,n)))
        # compute the total speed contribution from all other galaxies
        speed[:,i] += calc_force(galaxy['m'][i], position[:,i], galaxy['m'][all_others], position[:,all_others], dt)
    
    # advance position
    for i in xrange(n):
        position[:,i] += speed[:,i] * dt

    # copy data back into `galaxy`
    # perhaps, this step becomes obsolete in a later version of NumPy
    for k,field in enumerate(['x','y','z']):
        galaxy[field] = position[k]
        galaxy['v'+field] = speed[k]


def random_galaxy(
    x_max,
    y_max,
    z_max,
    n,
    ):
    """Generate a galaxy of random bodies
    
    Changed here compared to the sequential version
    -----------------------------------------------
    `galaxy` is now a NumPy record array instead of a list of dictionaries

    """

    max_mass = 40.0  # Best guess of maximum known star


    # get the fields (i.e all the galaxy attributes)
    fields = ['m','x','y','z','vx','vy','vz']

    # make a custom data type for the record array
    galaxydtype = dict(names=fields,formats=['f8']*len(fields))

    # initialize the array with zeros
    galaxy = np.zeros(n,dtype=galaxydtype)

    # We let all bodies stand still initially
    # --> nothing to do here because galaxy['vx'] etc. already is 0

    # initialize mass
    galaxy['m'] = np.random.random(n) * np.random.randint(1, max_mass, n) / (4 * np.pi ** 2)

    # initialize position
    galaxy['x'] = np.random.random(n)*2*x_max-x_max
    galaxy['y'] = np.random.random(n)*2*y_max-y_max
    galaxy['z'] = np.random.random(n)*2*z_max-z_max

    return galaxy


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
