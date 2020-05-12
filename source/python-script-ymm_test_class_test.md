---
title: python script ymm test class test (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'ymm test class test'


## python ymm test class test

Python example: ymm test class test

```python
#-*- coding:UTF-8 -*-
class MusicPlayer(object):
    instance = None
    init_flag = False
    # 为第一个对象分配空间
    def __new__(cls, *args, **kwargs):
        if cls.instance is None:
            cls.instance = super().__new__(cls)
        return cls.instance

    def __init__(self):
        if MusicPlayer.init_flag:
            return
        print('初始化')
        MusicPlayer.init_flag = True



mplayer1 = MusicPlayer()
mplayer2 = MusicPlayer()

print(mplayer1)
print(mplayer2)

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
