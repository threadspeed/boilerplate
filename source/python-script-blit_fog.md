---
title: python script blit fog (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'blit fog'


## python blit fog

Python example: blit fog

```python
from array import array

from kivy.app import App
from kivy.lang import Builder
from kivy.graphics.fbo import Fbo
from kivy.graphics.texture import Texture
from kivy.uix.widget import Widget
from kivy.properties import ListProperty, ObjectProperty

KV = '''
#:import F kivy.factory.Factory
#:import random random.random

FloatLayout:
    GridLayout:
        cols: 20
        on_parent:
            for i in range(20 * 20): self.add_widget(F.ColorLabel(text=str(i)))
    Fog:
        texture_size: 100, 100
        pencil_size: 5, 5

<ColorLabel@Label>:
    canvas.before:
        Color:
            rgba: [random() for i in range(4)]
        Rectangle:
            pos: self.pos
            size: self.size

<Fog>:
    canvas:
        Rectangle:
            size: self.size
            pos: self.pos
            texture: self.texture

'''

class Fog(Widget):
    texture_size = ListProperty([0, 0])
    texture = ObjectProperty(allownone=True)
    pencil_size = ListProperty([1, 1])

    def on_texture_size(self, *args):
        self.texture = texture = Texture.create(size=self.texture_size)

        size = self.texture_size[0] * self.texture_size[1]
        buf = sum(([0, 0, 0, 255] for x in range(size)), [])
        arr = array('B', buf)
        texture.blit_buffer(arr, colorfmt='rgba', bufferfmt='ubyte')

    def on_touch_move(self, touch):
        width, height = self.texture_size
        x = (touch.x - self.x) / self.width
        y = (touch.y - self.y) / self.height

        if not (0 < x < 1 and 0 < y < 1):
            return

        texture = self.texture

        ps = self.pencil_size

        texture.blit_buffer(
            array('B', [0, 0, 0, 0] * ps[0] * ps[1]),
            colorfmt='rgba',
            bufferfmt='ubyte',
            size=ps,
            pos=(x * width - ps[0] / 2, y * height - ps[1] / 2)
        )
        self.canvas.flag_update()


class DrawApp(App):
    def build(self):
        return Builder.load_string(KV)


if __name__ == '__main__':
    DrawApp().run()

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
