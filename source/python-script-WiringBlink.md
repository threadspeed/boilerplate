---
title: python script WiringBlink (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'WiringBlink'


Modules used in program: 
* `import os`
* `import time`
* `import wiringpi`

## python WiringBlink

Python mysql example: WiringBlink

```python

import wiringpi

import time

import os

 

wiringpi.wiringPiSetupSys()

 

os.system('gpio export 17 out')

 

wiringpi.pinMode(17,1)

 

while True:

    time.sleep(0.5)

    wiringpi.digitalWrite(17,1)

    time.sleep(0.5)

    wiringpi.digitalWrite(17,0)

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
