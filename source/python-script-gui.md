---
title: python script gui (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'gui'

Functions in program: 
* `def loadSQLiteData(depl=0):`

Modules used in program: 
* `import random`
* `import sqlite3`
* `import sys`

## python gui

Python example: gui

```python
#!/usr/bin/python

import sys
import sqlite3
import random
from PyQt4.QtCore import *
from PyQt4.QtGui import *

# GUI with a table that fetches 1000 rows when the range selector changes the value

START_INDEX = 14069381
RANGE = 100000

conn = sqlite3.connect('test.db')
c = conn.cursor()


def loadSQLiteData(depl=0):
    data = []
    query = 'SELECT * FROM plot WHERE x_bound > %d\
            LIMIT 1000' % (START_INDEX + random.randint(0, RANGE))
    # print(query)
    for row in c.execute(query):
        data.append(row)
    return data


class SqliteTestWindow(QWidget):
    def __init__(self, *args):
        QWidget.__init__(self, *args)

        self.tablemodel = tablemodel = SqliteTableModel(loadSQLiteData(), self)
        tableview = QTableView()
        tableview.setModel(tablemodel)

        sliderView = QSlider(Qt.Horizontal)

        QObject.connect(sliderView,
                        SIGNAL("valueChanged(int)"),
                        self.onSliderChanged)

        layout = QVBoxLayout(self)
        layout.addWidget(sliderView)
        layout.addWidget(tableview)
        self.setLayout(layout)

    def onSliderChanged(self, val):
        self.tablemodel.setData(loadSQLiteData(val))


class SqliteTableModel(QAbstractTableModel):
    def __init__(self, datain, parent=None, *args):
        QAbstractTableModel.__init__(self, parent, *args)
        self.arraydata = datain

    def setData(self, data):
        self.beginResetModel()
        self.arraydata = data
        self.endResetModel()

    def rowCount(self, parent):
        return len(self.arraydata)

    def columnCount(self, parent):
        if(len(self.arraydata) == 0):
            return 0
        return len(self.arraydata[0])

    def data(self, index, role):
        if not index.isValid():
            return QVariant()
        elif role != Qt.DisplayRole:
            return QVariant()
        return QVariant(self.arraydata[index.row()][index.column()])


if __name__ == "__main__":
    app = QApplication(sys.argv)
    main_window = SqliteTestWindow()
    main_window.show()
    app.exec_()


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
