---
title: python script tiff parse (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'tiff parse'


Modules used in program: 
* `import argparse`
* `import numpy as np`
* `import tifffile as tiff`

## python tiff parse

Python example: tiff parse

```python
#!/usr/bin/env python

import tifffile as tiff
import numpy as np
import argparse

parser = argparse.ArgumentParser()
parser.add_argument("tiff",help="your tiff file")
parser.add_argument("result",help="your result file")
args = parser.parse_args()

n_name = []
with tiff.TiffFile(args.tiff) as tifile, open(args.result,'w')  as  res:
        images = tifile.asarray()
        for page in tifile:
                name  = page.tags.values()
#               print(name[-2].name,name[-2].value    #document_name name)
#                print(name[-2].value)
                n_name.append(name[-2].value.split('.')[0])
		n_name.append('\00')
        f = np.array(n_name)
        res.write(f)

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
