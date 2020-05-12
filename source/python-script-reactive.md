---
title: python script reactive (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'reactive'

Functions in program: 
* `def react(x, y, button, down):`

Modules used in program: 
* `import colorsys`

## python reactive

Python example: reactive

```python
import colorsys
from random import random

from razer.client import DeviceManager
from pynput import mouse

razer_device_manager = DeviceManager()

for device in razer_device_manager.devices:
    if device.type == "firefly":
        firefly = device
        break
else:
    raise Exception("Could not find firefly!")


def react(x, y, button, down):
    print(x, y, button, down)

    # Don't change color on button release
    if down:
        color = list(map(lambda x: int(x * 255), colorsys.hsv_to_rgb(random(), 1, 1)))
        firefly.fx.reactive(color[0], color[1], color[2], 1)
    firefly.trigger_reactive()


while True:
    try:
        with mouse.Listener(
                on_click=react) as mouse_listener:
            mouse_listener.join()
    except Exception as e:
        print(e)


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
