---
title: python script urlsutils (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'urlsutils'

Functions in program: 
* `def pickRandom(list):`
* `def topics(hotTopics, allWords):`
* `def findKey(data):`
* `def pickWordsList(pickedWords, allWords):`
* `def readjson(subject, page_num):`

Modules used in program: 
* `import random`

## python urlsutils

Python mysql example: urlsutils

```python
import random

def readjson(subject, page_num):
	subject = open(pages[page_num]).read()
	return json.loads(subject)

def pickWordsList(pickedWords, allWords):
	pickedWords = random.sample(allWords, 4)
	wordsList = list()
	for word in pickedWords:
		word = word.lower()
		word = word.replace(" ", "-")
		wordsList.append(word)
	return wordsList

def findKey(data):
	for key in data.keys():
		if key != 'description':
			return key

def topics(hotTopics, allWords):
	hotTopics = random.sample(allWords, 3)
	topicsList = list()
	for word in hotTopics:
		topicsList.append(word)
	return topicsList

def pickRandom(list):
	picked = random.choice(list)
	return picked

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
