---
title: python script pickleschreiber (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'pickleschreiber'


Modules used in program: 
* `import random`
* `import pickle`
* `import os`

## python pickleschreiber

Python example: pickleschreiber

```python
#python 3
import os
import pickle
import random
#variablen______________________________
verb ={}
adj={}
nom={} 
#variablen______________________________

##########################################################################################
verb["stehlen"]=["u","stehle","stielst","stiehlt","stehlen","stehlt","stehlen"]
verb["gehen"]=["r","geh"]
verb["schlagen"]=["u","schlage","schlägst","schlägt","schlagen","schlägt","schlagen"]
verb["rennen"]=["r","renn"]
verb["essen"]=["u","esse","isst","isst","essen","esst","essen"]
verb["schlafen"]=["u","schlafe","schläfst","schläft","schlafen","schlaft","schlafen"]
verb["werfen"]=["u","werfe","wirfst","wirft","werfen","werft","werfen"]
verb["fahren"]=["u","fahre","fährst","fährt","fahren","fahrt","fahren"]
verb["wissen"]=["u","weiß","weißt","weiß","wissen","wisst","wissen"]
adj["groß"]=["u","größer","größten"]
adj["klug"]=["u","klüger","klügsten"]
adj["intelligent"]=["u","intelligenter","Intelligentesten"]
adj["viel"]=["u""mehr","meisten"]
adj["wenig"]=["r"]
adj["dumm"]=["r"]
adj["klein"]=["r"]
adj["blau"]=["u","blauer","bläulichsten"]
nom["Geschwister"]=["p"]
nom["Lexikon"]=["b","s","Lexikas"]
nom["Leute"]=["p"]
nom["Wasser"]=["s","s"]
nom["Weltall"]=["b","s","Weltalle"]
nom["Kind"]=["b","s","Kinder"]
nom["Hans"]=["s","m"]
nom["Peter"]=["s","m"]
nom["Paul"]=["s","m"]
nom["Gerhard"]=["s","m"]
nom["Tom"]=["s","m"]
nom["Haus"]=["b","s"]
###############################################
with open("nom.adb","wb") as nomfile:
    pickle.dump(nom,nomfile,pickle.HIGHEST_PROTOCOL)
with open("verb.adb","wb") as verbfile:
    pickle.dump(verb,verbfile,pickle.HIGHEST_PROTOCOL)
with open("adj.adb","wb") as adjfile:
    pickle.dump(adj,adjfile,pickle.HIGHEST_PROTOCOL)




```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
