---
title: python script websockets server (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'websockets server'


Modules used in program: 
* `import os`
* `import time`
* `import wiringpi`
* `import websockets`
* `import random`
* `import datetime`
* `import asyncio`

## python websockets server

Python example: websockets server

```python

import asyncio

import datetime

import random

import websockets

import wiringpi

import time

import os





wiringpi.wiringPiSetupSys()

 

os.system('gpio export 17 out')

 

wiringpi.pinMode(17,1)



async def time(websocket, path):

    while True:

        

        data=await websocket.recv()

        print(data)

        if(data == '1'):

            {

                wiringpi.digitalWrite(17,1)

            }

        if(data == '0'):

            {

                wiringpi.digitalWrite(17,0)

            }

        

        now = datetime.datetime.utcnow().isoformat() + 'Z'

        await websocket.send(now)

        await asyncio.sleep(random.random() * 3)



start_server = websockets.serve(time, '127.0.0.1', 12355)



asyncio.get_event_loop().run_until_complete(start_server)

asyncio.get_event_loop().run_forever()

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
