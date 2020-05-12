---
title: python script cyborghousewife (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'cyborghousewife'


Modules used in program: 
* `import random	#import random library`

## python cyborghousewife

Python mysql example: cyborghousewife

```python
import random	#import random library

girls = []		#make an empty list called girls
substring = "girl"

key_words = ["woman", "women", "girl", "mother"]

usernames = open('10million.txt').read()	#load 10million.txt into a string

for item in usernames.split():		#go through usernames, split the string up into words
	if substring in item:				#check if the list contains the substring girl
		girls.append(item)				#if it does, add it to the list called girls

#loop through the list girls and print(all the items in it)
# for item in girls:				
# 	print(item)


for line in open("housewife.txt"):		#for each line in housewife.txt (loaded as a string)
	line = line.strip()		#strip the whitespace
	#line = line.split()		#split each line into a list of words
	#if any(match in line for match in key_words):
	#	print(match)
	
for word in key_words:		#for all the words in the list key words
	if word in line:		#if the word is in the line
		newline = line.replace(word, random.choice(girls))	#replace the word with a random word from the list girls()
		print(newline		#print(the new line)
	

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
