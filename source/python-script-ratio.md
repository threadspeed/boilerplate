---
title: python script ratio (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'ratio'

Functions in program: 
* `def main():`

## python ratio

Python mysql example: ratio

```python
def main():
  values = [19671, 1064, 28017, 2411, 52546]
  names = [u"投稿率", u"リポスト", u"ファボ", u"コメント", u"フォロー"]
  min = values[0]
  for value in values:
    if min > value:
      min = value

  for i in range(0,5):
   print(names[i] + u" : " + unicode(values[i] / min))

if __name__ == '__main__':
  main()
  
# [結果]
# 投稿率 : 18
# リポスト : 1
# ファボ : 26
# コメント : 2
# フォロー : 49

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
