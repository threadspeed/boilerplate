---
title: python script crawler download worker (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'crawler download worker'

Functions in program: 
* `def Download(req_url):`

Modules used in program: 
* `import urlparse`
* `import time`
* `import json`
* `import urllib2`
* `import sys`
* `import socket, traceback`
* `import random`

## python crawler download worker

Python mysql example: crawler download worker

```python
#!/usr/bin/env python
import random
import socket, traceback
import sys
import urllib2
import json
import time
import urlparse

default_headers = {
    'User-Agent': 'Mozilla/5.0 (X11; Linux x86_64) AppleWebKit/537.36 (KHTML, like Gecko) '
                  'Chrome/50.0.2661.102 Safari/537.36'
}
last_request_time={}
def Download(req_url):
    parsedTuple = urlparse.urlparse(req_url)
    host = parsedTuple.hostname
    global  last_request_time

    if (host in last_request_time  and time.time() - last_request_time[host] < 3.0) :
        sleep_time = random.randint(3, 6)  # '%.2f' % random.random()
        time.sleep(sleep_time)

    last_request_time[host] = time.time()
    try:
        req = urllib2.Request(req_url, headers=default_headers)
        page = urllib2.urlopen(req, timeout=20)
        content = page.read()
    except:
        traceback.print_exc()
        return ""
    return content

host = ''                               # Bind to all interfaces
port = 51423

s = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
s.setsockopt(socket.SOL_SOCKET, socket.SO_REUSEADDR, 1)
s.bind((host, port))

s.listen(1)

while 1:
    try:
        clientsock, clientaddr = s.accept()
    except KeyboardInterrupt:
        raise
    except:
        traceback.print_exc()
        continue

    # Process the connection

    try:
        print("Got connection from", clientsock.getpeername())
        # Process the request here
        req_url = clientsock.recv(1024)
        print(req_url)
        if (len(req_url) == 0):
            print("Error url get from remote")
        content = ""
        if (len(req_url) != 0):
            content = Download(req_url)
        print("Get data length: " + str(len(content)))
        clientsock.sendall(content)


    except (KeyboardInterrupt, SystemExit):
        raise
    except:
        traceback.print_exc()

    # Close the connection

    try:
        clientsock.close()
    except KeyboardInterrupt:
        raise
    except:
        traceback.print_exc()

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
