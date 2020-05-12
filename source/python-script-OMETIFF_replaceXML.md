---
title: python script OMETIFF replaceXML (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'OMETIFF replaceXML'


## python OMETIFF replaceXML

Python example: OMETIFF replaceXML

```python
#from loci.formats.tools import TiffComment as TC
from loci.formats.tiff import TiffParser
from loci.formats.tiff import TiffSaver
from loci.common import DataTools
from loci.common import RandomAccessInputStream
from loci.common import RandomAccessOutputStream

filepath = '/Users/miura/Desktop/test.ome.tif'

# reading out
comment = TiffParser(filepath).getComment()
print(comment)

# replacing OME-XML
xmlpath = '/Users/miura/Desktop/ometest.xml'
newComment = DataTools.readFile(xmlpath)
filein = RandomAccessInputStream(filepath)
fileout = RandomAccessOutputStream(filepath)
saver = TiffSaver(fileout, filepath)
saver.overwriteComment(filein, newComment)
filein.close()
fileout.close()

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
