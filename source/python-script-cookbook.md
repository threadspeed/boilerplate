---
title: python script cookbook (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'cookbook'

Functions in program: 
* `def random_pick(some_list, probabilities):`
* `def is_text(s, text_characters=text_characters, threshold=0.3):`
* `def translator(frm='', to='', delete='', keep=None):`

Modules used in program: 
* `import sys`
* `import random`
* `import random`
* `import string`
* `import string`

## python cookbook

Python mysql example: cookbook

```python
# coding: utf-8


u"""
1.4 字符串对齐
字符串方法 ljust rjust center 参数: int 对齐符号数目 str 可以选的对齐占位符,默认为空格
"""

# 1.9 简化string translate方法使用流程
import string

def translator(frm='', to='', delete='', keep=None):
    if len(to) == 1:
        to = len(frm) * to
    trans = string.maketrans(frm, to) # 创建翻译表
    if keep is not None:
        allchars = string.maketrans('', '')
        delete = allchars.translate(allchars, keep.translate(allchars, delete))
    def translate(s):
        return s.translate(trans, delete)
    return translate


# 1.11 检查文本是否为字符串
from __future__ import division
import string

text_characters = "".join(map(chr, range(32, 127))) + "\n\r\t\b"
_null_trans = string.maketrans('', '')
def is_text(s, text_characters=text_characters, threshold=0.3):
    u"""
    借鉴Perl的判断,如果文本有30%以上不是字符,那就不是字符串
    """
    if '\0' in s:
        return False
    if not s:
        return True
    t = s.translate(_null_trans, text_characters)
    return len(t)/len(s) <= threshold


# 4.21 指定概率获取随机值
import random

def random_pick(some_list, probabilities):
    x = random.uniform(0, 1)
    cumulative_probability = 0.0
    for item, item_probability in zip(some_list, probabilities):
        cumulative_probability += item_probability
        if x < cumulative_probability: break
    return item


# 5.6 随机访问list
import random
random.shuffle(some_list)


# 6.2 定义常量
class _const(object):
    class ConstError(TypeError): pass

    def __setattr__(self, name, value):
        if name in self.__dict__:
            raise self.ConstError('Can`t rebind const name {}'.format(name))
        self.__dict__[name] = value

    def __delattr__(self, name):
        if name in self.__dict__:
            raise self.ConstError('Can`t unbind const name {}'.format(name))
        raise NameError(name)

import sys
sys.modules[__name__] = _const()


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
