---
title: python script untitled ex048 (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'untitled ex048'


Modules used in program: 
* `import  time`
* `import  random`

## python untitled ex048

Python mysql example: untitled ex048

```python
import  random
import  time

l= random.randint(0,10)
print("Sou seu computador...")
time.sleep(1)
print("Você consegue adivinhar um número de 0 a 10 ?")
time.sleep(1)
n = int(input("QUAL SEU CHUTE ? "))
while not n==l:
    if n >= 11:
        print("Preste atenção eu pensei em um número de 0 a 10.")
    n = int(input("Você errou tente novamente: "))
print(l)
print("Parabéns você ACERTOU !")



```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
