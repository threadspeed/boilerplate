---
title: python script check delivery time (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'check delivery time'


Modules used in program: 
* `import traceback`
* `import os`
* `import os.path`
* `import string`
* `import random`
* `import email.utils`
* `import time`
* `import sys`
* `import smtplib`
* `import json`
* `import optparse`

## python check delivery time

Python example: check delivery time

```python
import optparse
import json
import smtplib
import sys
import time
import email.utils
import random
import string
import os.path
import os
import traceback
from socket import gethostname
from email.mime.text import MIMEText
from email import message_from_file

CONFIGFILE = "/path/to/config.json"

if __name__ == "__main__":
  try:
    parser = optparse.OptionParser(usage="Usage: %prog [options]")
    parser.add_option("--config", dest="config", type="str", help="Config file path", default="")
    parser.add_option("-w", "--warning", dest="warning", type="float", help="Delivery time before warning")
    parser.add_option("-c", "--critical", dest="critical", type="float", help="Delivery time before critical")
    
    options, args = parser.parse_args()
    
    global CONFIG
    CONFIG = None
    
    if options.config != "":
      with open(options.config) as f:
        CONFIG = json.load(f)
    else:
      with open(CONFIGFILE) as f:
        CONFIG = json.load(f)
    
    hostname = gethostname() + "." + CONFIG["domain"]
    
    if options.warning > options.critical:
      raise Exception("Warning time cannot be greater than critical time.")
    
    times = []
    for root, dirs, files in os.walk(os.path.join(CONFIG["maildir"], "Maildir", "new")):
      for name in files:
        filename = os.path.join(root, name)
        stats = os.stat(filename)
        with open(filename) as emailf:
          msg = message_from_file(emailf)
        if msg["Subject"].lower().strip() == hostname.lower().strip():
          body = msg.get_payload()
          starttime = float(body.strip())
          times.append((starttime, stats.st_ctime))
          os.remove(filename)
    
    if len(times) == 0:
      print("No messages found.")
      sys.exit(3)
    times.sort(key=lambda t: t[0])
    latest = times[-1]
    start = latest[0]
    end = latest[1]
    deliverytime = end - start
    print("Delivery time: %s" % deliverytime)
    if deliverytime > options.critical:
      sys.exit(2)
    elif deliverytime > options.warning:
      sys.exit(1)
    else:
      sys.exit(0)
  except Exception, e:
    traceback.print_exc()
    print(str(e))
    sys.exit(3)

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
