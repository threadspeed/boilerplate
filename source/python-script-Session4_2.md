---
title: python script Session4 2 (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'Session4 2'


Modules used in program: 
* `import random`
* `import random`
* `import matplotlib.pyplot as plt`
* `import numpy as np`
* `import matplotlib.pyplot as plt`
* `import numpy as np`
* `import numpy as np`
* `import numpy as np`

## python Session4 2

Python example: Session4 2

```python
#Hiring problem: 

#Question 1 + 2
import numpy as np

best = 0
for i in range(1000): #1000 interviews
    best = numpy.random.uniform(0, 1) #for each interview, the quality of the candidate is a random number between 0 and 1.
    if new > best: #if the candidate is beter than the currennt accepted candidate 
        best = new #the new candidate is accepted
        
        
#Question 2
import numpy as np

best = 0
acceptance = 0

for i in range(100000):
    new = np.random.uniform(0, 1)
    if new > best:
        best = new
        acceptance += 1 #count the number of applicants accepted

print('The probability is: ', acceptance/100000*100) #total number of people accepted over the total applicants.

#Question 3
import numpy as np
import matplotlib.pyplot as plt


import numpy as np
import matplotlib.pyplot as plt
import random


x = [] #The number of applicants
y = [] #The number of accepted applicants

for i in range(0, 100):
    x.append(i) #create the list of number of applicants
    best = 0 #the starting point to compare 
    acceptance = 0
    for a in range(1000): #for each value of number of applicants, repeat 1000 times, to find the total number of accepted applicants
      for _ in range(i): #interview each applicant in the pool of i
          new = random.random(0, 1) #the quality of the applicant
          if new > best:
              best = new
              acceptance += 1
    y.append(acceptance/1000) #add the average value into y.

plt.plot(x, y)
plt.show()

#Question 4
Y =
X = 
Z =
M = 
best = 0
cost = 0
while total_work < M:
    cost += Y #each day of interview, we have to pay the interview fee
    new = np.random.uniform(0, 1)
    if new > best: #the new applicant is beter than the old one. 
        best = new #hire the applicant
        cost += Z #fire the old employee
        total_work += new #add the work from the new applicant
    if new <= best: #the old employee is still better
        total_work += best #the old employee contribute to the total_work
print('The total cost is', cost)     
    
#Hat-problem
import random
y = []
x = []
for N in range(1, 100):
    temp_sum = 0
    x.append(N)
    for _ in range(10):
        correct = 0
        people = range(N)
        hat = []
        for a in range(N):
            hat.append(a)
        random.shuffle(hat)
        
        for i in range(N):
            if hat[i] == people[i]:
                correct += 1
        temp_sum += correct

    y.append(temp_sum/10)
plt.plot(x, y)
plt.show()


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
