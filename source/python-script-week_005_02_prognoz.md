---
title: python script week 005 02 prognoz (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'week 005 02 prognoz'

Functions in program: 
* `def prognoz():`

## python week 005 02 prognoz

Python example: week 005 02 prognoz

```python
def prognoz():
	temp = int(input("Температура на сегодня?\n"))
	result = None
	if temp < 0:
		if temp > -15:
			result = "снег"
		elif -30 < temp < -15:
			result = "лед"
	elif temp < 15:
		if temp > 7:
			result = "дождь"
		elif 0 < temp < 7:
			result = "град"
	elif 15 < temp < 25:
		result = "ветер"
	elif 25 < temp < 30:
		result = "солнце"
	
	if result is not None:
		print("Погода на сегодня: %s" % result)
	else:
		print("404: Прогноз погоды не существует")


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
