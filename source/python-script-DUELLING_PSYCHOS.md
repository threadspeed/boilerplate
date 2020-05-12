---
title: python script DUELLING PSYCHOS (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'DUELLING PSYCHOS'


Modules used in program: 
* `import time`
* `import random`

## python DUELLING PSYCHOS

Python mysql example: DUELLING PSYCHOS

```python
import random
import time

ls1 = [' is it raining? ', ' what have I become? ', ' because ', ' since I know that answer ', ' because you asked me to ', ' - in the middle of it all - ', ' verily, verily, it was thus ', ' predicting the future ', ' raining hard, is it? ', ' data terrain built from constructivistic principles ' ]

ls2 = [' in the morning we saw a white mare ', ' poetic license is what I am told ', ' because ', ' and because ', ' always surely ', 'almost gigantesque ', ' almost certainly ', ' an infinitesimal change ', ' because the differential ', ' all the while ', ' is threatening our documentary heritage ', ' historiotherapeusis & historiopathogenesis ']

"""
>>> import random
>>> import time
>>> ls1 = [' is it raining? ', ' what have I become? ', ' because ', ' since I know that answer ', ' because you asked me to ', ' - in the middle of it all - ', ' verily, verily, it was thus ', ' predicting the future ', ' raining hard, is it? ', ' data terrain built from constructivistic principles ' ]
>>> type(ls1)
<type 'list'>
>>> len(ls1)
10
>>> ls1[random.randint(0,9)]
' verily, verily, it was thus '
>>> ls1[random.randint(0,9)]
' what have I become? '
>>> ls1[random.randint(0,9)]
' is it raining? '
>>> for i in ls1:
	print(ls1[random.randint(0,9)])

	
 because 
 raining hard, is it? 
 what have I become? 
 since I know that answer 
 since I know that answer 
 verily, verily, it was thus 
 because 
 because you asked me to 
 data terrain built from constructivistic principles 
 what have I become? 

>>> def send_sig(ls):
	return ls1[random.randint(0,9)]

>>> send_sig(ls1)
' because '
>>> send_sig(ls1)
' because '
>>> send_sig(ls1)
' verily, verily, it was thus '
>>> send_sig(ls1)
' data terrain built from constructivistic principles '
>>> send_sig(ls1)
'because you asked me to '
>>> send_sig(ls1)
' raining hard, is it? '

>>> ls2 = [' in the morning we saw a white mare ', ' poetic license is what I am told ', ' because ', ' and because ', ' always surely ', 'almost gigantesque ', ' almost certainly ', ' an infinitesimal change ', ' because the differential ', ' all the while ', ' is threatening our documentary heritage ', ' historiotherapeusis & historiopathogenesis ']
>>> type(ls2)
<type 'list'>
>>> len(ls2)
12
>>> def send_sig(ls):
	return ls[random.randrange(len(ls))]

>>> send_sig(ls1)
' verily, verily, it was thus '
>>> send_sig(ls2)
' all the while '
>>> send_sig(ls1)
' is it raining? '
>>> send_sig(ls1)
' - in the middle of it all - '
>>> send_sig(ls1)
' data terrain built from constructivistic principles '
>>> send_sig(ls1)
' verily, verily, it was thus '
>>> send_sig(ls1)
' predicting the future '
>>> send_sig(ls2)
' and because '
>>> send_sig(ls2)
' is threatening our documentary heritage '
>>> send_sig(ls2)
'almost gigantesque '
>>> send_sig(ls2)
' because '
>>> send_sig(ls2)
' and because '

>>> for i in range(10):
	print(send_sig(ls1+ls2))

	
 historiotherapeusis & historiopathogenesis 
because you asked me to 
 raining hard, is it? 
almost gigantesque 
 an infinitesimal change 
 because 
 an infinitesimal change 
 - in the middle of it all - 
 raining hard, is it? 
 - in the middle of it all - 

"""

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
