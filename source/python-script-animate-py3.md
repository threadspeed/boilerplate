---
title: python script animate-py3 (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'animate-py3'

Functions in program: 
* `def cesar(text, key=1, reverse=False):`
* `def animate_forever(chars='|/-\\', timing=0.1):`
* `def animate(`

Modules used in program: 
* `import string`
* `import random`
* `import time`
* `import sys`

## python animate-py3

Python mysql example: animate-py3

```python

import sys
import time
import random
import string


def animate(
        text, timing=0.05, shift=5, reverse=False, 
        decrypt=False, decrypt_key=1, chars=string.printable[:74]):
    if reverse:
        text = ''.join(reversed(text))
    if decrypt:
        text = ''.join([chr(ord(x) - decrypt_key) for x in text])
    for c in text:
        shuffle = list(chars.lower() if c.islower() else chars)
        random.shuffle(shuffle)
        shuffle = shuffle[:random.randint(shift // 2, shift * 2)]
        shuffle.append(c)
        spinner = (x for x in ''.join(shuffle))
        for _ in range(len(shuffle) - 1):
            sys.stdout.write(next(spinner))
            sys.stdout.flush()
            time.sleep(timing)
            sys.stdout.write('\b')
        sys.stdout.write(next(spinner))


def animate_forever(chars='|/-\\', timing=0.1):
    for c in itertools.cycle(list(chars)):
        c = str(c)
        sys.stdout.write(c)
        sys.stdout.flush()
        time.sleep(timing)
        sys.stdout.write('\b' * len(c))


def cesar(text, key=1, reverse=False):
    text = ''.join([chr(ord(x) + key) for x in text])
    return ''.join(reversed(text)) if reverse else text


secret_str = cesar('TESTE', reverse=True)
animate(secret_str, reverse=True, decrypt=True)

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
