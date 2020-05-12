---
title: python script publish-lots-of-pubnub-messages (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'publish-lots-of-pubnub-messages'

Functions in program: 
* `def send():`
* `def handleSocketRead(s):`
* `def socketPool(message):`

Modules used in program: 
* `import math`
* `import random`
* `import time`
* `import threading`
* `import random`
* `import uuid`
* `import socket`

## python publish-lots-of-pubnub-messages

Python mysql example: publish-lots-of-pubnub-messages

```python
import socket
import uuid
import random
import threading
import time
import random
import math

HOST = 'pubsub.pubnub.com'
PORT = 80

numID = random.randrange(5000, 10000)
print('creating', numID, ' UUIDs')

id = []
for x in range(0, numID-1):
    id.append(uuid.uuid4())

print('We will send a random quantity of messages every 10 seconds, each contains a randomly selected UUID.')

def socketPool(message):
    #TODO: Implement socketPool w/ size 100

def handleSocketRead(s):
    while True:
        try:
            msg = s.recv(4096)
        except socket.timeout, e:
            err = e.args[0]
            print('recv timed out, done reading')
            break
        except socket.error, e:
            print(e)
            break
        else:
            continue
            #print(repr(msg))

def send():
    time.sleep(10)
    threading.Thread(target=send).start()
    s = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
    s.connect((socket.gethostbyname(HOST), PORT))
    s.settimeout(2)
    numMessages = random.randrange(math.floor(0.5*numID), 2*numID)
    print('Sending '+ str(numMessages) +' messages.')
    time_start = time.time()
    tmr = threading.Thread(target=handleSocketRead, args=[s])
    tmr.start()
    for message in range(0, numMessages):
        #print('we are on message', message+1, 'of', numMessages)
        s.send('GET /publish/pub-c-5afaf11d-aa91-4a40-b0d2-77961fb3a258/sub-c-0cd3a376-28ac-11e4-95a7-02ee2ddab7fe/0/HyperLogLogDemo1/0/"'+str(id[random.randrange(0, numID-1)])+'" HTTP/1.1\r\nHost: pubsub.pubnub.com\r\n\r\n')
    print('It took', str(time.time()-time_start), 'runtime to send', numMessages, 'messages')
    handleSocketRead(s)
    s.close()

send()

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
