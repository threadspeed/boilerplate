---
title: python script make own constellation (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'make own constellation'


Modules used in program: 
* `import cv2`

## python make own constellation

Python example: make own constellation

```python
# -*- coding: utf-8 -*-

from constellation import read_constellation
from make_star_image import make_star_image
from scanstars import scanstars

import cv2

#星のデータの読み込み
stars = read_constellation('some.csv')

# 与えた画像とベースマップから星のデータ数を取得する
img = cv2.imread('akari.png',-1)
scale = 5.0
n = scanstars(stars,img,scale)

#make_star_image(stars, "stars.png")


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
