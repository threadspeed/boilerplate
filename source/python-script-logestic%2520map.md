---
title: python script logestic%2520map (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'logestic%2520map'


Modules used in program: 
* `import math`
* `import numpy as np`
* `import matplotlib as plt`
* `import random`

## python logestic%2520map

Python example: logestic%2520map

```python
import random
import matplotlib as plt
import numpy as np
import math
x=np.zeros(100)
x[0]=0.1
y=list(range(0, 100))
mu=3.8
i=0
while(i<99):
        x[i+1]=mu*x[i]*(1-x[i])
        i+=1
print((x))
np.savetxt("logestic1.csv", x, delimiter=",")
plt.plot(y,x)
plt.show()

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
