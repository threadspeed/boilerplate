---
title: python script pairserver (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'pairserver'


Modules used in program: 
* `import time`
* `import random`
* `import zmq`
* `import subprocess`
* `import sys`
* `import os`

## python pairserver

Python example: pairserver

```python
import os
import sys
import subprocess

sys.path.append('/usr/local/bin')
sys.path.append('/usr/local/grass-7.3.svn/bin')
sys.path.append('/usr/local/grass-7.3.svn/scripts')

os.environ['GISDBASE']='/home/epinux/grassdata/'
os.environ['LOCATION_NAME']='project'
os.environ['GRASS_VERBOSE']='-1'
os.environ['GUI']='text'
os.environ['DEBUG']='0'
os.environ['MAPSET']='PERMANENT'
os.environ['GISBASE']='/usr/local/grass-7.3.svn'
os.environ['GISRC']='/home/epinux/.grass7/rc'
os.environ['GIS_LOCK']='77'
os.environ['GISRC']='/home/epinux/.grass7/rc'

os.environ['PATH']=os.environ['PATH']+':/usr/local/bin:/usr/local/grass-7.3.svn/bin:/usr/local/grass-7.3.svn/scripts'
os.environ['LD_LIBRARY_PATH']='/usr/local/grass-7.3.svn/lib:/usr/local/lib:/usr/lib/'

import zmq
import random
import time

port = "5556"

if len(sys.argv) > 1:
    port =  sys.argv[1]
    int(port)

context = zmq.Context()
socket = context.socket(zmq.REP)
socket.bind("tcp://*:%s" % port)

while True:
    msg = socket.recv()
    print('client meesage: ', msg)
    gmsg=msg.split()
    try:
        proc = subprocess.Popen(gmsg, stdout=subprocess.PIPE)
        output = proc.stdout.read()
        socket.send_string(output)
    except:
        pass
    time.sleep(0.5)

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
