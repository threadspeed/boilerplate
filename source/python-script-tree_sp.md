---
title: python script tree sp (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'tree sp'


## python tree sp

Python example: tree sp

```python
# See http://bennuttall.com/raspberry-pi-zero-gpio-expander/

from gpiozero import LED, LEDBoard, SnowPi
from gpiozero.pins.pigpio import PiGPIOFactory
from gpiozero.tools import random_values
from signal import pause

pizero = PiGPIOFactory('fe80::1%usb0')

star = LED(2, initial_value=True)
tree = LEDBoard(*range(3, 28), pwm=True)
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
