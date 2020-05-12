---
title: python script vk photos downloader (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'vk photos downloader'


Modules used in program: 
* `import os`
* `import re`
* `import unidecode`
* `import codecs`
* `import HTMLParser`
* `import time`
* `import traceback`
* `import datetime`
* `import json`
* `import urllib2`
* `import socket`
* `import random`
* `import time`
* `import sys, traceback`
* `import hashlib`
* `import sys`
* `import csv`
* `import random`
* `import time`
* `import string`
* `import re`
* `import requests`

## python vk photos downloader

Python example: vk photos downloader

```python
#!/usr/bin/python
# -*- coding: utf-8 -*-
# How to use:
# 1. pip install bs4, urllib2 ... etc. (and everything other not intalled)
# 2. Insert res array from js file to arr array below
# 3. Profit!!!
import requests
import re
import string
import time
import random
import csv
import sys
import hashlib
import sys, traceback
import time
import random
from random import choice
import socket
import urllib2
import json
import datetime
import traceback
import time

from bs4 import BeautifulSoup,NavigableString
import HTMLParser
from datetime import datetime
import codecs
import unidecode
DEBUG = True
import re
import os
arr = #insert res array from js file here
count = 0
DIR_NAME = './photos2/'
TIMEOUT = 10
for a in arr:
    try:
        s = requests.Session()
        s.headers.update({'User-Agent':'Mozilla/4.0 (compatible; MSIE 8.0; Windows NT 6.0)'})
        response = urllib2.urlopen(a)
        html = response.read()
        soup = BeautifulSoup(html, 'lxml')
        count += 1
        content = soup.select("img")
        photo = urllib2.urlopen(soup.find_all(class_="mva_item")[0]['href'])
        if not os.path.exists(DIR_NAME + soup.find("dd").text):
            os.makedirs(DIR_NAME + soup.find("dd").text)
        output = open(DIR_NAME + soup.find("dd").text +"/" + content[0]['src'][-14:],'wb')
        output.write(photo.read())
        output.close()
        time.sleep(TIMEOUT)
        print(count + " photos downloaded")
    except Exception, e:
        print(a)
        print(e)

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
