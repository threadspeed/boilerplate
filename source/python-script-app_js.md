---
title: python script app js (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'app js'

Functions in program: 
* `def image():`
* `def index():`

Modules used in program: 
* `import random`

## python app js

Python mysql example: app js

```python
import random
from flask import render_template


@app.route('/', methods=['GET'])
def index():
    """
    Route that maps to the main index page.
    """
    return render_template('indexJS.html')

@app.route('/image', methods=['GET'])
def image():
    """
    Returns a random url
    """
    random_str = ''.join(random.choices('abcedfg', k=5))
    random_image = 'https://robohash.org/{}'.format(random_str)
    return random_image


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
