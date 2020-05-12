---
title: python script auto recommend test parse (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'auto recommend test parse'


Modules used in program: 
* `import question_helper`
* `import time`

## python auto recommend test parse

Python example: auto recommend test parse

```python
#encoding=utf-8
import time
import question_helper
question = '4.电影《中国合伙人》中,由主角创办的英语学||校叫什么名字?||新希望||新东方||新梦想||'
s = time.time()
print(question_helper.parse_question_and_answer(question)[1])
print(question_helper.parse_question_and_answer(question)[2][0])
print(question_helper.parse_question_and_answer(question)[2][1])
print(question_helper.parse_question_and_answer(question)[2][2])
e = time.time()
print(e -s)

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
