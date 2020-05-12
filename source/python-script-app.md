---
title: python script app (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'app'

Functions in program: 
* `def index():`

Modules used in program: 
* `import random`
* `import random`

## python app

Python example: app

```python
#without JS
import random
from flask import render_template

import random
from flask import render_template


@app.route('/', methods=['GET'])
def index():
    """
    Route that maps to the main index page.
    """
    random_str = ''.join(random.choices('abcedfg', k=5))
    robot = 'https://robohash.org/{}'.format(random_str)
    return render_template('index.html', robot=robot)

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
