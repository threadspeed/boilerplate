---
title: python script linear (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'linear'

Functions in program: 
* `def linear(search, list, size):`

Modules used in program: 
* `import random`

## python linear

Python mysql example: linear

```python
# -*- coding: utf -8 -*-

"""
アルゴリズムとデータ構造レポート3 [探索]
リニアサーチ(番兵なし)
"""

import random

def linear(search, list, size):
	"""
	linear - リニアサーチ関数
	@param search	探したい要素
	@param list		検索対象のリスト
	@param size		リストサイズ
	@return 検索結果(-1: NOT FOUND, その他: 要素番号)
	"""
	
	num = 0 # 要素番号
	
	# 配列のサイズの中で，目的の値を探す
	while (num<size) and (list[num]!=search):
		num += 1
	
	# 配列のサイズ内かを確認
	if num<size:
		return num
	
	# NOT FOUND
	return -1

if __name__ == '__main__':
	# 適当な配列を生成
	list = [random.randint(0, 1000) for x in range(1000)]
	
	# 検索対象
	search = random.randint(0, 1000)
	
	# リニアサーチ回す
	result = linear(search, list, len(list))
	
	if result:
		print(search)
	else:
		print('NOT FOUND')

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
