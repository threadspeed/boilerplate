---
title: python script run sanic (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'run sanic'


Modules used in program: 
* `import random`

## python run sanic

Python mysql example: run sanic

```python
import random

from sanic import Sanic
from sanic.response import json
from shared import setup_db

app = Sanic()


@app.listener('before_server_start')
async def register_db(app, loop):
    app.db = await setup_db(loop)


@app.listener('after_server_stop')
async def cleanup(app, loop):
    await app.db.close()


@app.route('/')
async def index(request):
    data = {'message': 'hello world'}
    return json(data)


@app.route('/db')
async def get_form_db(request):
    user_id = random.randrange(1, 1000)
    async with request.app.db.acquire() as conn:
        username = await conn.fetchval('SELECT name from users WHERE id=$1', user_id)
    data = {'message': f'hello {username}'}
    return json(data)


if __name__ == '__main__':
    app.run(host='0.0.0.0', port=8000, log_config=None)


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
