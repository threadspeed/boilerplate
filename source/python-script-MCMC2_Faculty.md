---
title: python script MCMC2 Faculty (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'MCMC2 Faculty'

Functions in program: 
* `def gibbs_metropolis(node_list, nrounds, burn):`

Modules used in program: 
* `import random`
* `import numpy as np`

## python MCMC2 Faculty

Python mysql example: MCMC2 Faculty

```python
import numpy as np
import random
from NormalNode import NormalNode
from InvGammaNode import InvGammaNode


def gibbs_metropolis(node_list, nrounds, burn):
    for i in xrange(burn):
        for node in node_list:
            if  node.observed == False:
                node.sample()

    for i in xrange(nrounds):
        for node in node_list:
            if  node.observed == False:
                node.sample()


if __name__ == "__main__":

    datafilename = 'faculty.dat'
    nrounds = 1000
    burn = 100
    mean_candsd = 0.2
    var_candsd = 0.15
    mean_of_mean = 5.
    var_of_mean = 1./9
    alpha_of_var = 11.
    beta_of_var = 2.5

    node_list = []

    # Read in Data
    data = [float(line) for line in open(datafilename, 'r')]

    # Use point estimators from the data to come up with starting values.
    estimated_mean = np.mean(data)
    estimated_var = np.var(data)

    # Create Nodes and Links in Network
    mean_node = NormalNode(estimated_mean, name='Mean', \
                           candsd=mean_candsd, mean=mean_of_mean, var=var_of_mean)

    var_node = InvGammaNode(estimated_var, name='Variance', \
                            candsd=var_candsd, shape=alpha_of_var, scale=beta_of_var)

    data_nodes = []
    for datum in data:
        data_node = NormalNode(datum, name="Data", observed=True, mean=mean_node, var=var_node)
        data_nodes.append(data_node)
        node_list.append(data_node)

    node_list.extend([mean_node, var_node])

    # Perform simulations and plot results
    gibbs_metropolis(node_list, nrounds, burn)
    mean_node.draw_mixing(burn)
    var_node.draw_mixing(burn)
    mean_node.draw_hist(burn_in = burn, mean = mean_of_mean, var = var_of_mean)
    var_node.draw_hist(burn_in = burn, alpha = alpha_of_var, beta = beta_of_var)

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
