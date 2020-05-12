---
title: python script reactive-move-scroll (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'reactive-move-scroll'

Functions in program: 
* `def react(x, y, button=None, down=None):`

Modules used in program: 
* `import time`
* `import colorsys`

## python reactive-move-scroll

Python mysql example: reactive-move-scroll

```python
import colorsys
import time
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


last_time = {
    "color": time.time(),
    "react": time.time()
}

def react(x, y, button=None, down=None):
    global last_time

    print(x, y, button, down)

    this_time = time.time()

    # Don't change color on button release
    if (down or down == -1) and this_time - last_time["color"] > 0.1:
        color = list(map(lambda x: int(x * 255), colorsys.hsv_to_rgb(random(), 1, 1)))
        firefly.fx.reactive(color[0], color[1], color[2], 1)
        last_time["color"] = this_time

    if this_time - last_time["react"] > 0.05:
        firefly.trigger_reactive()
        last_time["react"] = this_time


while True:
    try:
        with mouse.Listener(on_click=react, on_move=react, on_scroll=react) as mouse_listener:
            mouse_listener.join()
    except Exception as e:
        print(e)


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
