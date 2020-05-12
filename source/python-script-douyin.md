---
title: python script douyin (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'douyin'


Modules used in program: 
* `import random`
* `import json`
* `import os`

## python douyin

Python example: douyin

```python
import os
import json
import random

path = "/Users/glow/Desktop/aa/douyin/json" # json 文件位置
files = os.listdir(path)

jueyou = {} # 存储抖音所有掘友的 ID 和留言内容 为词典
nameList = [] # 存储掘友 ID

for file in files:
     if not os.path.isdir(file):
        with open(path+"/"+file) as f:
            js = json.load(f)
            for content in js["notice_list"]:
                name = content["comment"]["comment"]["user"]["nickname"]
                comment = content["comment"]["comment"]["text"]
                jueyou[name] = comment
                nameList.append(name)

newNameList = list(set(nameList))
print("1024活动抖音参与评论数为：", len(nameList))
print("1024活动抖音参与总人数为：", len(newNameList))


for i in range(10):
    lucky = random.randint(1,len(newNameList)) - 1
    print("获得掘金笔记本的掘友抖音用户名是：%s 他的评论内容为：%s" % (newNameList[lucky], jueyou[newNameList[lucky]]))
    newNameList.pop(lucky) # 中奖就不进入下次奖池

for i in range(10):
    lucky = random.randint(1,len(newNameList)) - 1
    print("获得掘金鼠标垫的掘友抖音用户名是：%s 他的评论内容为：%s" % (newNameList[lucky], jueyou[newNameList[lucky]]))
    newNameList.pop(lucky) # 中奖就不进入下次奖池

for i in range(10):
    lucky = random.randint(1,len(newNameList)) - 1
    print("获得掘金水杯的掘友抖音用户名是：%s 他的评论内容为：%s" % (newNameList[lucky], jueyou[newNameList[lucky]]))
    newNameList.pop(lucky)

for i in range(5):
    lucky = random.randint(1,len(newNameList)) - 1
    print("获得掘金T恤的掘友抖音用户名是：%s 他的评论内容为：%s" % (newNameList[lucky], jueyou[newNameList[lucky]]))
    newNameList.pop(lucky)

for i in range(5):
    lucky = random.randint(1,len(newNameList)) - 1
    print("获得掘金大礼包的掘友抖音用户名是：%s 他的评论内容为：%s" % (newNameList[lucky], jueyou[newNameList[lucky]]))
    newNameList.pop(lucky)

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
