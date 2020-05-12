---
title: python script tree sp 2 (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'tree sp 2'


## python tree sp 2

Python example: tree sp 2

```python
# This version waits for the pi zero to boot

from gpiozero import LED, LEDBoard, SnowPi
from gpiozero.pins.pigpio import PiGPIOFactory
from gpiozero.tools import random_values
from time import sleep
from signal import pause

star = LED(2, initial_value=True)
tree = LEDBoard(*range(3, 28), pwm=True, initial_value=True)

pizero = None
while not pizero:
    try:
        pizero = PiGPIOFactory('fe80::1%usb0')
    except OSError:
        sleep(1)

sp = SnowPi(pwm=True, pin_factory=pizero)

for led in tree:
    led.source = random_values()
    led.source_delay = 0.1

sp.blink()

pause()

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
