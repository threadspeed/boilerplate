---
title: python script scanstars (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'scanstars'

Functions in program: 
* `def scanstars(stars,img,scale):`

Modules used in program: 
* `import numpy as np`
* `import random`
* `import cv2`

## python scanstars

Python mysql example: scanstars

```python
# -*- coding: utf-8 -*-

import cv2
import random
import numpy as np
from make_star_image import make_star_image

#入力ベースマップ
#作りたい元の画像
# 出力星の数
def scanstars(stars,img,scale):

    width, height = img.shape[:2]
    ratio = 10.0 * scale / width

    x = random.random() * 360
    y = random.random() * 180 - 90.0


    akari = cv2.resize(img,(int(height*ratio),int(width*ratio)))
    mask = akari[:,:,3]
    mask = cv2.cvtColor(mask, cv2.COLOR_GRAY2BGR)
    mask = mask / 255.0

    out_img = make_star_image(stars)
    out_img = np.float64( cp.deepcopy(out_img) )
    out_img[0:height:, 0:width] *= (1 - mask)
#    out_img[0:height:, 0:width] += akari * mask
#    cv2.imwrite('star_with_akari.png', out_img)

#print(random.random())

#print(random.uniform(1,2))

#print(random.randint(1,100))

#print(random.choice("123456789abcdefghij"))

#sample_list = ["python","izm","com","random","sample"]

#random.shuffle(sample_list)


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
