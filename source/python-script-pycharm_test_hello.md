---
title: python script pycharm test hello (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'pycharm test hello'


## python pycharm test hello

Python mysql example: pycharm test hello

```python
#
#输出“Hello World!”
print('Hello World!')
#
#加减法
a = 12
b = 13
c = a + b
print(c)
#
##打开一个文件并写入
###注意windows下的路径书写格式
#file = open('E:/MyCodes/python/tmp/test.txt','w')
#file.write('Hello, World!')

#字符串用法
what_he_does= ' plays '
his_instrument = ' guitar '
his_name = ' Robert Johnson '
artist_intro = his_name + what_he_does + his_instrument
print(artist_intro)
#
#查看变量类型
print(type(what_he_does))
print('变量c的类型是：', type(c))
#字符串相乘
words = 'words ' * 3
print(words)
#文字游戏——找出你朋友中的魔鬼
word = 'friends'
find_the_evil_in_your_friends = word[0] + word[2:4] + word[-3:-1]
#
print(find_the_evil_in_your_friends)
#
##电话号码--遮挡电话号码
phone_number = '182-1117-7292'
hiding_num = phone_number.replace(phone_number[:9],'*' * 9)
print(hiding_num)
#号码查找
print("--------------------------------------------")
search = '168'
num_a = '1386-168-0006'
num_b = '1681-222-0006'
print( search + ' is at ' + str(num_a.find(search)) + ' to ' + str(num_a.find(search)  + len(search))+ ' of num_a')
print(search + ' is at '+ str(num_b.find(search)) + ' to ' + str(num_b.find(search) + + len(search)) +' of num_b')



```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
