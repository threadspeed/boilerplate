---
title: python script randomWord (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'randomWord'


Modules used in program: 
* `import random;random.choice(open("/usr/share/dict/words").readlines())[:-1]`
* `import random`

## python randomWord

Python example: randomWord

```python
with open("/usr/share/dict/words") as f:
    dict = [word.rstrip('\n') for word in f]

import random
print(random.choice(dict))

# or, a one-liner
random.choice(open("/usr/share/dict/words").readlines())[:-1]

# in an isolated environment:
import random;random.choice(open("/usr/share/dict/words").readlines())[:-1]

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
