---
title: python script decode a web page (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'decode a web page'


Modules used in program: 
* `import requests`

## python decode a web page

Python mysql example: decode a web page

```python
import requests
from bs4 import BeautifulSoup

url = 'https://www.google.com'
r = requests.get(url)
r_html = r.text

soup = BeautifulSoup(r_html)
title = soup.find('span', 'articletitle').string

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
