---
title: python script findmarker delaunay (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'findmarker delaunay'

Functions in program: 
* `def recognize(im):`
* `def draw_delaunay(img, subdiv, delaunay_color, distance ) :`
* `def draw_point(img, p, color ) :`
* `def rect_contains(rect, point) :`

Modules used in program: 
* `import cv2`
* `import math`
* `import random`
* `import numpy as np`

## python findmarker delaunay

Python example: findmarker delaunay

```python
import numpy as np
import random
import math
import cv2
from PIL import Image

# 三角形とみなす閾値の長さ
len = 10000

def rect_contains(rect, point) :
    if point[0] < rect[0] :
        return False
    elif point[1] < rect[1] :
        return False
    elif point[0] > rect[2] :
        return False
    elif point[1] > rect[3] :
        return False
    return True
 
# Draw a point
def draw_point(img, p, color ) :
    cv2.circle( img, p, 2, color, cv2.cv.CV_FILLED, cv2.CV_AA, 0 )
 
 
# Draw delaunay triangles
def draw_delaunay(img, subdiv, delaunay_color, distance ) :
 
    triangleList = subdiv.getTriangleList();
    size = img.shape
    r = (0, 0, size[1], size[0])
 
    for t in triangleList :
         
        pt1 = (t[0], t[1])
        pt2 = (t[2], t[3])
        pt3 = (t[4], t[5])
        s = (t[0]-t[2])*(t[0]-t[2]) + (t[1]-t[3])*(t[1]-t[3]) + (t[2]-t[4])*(t[2]-t[4]) + (t[3]-t[5])*(t[3]-t[5])+ (t[4]-t[0])*(t[4]-t[0]) + (t[5]-t[1])*(t[5]-t[1])
        if s < distance and s > -distance and rect_contains(r, pt1) and rect_contains(r, pt2) and rect_contains(r, pt3) :
         
            cv2.line(img, pt1, pt2, (0,255,0), 2)
            cv2.line(img, pt2, pt3, (0,255,0), 2)
            cv2.line(img, pt3, pt1, (0,255,0), 2)

def recognize(im):
 # 輪郭線抽出のための二値化
 im_gray = cv2.cvtColor(im, cv2.COLOR_BGR2GRAY)
 im_blur = cv2.GaussianBlur(im_gray, (3, 3), 0)
 ret,th = cv2.threshold(im_blur, 0, 255, cv2.THRESH_BINARY_INV+cv2.THRESH_OTSU)
 
 # 画像から輪郭線を抽出
 imgEdge,contours,hierarchy = cv2.findContours(th, cv2.RETR_TREE,cv2.CHAIN_APPROX_SIMPLE)

 # 背景を黒に
 im[:] = (0, 0, 0)
 
 size = im.shape
 rect = (0, 0, size[1], size[0])
     
 # Create an instance of Subdiv2D
 subdiv = cv2.Subdiv2D(rect);
 
 points = [];
 for (i,cnt) in enumerate(contours):
   # 輪郭線領域を長方形に近似する
   rect = cv2.minAreaRect(cnt)
   s = rect[1][0] * rect[1][1]         # 面積
   p = rect[1][0] / (rect[1][1] + 0.1) # 縦横比
   if s > 500 or s < 50: continue
   if p < 0.4 or p > 2.0 : continue

   # 中心位置
   cx = int(rect[0][0])
   cy = int(rect[0][1])
   points.append((int(cx), int(cy)))
   
   # ×を描画
   cv2.line(im, (cx - 3,cy - 3),(cx + 3, cy + 3), (0,255,0), 2)
   cv2.line(im, (cx + 3,cy - 3),(cx - 3, cy + 3), (0,255,0), 2)

 for p in points :
   subdiv.insert(p)
   draw_delaunay( im, subdiv, (255, 255, 255) , len);
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
