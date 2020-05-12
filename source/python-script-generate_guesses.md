---
title: python script generate guesses (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'generate guesses'


Modules used in program: 
* `import uuid`
* `import synapseclient`
* `import random`
* `import os`
* `import filecmp`

## python generate guesses

Python example: generate guesses

```python
import filecmp
import os
import random
import synapseclient
from synapseclient import Activity, File, Folder, Project
import uuid

## create synapse object and log in
syn = synapseclient.Synapse()
syn.login()

## store this script in Synapse
code_folder_id = 'syn1937669'

## find or create the synapse entity representing this script
filename = os.path.basename(os.path.abspath(__file__))
results = syn.query('select id from entity where parentId=="%s" and name=="%s"' % (code_folder_id, filename,))
if results['totalNumberOfResults'] == 0:
    raise Exception('Need to add code entity to folder %s' % code_folder_id)
this_script = results['results'][0]['entity.id']

# this_script = File(os.path.abspath(__file__), description='generate random guesses', parentId=code_folder_id)
# this_script = syn.store(this_script)

## The activity represents the provenance of our guesses
ran_this_script = Activity(executed=this_script)

## get the evaluation queue
eid = 1901877
evaluation = syn.getEvaluation(eid)

## put entries here
entries_folder_id = 'syn1901907'

## generate entries
for i in range(0,5):
    guess = sorted([random.randrange(1,60) for z in range(0,5)])
    filename = 'entry-%s.txt' % (str(uuid.uuid4()))
    with open(filename, 'w') as f:
        f.write(', '.join([str(x) for x in guess]))
        f.write('\n')
    entry = File(filename, description='randomly generated guess', parentId=entries_folder_id)
    entry = syn.store(entry, activity=ran_this_script)
    syn.submit(evaluation, entry)



```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
