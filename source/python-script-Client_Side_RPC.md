---
title: python script Client Side RPC (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'Client Side RPC'

Functions in program: 
* `def on_message(client, userdata, msg):`
* `def on_connect(client, userdata, flags, rc):`

Modules used in program: 
* `import paho.mqtt.client as mqtt`
* `import random`
* `import json`
* `import sys`
* `import time`
* `import os`

## python Client Side RPC

Python example: Client Side RPC

```python
# This Program illustrates the Client Side RPC on ThingsBoard IoT Platform
# Paste your ThingsBoard IoT Platform IP and Device access token
# Client_Side_RPC.py : This program will illustrates the Client side
import os
import time
import sys
import json
import random
import paho.mqtt.client as mqtt

# Thingsboard platform credentials
THINGSBOARD_HOST = 'Paste your ThingsBoard IP'
ACCESS_TOKEN = 'Paste your Device Access Token Here '
request = {"method": "getemail", "params": ""}

# MQTT on_connect callback function
def on_connect(client, userdata, flags, rc):
    print("rc code:", rc)
    client.subscribe('v1/devices/me/rpc/response/+')
    client.publish('v1/devices/me/rpc/request/1',json.dumps(request), 1)

# MQTT on_message caallback function
def on_message(client, userdata, msg):
    print('Topic: ' + msg.topic + '\nMessage: ' + str(msg.payload))

# start the client instance
client = mqtt.Client()

# registering the callbacks
client.on_connect = on_connect
client.on_message = on_message

client.username_pw_set(ACCESS_TOKEN)
client.connect(THINGSBOARD_HOST, 1883, 60)

try:
    client.loop_forever()

except KeyboardInterrupt:
    client.disconnect()



```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
