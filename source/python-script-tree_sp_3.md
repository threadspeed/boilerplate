---
title: python script tree sp 3 (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'tree sp 3'

Functions in program: 
* `def blink(sp, b):`

## python tree sp 3

Python example: tree sp 3

```python
# This version allows the snowpi brightness to be set
# and turns the tree lights on while the pi zero boots

from gpiozero import LED, LEDBoard, SnowPi
from gpiozero.pins.pigpio import PiGPIOFactory
from gpiozero.tools import random_values
from time import sleep

def blink(sp, b):
    while True:
        sp.value = [(b, b), b, ((b, b, b), (b, b, b))]
        sleep(1)
        sp.off()
        sleep(1)

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

blink(sp, 0.1)

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
