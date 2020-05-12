---
title: python script MainScores (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'MainScores'

Functions in program: 
* `def score_server():`

Modules used in program: 
* `import Utils`

## python MainScores

Python mysql example: MainScores

```python
from flask import Flask
import Utils
app = Flask(__name__)

@app.route('/')
def score_server():
    try:
        score = open("Scores.txt", "r")
    except BaseException as e:
        return """<html>
        <head>
            <title>Scores Game</title>
        </head>
        <body>
        <body>
            <h1><div id="score" style="color:red">""" + Utils.ERROR_MESSAGE() + str(e) + """</div></h1>
        </body>
        </html>
        """
    return """
    <html>
        <head>
            <title>Scores Game</title>
        </head>
        <body>
            <h1>The score is <div id="score">""" + str(score.readline()) + """</div></h1>
        </body>
    </html>"""


if __name__ == '__main__':
    app.run(host='0.0.0.0', debug=True, threaded=True, port=8777)

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
