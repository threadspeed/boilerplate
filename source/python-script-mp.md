---
title: python script mp (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'mp'


Modules used in program: 
* `import random`
* `import json`
* `import os`

## python mp

Python example: mp

```python
import os
import json
import random

path = "/Users/panzimeng/Downloads/微信公众号/json" # json 文件位置
files = os.listdir(path)

jueyou = {} # 存储抖音所有掘友的 ID 和留言内容 为词典
nameList = [] # 存储掘友 ID

for file in files:
     if not os.path.isdir(file):
        with open(path+"/"+file) as f:
            js = json.load(f)
            data = json.loads(js["comment_list"])
            commentArray = data["comment"]
            for content in commentArray:
                name = content["nick_name"]
                comment = content["content"]
                jueyou[name] = comment
                nameList.append(name)


newNameList = list(set(nameList))
print("1024活动抖音参与评论数为：", len(nameList))
print("1024活动抖音参与总人数为：", len(newNameList))


for i in range(6):
    lucky = random.randint(1,len(newNameList)) - 1
    print("获得掘金笔记本的掘友用户名是：%s，留言内容为：%s" % (newNameList[lucky], jueyou[newNameList[lucky]]))
    newNameList.pop(lucky) # 中奖就不进入下次奖池

for i in range(6):
    lucky = random.randint(1,len(newNameList)) - 1
    print("获得掘金鼠标垫的掘友用户名是：%s，留言内容为：%s" % (newNameList[lucky], jueyou[newNameList[lucky]]))
    newNameList.pop(lucky) # 中奖就不进入下次奖池

for i in range(6):
    lucky = random.randint(1,len(newNameList)) - 1
    print("获得掘金水杯的掘友用户名是：%s，留言内容为：%s" % (newNameList[lucky], jueyou[newNameList[lucky]]))
    newNameList.pop(lucky) # 中奖就不进入下次奖池

for i in range(3):
    lucky = random.randint(1,len(newNameList)) - 1
    print("获得掘金大礼包的掘友用户名是：%s，留言内容为：%s" % (newNameList[lucky], jueyou[newNameList[lucky]]))
    newNameList.pop(lucky) # 中奖就不进入下次奖池

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
