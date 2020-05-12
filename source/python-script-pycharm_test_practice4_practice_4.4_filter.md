---
title: python script pycharm test practice4 practice 4.4 filter (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'pycharm test practice4 practice 4.4 filter'

Functions in program: 
* `def text_censored_create(name,message):`
* `def text_filter(word , censord_word = 'lame' , changed_word = 'Alsome'):`
* `def text_create(name,message):`

## python pycharm test practice4 practice 4.4 filter

Python mysql example: pycharm test practice4 practice 4.4 filter

```python
# file = open('E:/MyCodes/python/tmp/test0526.txt','w')
# file.write('Hello!')
#创建文件并写入内容
def text_create(name,message):
    text_path = 'E:/MyCodes/python/tmp/'
    full_path = text_path + name + '.txt'
    file = open(full_path,'w')
    file.write(message)
    file.close()
    print('操作完成！')
    return 0
##调用函数
text_create('text_create_function' , 'Hi, I\'m from your own function which named text_create in practice_4.4_filter.py')
print('分割线----------------')
#过滤文本
def text_filter(word , censord_word = 'lame' , changed_word = 'Alsome'):
    return word.replace(censord_word,changed_word)
print(text_filter('Python is lame!'))

def text_censored_create(name,message):
    filtered_msg = text_filter(message)
    text_create(name,filtered_msg)
text_censored_create('filter_lame','过滤文本，Python is lame!!!')


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
