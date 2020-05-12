---
title: python script frequency (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'frequency'

Functions in program: 
* `def generateFrequencies(max,trials):`

Modules used in program: 
* `import random`

## python frequency

Python example: frequency

```python
#import random module
import random
max=10
#array holding the frequencies of each generated number
freqs=[]
#set all frequencies to zero
for i in range(0,max):
  freqs+=[0]
n=100000
#generate n random numbers between 0 and max (not inclusive)
for i in range(0,n):
  freqs[random.randint(0,max-1)]+=1
#relative frequencies
relFreqs=[]
for i in range(0,len(freqs)):
  #cast int to float and put it in array
  relFreqs+=[float(freqs[i])/n]
#same code but as a function
def generateFrequencies(max,trials):
  freqs=[]
#set all frequencies to zero
  for i in range(0,max):
	  freqs+=[0]
  for i in range(0,trials):
	  freqs[random.randint(0,max-1)]+=1
  #make it relative
  relFreqs=[]
  for i in range(0,len(freqs)):
    #cast int to float and put it in array
    relFreqs+=[float(freqs[i])/trials]
  return relFreqs



```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
