---
title: python script deliverytimemailsender (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'deliverytimemailsender'

Functions in program: 
* `def sendMessage(smtp, messagestr, env_from_address, sendingtoaddress):`
* `def dumpRecipientsRefused(e):`
* `def debugwrite(s):`

Modules used in program: 
* `import string`
* `import random`
* `import email.utils`
* `import time`
* `import sys`
* `import smtplib`
* `import json`
* `import optparse`

## python deliverytimemailsender

Python example: deliverytimemailsender

```python
import optparse
import json
import smtplib
import sys
import time
import email.utils
import random
import string
from email.mime.text import MIMEText

CONFIGFILE = "/path/to/config.json"

def debugwrite(s):
  if DEBUG:
    sys.stderr.write(s)

def dumpRecipientsRefused(e):
  '''Takes in an SMTPRecipientsRefused exception and
pretty prints it if verbosity is set.'''
  if DEBUG:
    sys.stderr.write("Recipient Address Refused.\n")
    for k, v in e.recipients.items():
      sys.stderr.write("%s: %s (%s)\n" % (k, v[0], v[1]))

def sendMessage(smtp, messagestr, env_from_address, sendingtoaddress):
  '''Sends the given message to the given address,
using the given SMTP instance.'''
  debugwrite("Sending a message.\n")
  try:
    smtp.sendmail(env_from_address,
                  sendingtoaddress,
                  messagestr)
  except smtplib.SMTPRecipientsRefused, e:
    dumpRecipientsRefused(e)
  except smtplib.SMTPHeloError, e:
    debugwrite("SMTP server failed to respond correctly to HELO command.\n", 1)
  except smtplib.SMTPSenderRefused, e:
    debugwrite(
        "SMTP server rejected env-from address of %s.\n"
        % env_from_address, 1)
  except smtplib.SMTPDataError, e:
    debugwrite("Unknown STMP error.\n")

      
if __name__=="__main__":
  parser = optparse.OptionParser(usage="Usage: %prog [options] server")
  parser.add_option("--config", dest="config", type="str", help="Config file path", default="")
  parser.add_option("-d", "--debug", dest="debug", action="store_true", help="Debugging output.", default=False)
  
  options, args = parser.parse_args()
  
  global DEBUG
  DEBUG = options.debug
  
  global CONFIG
  if options.config != "":
    with open(options.config) as f:
      CONFIG = json.load(f)
  else:
    with open(CONFIGFILE) as f:
      CONFIG = json.load(f)
  
  for server in CONFIG["servers"]:
    smtp = smtplib.SMTP(server)
    if "smtp_user" in CONFIG and "smtp_pass" in CONFIG:
      smtp.login(CONFIG["smtp_user"], CONFIG["smtp_pass"])
    
    messageraw = str(time.time())
    message = MIMEText(messageraw)
    message["Date"] = email.utils.formatdate()
    message["From"] = CONFIG["from_header"]
    message["To"] = CONFIG["to_header"]
    message["Subject"] = server
   
    sendMessage(smtp, message.as_string(), CONFIG["mail_from"], CONFIG["rcpt_to"])

    smtp.close()
  


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
