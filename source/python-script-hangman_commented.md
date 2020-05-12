---
title: python script hangman commented (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'hangman commented'


Modules used in program: 
* `import random`

## python hangman commented

Python mysql example: hangman commented

```python
import random
 
name = input('What is your name?')
 
print('Hello', name, 'lets begin!')
 
answerlist = ['lion', 'giraffe', 'strawberry', 'lemon']
random.shuffle(answerlist)
answer = list(answerlist[0])
#wystarczyło by random intem wybrać odpowiedź, ale chuj tam
# np answer = list(answerlist[random.randint(0,len(answerlist))])
display = []
 
display.extend(answer)

for i in range(len(display)):
    display[i] = '_'
 
attempts = 10
while attempts > 0:
    print('')
    print('Left ' + str(attempts) + ' guesses')
    print('')
    print(' '.join(display))
    print(' ')
 
    print('Type a letter')
    letter = input()
 
    if letter in display:
        for i in range(len(display)):
            # tutaj jest pokićkane bo display ma same _, a odpowiedź ma odpowiedź 
            # więc answer[i] == letter
            if (display[i] == letter):
                # tutaj dodawać powinien literkę do displaya nie do odpowiedzi 
                answer[i] = letter
            #warunek zwycięztwa, łączy stringa answer czy jest taki sam jak lista display, a powinno być na odwrót 
            #i złączyć całą tablice do stringa i porównać z odpowiedzią 
            if ''.join(map(str, answer)) == display:
                print('')
                print('Left' + str(attempts) + 'guesses')
                print('')
                print(' '.join(display))
                print(' ')
                print('Congratulations', name, 'you won!')
                break
 
    else:
        attempts -= 1

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
