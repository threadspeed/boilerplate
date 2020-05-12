---
title: python script findmarker (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'findmarker'

Functions in program: 
* `def recognize(im):`

Modules used in program: 
* `import cv2`
* `import math`
* `import random`
* `import numpy as np`

## python findmarker

Python mysql example: findmarker

```python
import numpy as np
import random
import math
import cv2
from PIL import Image

def recognize(im):
 # 輪郭線抽出のための二値化
 im_gray = cv2.cvtColor(im, cv2.COLOR_BGR2GRAY)
 im_blur = cv2.GaussianBlur(im_gray, (3, 3), 0)
 ret,th = cv2.threshold(im_blur, 0, 255, cv2.THRESH_BINARY_INV+cv2.THRESH_OTSU)
 
 # 画像から輪郭線を抽出
 imgEdge,contours,hierarchy = cv2.findContours(th, cv2.RETR_TREE,cv2.CHAIN_APPROX_SIMPLE)

 # 背景を黒に
 im[:] = (0, 0, 0)
 
 for (i,cnt) in enumerate(contours):
   # 輪郭線領域を長方形に近似する
   rect = cv2.minAreaRect(cnt)
   s = rect[1][0] * rect[1][1]         # 面積
   p = rect[1][0] / (rect[1][1] + 0.1) # 縦横比
   # if s < 8000 or s > 15000 : continue
   if p < 0.4 or p > 2.0 : continue

   # 中心位置
   cx = int(rect[0][0])
   cy = int(rect[0][1])
   
   # ×を描画
   cv2.line(im, (cx - 3,cy - 3),(cx + 3, cy + 3), (0,255,0), 2)
   cv2.line(im, (cx + 3,cy - 3),(cx - 3, cy + 3), (0,255,0), 2)

 return im

if __name__ == '__main__':
  input_file_name = "input.mp4"
  output_file_name = "output.avi"

  video = cv2.VideoCapture(input_file_name)
  width = int(video.get(3))
  height = int(video.get(4))
  fps = int(video.get(5))
  frame_count = int(video.get(7))

  fourcc = cv2.VideoWriter_fourcc(*'XVID')
  out = cv2.VideoWriter(output_file_name,fourcc, fps, (width,height))

  cv2.namedWindow('window')

  for i in range(frame_count):
    _, frame = video.read()
    im_list = recognize(frame)
    cv2.imshow('window',im_list)
    out.write(frame)
    key = cv2.waitKey(1)

  out.release()
  cv2.destroyAllWindows()


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
