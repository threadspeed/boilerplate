---
title: python script markov (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'markov'

Functions in program: 
* `def make_sentence(dic):`
* `def word_choice(sel):`
* `def set_word3(dic, s3):`
* `def make_dic(words):`

Modules used in program: 
* `import random`
* `import json`
* `import json`

## python markov

Python mysql example: markov

```python
from janome.tokenizer import Tokenizer
import json

# テキストファイルを読み込む
sjis = open('rad_lyrics.txt', 'rb').read()
text = sjis.decode('utf_8')

# テキストを形態素解析読み込みます
t = Tokenizer()
words = t.tokenize(text)

# 辞書を生成
def make_dic(words):
    tmp = ["@"]
    dic = {}
    for i in words:
        word = i.surface
        if word == "" or word == "\r\n" or word == "\n": continue
        tmp.append(word)
        if len(tmp) < 3: continue
        if len(tmp) > 3: tmp = tmp[1:]
        set_word3(dic, tmp)
        if word == "。":
            tmp = ["@"]
            continue
    return dic

# 三要素のリストを辞書として登録
def set_word3(dic, s3):
    w1, w2, w3 = s3
    if not w1 in dic: dic[w1] = {}
    if not w2 in dic[w1]: dic[w1][w2] = {}
    if not w3 in dic[w1][w2]: dic[w1][w2][w3] = 0
    dic[w1][w2][w3] += 1

dic = make_dic(words)
json.dump(dic, open("markov-blog.json", "w", encoding="utf-8"))

##自動生成
import json
dic = open("markov-blog.json" , "r")
dic = json.load(dic)

tweets_list = []
import random
def word_choice(sel):
    keys = sel.keys()
    ran = random.choice(list(keys))
    return ran

def make_sentence(dic):
    ret = []
    if not "@" in dic: return "no dic"
    top = dic["@"]
    w1 = word_choice(top)
    w2 = word_choice(top[w1])
    ret.append(w1)
    ret.append(w2)
    while True:
        w3 = word_choice(dic[w1][w2])
        ret.append(w3)
        if w3 == "。": break
        w1, w2 = w2, w3
    tweets_list.append(ret)
    return "".join(ret)

for i in range(1):
    s = make_sentence(dic)
    tweets_list.append(s)
    print(s)


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
