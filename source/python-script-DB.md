---
title: python script DB (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'DB'


Modules used in program: 
* `import image_util`
* `import sys`
* `import os`
* `import random`
* `import tensorflow as tf`

## python DB

Python mysql example: DB

```python
import tensorflow as tf
import random
from tensorflow.python.platform import gfile
from tensorflow.python.framework import tensor_shape
import os
import sys

sys.path.insert(0, "scripts")
sys.path.insert(0, "models")

import image_util

class DB:
  
  def __init__(self, img_opt, img_stats, chance_multi):
    self.chance_multi = chance_multi
    def alter():
      self.input, self.output = \
                image_util.add_input_distortions(False, 10, 20, 5, img_stats.size, \
                                           img_stats.size, img_stats.depth, \
                                           img_stats.mean, img_stats.std)
    def unaltered():
      self.input, self.output = \
                image_util.add_jpeg_decoding(img_stats.size, img_stats.size, \
                                       img_stats.depth, img_stats.mean, \
                                       img_stats.std)
    def distort():
      self.input, self.output = \
                image_util.add_input_distortions(True, 20, 20, 5, img_stats.size, \
                                           img_stats.size, img_stats.depth, \
                                           img_stats.mean, img_stats.std)
    options = {
      "alter": alter,
      "unaltered": unaltered,
      "distort": distort,
    }
    options[img_opt]()
  def load_image(self, path, sess):
    if os.path.isfile(path):
      im = gfile.FastGFile(path, "rb").read()
      try:
        out = sess.run(self.output, {self.input: im})
      except Exception as e:
        print(e)
        print(path)
        out = None
      return out
    else:
      return None

  def get_image_pair(self, i, sess):
    p1, p2 = self.get_pair_path(i)
    return self.load_image(p1, sess), self.load_image(p2, sess)

  def get_random_pair(self, sess, level=0):
    if level > 5:
      print("Failed to retrieve pair")
      return 1, 1
    i = random.randrange(self.get_length())
    pair1, pair2 = self.get_image_pair(i, sess)
    if type(pair1) == type(None) or type(pair2) == type(None):
      return self.get_random_pair(sess, level+1)
    return pair1, pair2

  def batch(self, sess, batch_i, batch_size):
    start_i = batch_i * batch_size
    size = min(self.get_length() - start_i, batch_size)
    r_bat = []
    l_bat = []
    for i in range(size):
      r, l = self.get_image_pair(i, sess)
      r_bat.append(r)
      l_bat.append(l)
    return r_bat, l_bat

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
