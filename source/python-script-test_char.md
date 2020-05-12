---
title: python script test char (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'test char'

Functions in program: 
* `def get_char():`
* `def ask_user(char, tries):`

Modules used in program: 
* `import sensitive`
* `import time`
* `import random`

## python test char

Python mysql example: test char

```python
import random
import time
import sensitive
# just pick a letter and quiz it.

avg = 0

tries = 0

hard = ['1', '3', '4', '8']
num_right = 0

def ask_user(char, tries):
    global num_right
    input_num = input(char + '? : ')
    if sensitive.the_hash[char] == int(input_num):
        print('yes')
        num_right += 1
        if (tries < 5) and (tries > 0):
            tries += 1
            ask_user(char, tries)
    else:
        print('no, ' + char + ' is ' + str(sensitive.the_hash[char]))
        # sys.exit("Bye!")
        ask_user(char, 1)


def get_char():
    return chr(random.randint(ord('a'), ord('z')))

start = time.time()
while num_right < 50:
    char = get_char()
    ask_user(char, 0)

end = time.time()
print('finished in ' + str(end - start))

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
