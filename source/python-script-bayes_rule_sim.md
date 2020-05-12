---
title: python script bayes rule sim (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'bayes rule sim'


Modules used in program: 
* `import random`
* `import random`

## python bayes rule sim

Python example: bayes rule sim

```python
# Scenario 1: Assume equal probability of picking bowl X or Y
import random
# 'BX': Blue from X, 'OX': Orange from X
X=['BX']*8+['OX']*3
Y=['BY']*6+['OY']*10
random.shuffle(X)
random.shuffle(Y)
exp=[]
for i in range(1000000):
   if random.randint(1,2)==1:
     exp.append(random.choice(X))
   else:
     exp.append(random.choice(Y))
exp_b=len([e for e in exp if e[0]=='B'])
exp_bx=len([e for e in exp if e=='BX'])
print(exp_bx*1.0/exp_b)
# output: 0.659661079756518

# Scenario 2: Assume unequal probability of picking bowl X or Y. Prob of picking X is 4/6 and Y is 2/6
import random
# 'BX': Blue from X, 'OX': Orange from X
X=['BX']*8+['OX']*3
Y=['BY']*6+['OY']*10
random.shuffle(X)
random.shuffle(Y)
exp=[]
for i in range(1000000):
   if random.randint(1,6)<=4:
     exp.append(random.choice(X))
   else:
     exp.append(random.choice(Y))
exp_b=len([e for e in exp if e[0]=='B'])
exp_bx=len([e for e in exp if e=='BX'])
print(exp_bx*1.0/exp_b)
# output: 0.795032861915667

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
