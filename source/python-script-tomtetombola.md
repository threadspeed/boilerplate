---
title: python script tomtetombola (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'tomtetombola'


Modules used in program: 
* `import random`

## python tomtetombola

Python mysql example: tomtetombola

```python
import random

fler = True
tomtarInput=[]
while fler == True:
  tomtarInput.append(input('Mata in ett namn: '))
  if input('Vill du mata in ett namn till? (j/n): ') == 'j':
    fler = True
  else:
    if len(tomtarInput)%2==0:
      break
    else:
      print('Det måste vara ett jämt antal tomtar!')
      fler = True

kontroll = True


while kontroll == True:

  tomtar = list(tomtarInput)
  mottagare = list(tomtarInput)
  mottagareSlump = []
  resultat = []
  
  for i in range (len(mottagare)):
    temp = random.choice(mottagare)
    mottagareSlump.append(temp)
    mottagare.remove(temp)
  
  for i in range (len(mottagareSlump)):
    if tomtar[i] == mottagareSlump[i]:
      kontroll = True
      break
    else:
      kontroll = False
    

    
print('')
print('+++++++++++++++++++++++++++++++++++++++++')
for i in range (len(mottagareSlump)):
  print((tomtar[i] + ' är hemlig tomte åt ' + mottagareSlump[i]))
print('+++++++++++++++++++++++++++++++++++++++++') 

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
