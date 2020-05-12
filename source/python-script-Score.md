---
title: python script Score (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'Score'

Functions in program: 
* `def add_score(difficulty):`

Modules used in program: 
* `import Utils`
* `import io`

## python Score

Python example: Score

```python
import io
import Utils


def add_score(difficulty):
    try:
        file = open(Utils.SCORES_FILE_NAME(), 'r+')
        try:
            score = int(file.read())
        except:
            score = 0
        score += int(difficulty)
        print('current score ' + str(score))
        file.seek(0)
        file.write(str(score))
        file.truncate()
    except:
        file = open(Utils.SCORES_FILE_NAME(), 'w+')
        print('current score 0')
        if not difficulty:
            file.write('0')
        else:
            file.write(difficulty)
    finally:
        file.close()

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
