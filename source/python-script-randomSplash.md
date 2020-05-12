---
title: python script randomSplash (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'randomSplash'

Functions in program: 
* `def randomSplashScreen():`

Modules used in program: 
* `import shutil`
* `import random`
* `import glob`
* `import os`

## python randomSplash

Python mysql example: randomSplash

```python
import os
import glob
import random
import shutil

def randomSplashScreen():
    _tgtDir = "%s/prefs/icons" % os.environ.get("MAYA_APP_DIR")
    _srcDir = "%s/startupImages" % _tgtDir

    if not os.path.exists(_srcDir):
        os.makedirs(_srcDir)

    _list = glob.glob("%s/*.png" % _srcDir)
    if _list:
        _choice = random.choice(_list)
        shutil.copy2(_choice,"%s/MayaStartupImage.png" % _tgtDir)


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
