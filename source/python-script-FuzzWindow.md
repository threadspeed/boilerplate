---
title: python script FuzzWindow (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'FuzzWindow'


Modules used in program: 
* `import random`

## python FuzzWindow

Python example: FuzzWindow

```python
from PyQt5.QtWidgets import QDialog, QPushButton, QVBoxLayout
import random

class FuzzDialog(QDialog):
    def __init__(self, parent=None):
        super().__init__(parent)
        layout = QVBoxLayout(self)
        fuzzBox = QPushButton("Fuzz", self)
        fuzzBox.clicked.connect(self.glyphFuzzer)
        layout.addWidget(fuzzBox)
        self.setLayout(layout)

    def glyphFuzzer(self):
        glyph = CurrentGlyph()
        if glyph is not None and len(glyph):
            glyph.prepareUndo()
            for contour in glyph:
                for point in contour:
                    point.x += random.randrange(-4, 5)
                    point.y += random.randrange(-4, 5)
            glyph.dirty = True

window = FuzzDialog()
window.show()

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
