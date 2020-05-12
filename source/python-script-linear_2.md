---
title: python script linear 2 (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'linear 2'

Functions in program: 
* `def linear(search, list, size):`

Modules used in program: 
* `import random`

## python linear 2

Python example: linear 2

```python
# -*- coding: utf -8 -*-

"""
アルゴリズムとデータ構造レポート3 [探索]
リニアサーチ(番兵あり)
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
	
	# 番兵と最後の要素をほげ
	sentinel, list[-1] = list[-1], search
	
	# 目的の値を探す
	while list[num]!=search:
		num += 1
	
	# 番兵を元に戻す
	list[-1] = sentinel
	
	if num < size-1:
		return num
	
	if size == sentinel:
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
