---
title: python script Furtune teller (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'Furtune teller'


Modules used in program: 
* `import random`

## python Furtune teller

Python example: Furtune teller

```python
# import random from library
import random

# List of respones to questions asked
respones = ["Ask again", "Is that really a question", "Good question, you tell me",
            "I would look for another, better furtune teller", "Ask mom",
            "Ask Later", "Today is not a good day to  ask, come back later",
            "Only if I had a brain.", "I don't know", "I really don't know anything", "Hey! Look a squirrel",
            "Ask dad", "look up", "42", "For $5, I can tell you,"]

# reads in input from user
answer = raw_input("What is your questtion? \n")

# prints out random respones from list
print(random.choice(respones))

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
