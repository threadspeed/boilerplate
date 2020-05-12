---
title: python script 13.1PreclassCoby (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script '13.1PreclassCoby'


Modules used in program: 
* `import matplotlib.pyplot as plt`
* `import numpy as np`
* `import random`
* `import matplotlib.pyplot as plt`
* `import numpy as np`
* `import random`

## python 13.1PreclassCoby

Python example: 13.1PreclassCoby

```python
#Random Walk
import random
import numpy as np
import matplotlib.pyplot as plt

walks = []
for walk in range(200):
    position = 0
    for step in range(30):
        if random.random() > 0.5:
            position += 1
        else:
            position -= 1
        if position == 6:
            if random.random() > .75:
                position == 5
            else:
                position == 7
    walks.append(position)

plt.hist(walks, bins = 20)
plt.show()
#variance 
print((np.var(walks)))
#mean
print((np.mean(walks)))



#Wiener Process
import random
import numpy as np
import matplotlib.pyplot as plt

ax = plt.subplot(111, projection='polar')
ax.set_rmax(1)
ax.grid(True)

walks = []
for walk in range(1000):
    r = np.random.normal(0, 2**(1/2))
    ax.scatter(random.randint(0, 360), r)

plt.show()



```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
