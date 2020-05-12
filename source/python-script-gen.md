---
title: python script gen (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'gen'


Modules used in program: 
* `import random`
* `import sys `
* `import time `

## python gen

Python mysql example: gen

```python
# Repos: https://bitbucket.org/Sharkbyteprojects/passwordgenerator/
# Lizenz: https://bitbucket.org/Sharkbyteprojects/passwordgenerator/raw/6eb05bf88a03b5856fc7764470e4ff693c37f8a5/LICENSE
import time 
import sys 
import random
geladene_daten = ['1','2','3','4','5','6','7','8','9','0','q','w','e','r','t','z','u','i','o','p','a','s','d','f','g','h','j','k','l','y','x','c','v','b','n','m','.',',',';',':','_','-','@','!','"','§','%','&','/','(',')','=','?','#','*','+','~','Q','W','E','R','T','Z','U','I','O','P','A','S','D','F','G','H','J','K','L','Y','X','C','V','B','N','M','<','>','|','°']
choice = (random.choice(geladene_daten) + random.choice(geladene_daten) + random.choice(geladene_daten) + random.choice(geladene_daten)+ random.choice(geladene_daten)+ random.choice(geladene_daten)+ random.choice(geladene_daten)+ random.choice(geladene_daten)+ random.choice(geladene_daten)+ random.choice(geladene_daten)+ random.choice(geladene_daten)+ random.choice(geladene_daten)+ random.choice(geladene_daten)+ random.choice(geladene_daten)+ random.choice(geladene_daten)+ random.choice(geladene_daten)+ random.choice(geladene_daten)+ random.choice(geladene_daten))
title = 'Sicheres Password'
print("Sicheres Passwort: ")
print(choice)
time.sleep(2)
print("Zum Schliessen Enter Drücken")
sys.stdin.readline(0)


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
