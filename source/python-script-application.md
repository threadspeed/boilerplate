---
title: python script application (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'application'


Modules used in program: 
* `import random, json, time, datetime`
* `import random, json, time, datetime`
* `import os`

## python application

Python mysql example: application

```python
import os
import random, json, time, datetime

from flask import Flask, session, render_template, url_for, request, redirect, jsonify, Response
from flask_session import Session
from flask_socketio import SocketIO, emit, join_room, leave_room

import random, json, time, datetime

app = Flask(__name__)
app.config["SECRET_KEY"] = os.getenv("SECRET_KEY")
socketio = SocketIO(app)

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
