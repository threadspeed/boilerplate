---
title: python script runit (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'runit'

Functions in program: 
* `def nextword(target, source):`
* `def generate_the_word(infile):`
* `def random_the_word(infile):`

Modules used in program: 
* `import random`
* `import runitdb`
* `import sqlite3`
* `import random`

## python runit

Python example: runit

```python
"""
This file does strange stuff. It will find a random sentence then store the first 
word of that sentence, then it will randomly search text for that word, then record 
the following word.
The words are recorded in a file and in a sqlite database. Basically it builds a collection 
of words that follow words.
One goal is to find the most common two, three and four word combinations

"""


import random
from time import sleep
import sqlite3
import runitdb
database = "runit.db"
conn = sqlite3.connect(database)
conn.text_factory = lambda x: unicode(x, "utf-8", "ignore")
c = conn.cursor()
c.execute("""
CREATE VIRTUAL TABLE IF NOT EXISTS runit 
USING FTS4(target, targetS);
""")
conn.commit()
conn.close()

import random
def random_the_word(infile):
        with open(infile) as f:
            contents_file = f.read()
        lines = contents_file.splitlines()
        linenumber = random.randrange(0, len(lines))
        return lines[linenumber]

def generate_the_word(infile):
        with open(infile) as f:
            contents_of_file = f.read()
        lines = contents_of_file.splitlines()
        line_number = random.randrange(0, len(lines))
        return lines[line_number]


def nextword(target, source):
    for i, w in enumerate(source): 
        if w == target: 
            return source[i],source[i+1] 

TARG = ""
# Use a "very large" text file for random sentences/ lines 
infile ="Allperfect.txt"
count = 0
target_list = set()

# Use a "very large" text file for random sentences/ lines 
infile = "/home/jack/Desktop/text_stuff/ALL_WIKI_GOOD.txt"    
line = random_the_word(infile) 
target = line.split(' ', 1)[0] 
#Target = open("Target.txt", "a")
# target = "The"
while count < 3000:
    #sleep(.21)
    s = generate_the_word(infile)
    source = s.split()
    #target = "".join(target)
    #target = target.strip()
    target_list.add(target)
    
    target_list.add(target)
    targetS = target,"\n"
    targetS = str(targetS)
    #record the findings
    Target = open("Target.txt", "a")
    Target.write(targetS)    
    
    
    TARG = nextword(target, source)
    
    if TARG > "":
        TARG = nextword(target, source)
        target = TARG[-1]
        db_file= "runit.db"
        runitdb.create_or_open_db(db_file)
        runitdb.Insert(db_file, target, targetS)
        #target_list.add(target)
        #targetS = target
        #targetS = str(targetS)
        #entry = "".join(target)
        #Target.write(targetS)
        print(target)
        count = 101
    else:
        #sleep(.21)
        count = count +1 
        
asn = " ".join(target_list)
asn = asn+"\n"
Target = open("Target.txt", "a")
Target.write(asn)        

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
