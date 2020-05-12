---
title: python script hangman (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'hangman'


Modules used in program: 
* `import sys`
* `import random`

## python hangman

Python example: hangman

```python
import random
import sys

name = input('What is your name?')

print('Hello', name, 'lets begin!')

answerlist = ['dupa', 'dupa2']
#Można to random intem zrobić 
answer = answerlist[random.randint(0, len(answerlist)-1)]

display = []

display.extend(answer)
for i, _ in enumerate(display):
    print(i)
    display[i] = '_'

attempts = 10
while attempts > 0:
    print('')
    print("DISPLAY : ", display)
    print('Left ' + str(attempts) + ' guesses')
    print('')
    print(' '.join(display))
    print(' ')
    
    print('Type a letter')
    letter = input()
    if letter in answer:
        for i in range(len(display)):
            if (answer[i] == letter):
                display[i] = letter
                print(''.join(map(str, display)))
            if ''.join(map(str, display)) == answer:
                print('')
                print('Left' + str(attempts) + 'guesses')
                print('')
                print(' '.join(display))
                print(' ')
                print('Congratulations', name, 'you won!')
                sys.exit(0)
                
                

    else:
        attempts -= 1
    



```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
