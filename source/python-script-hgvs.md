---
title: python script hgvs (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'hgvs'


Modules used in program: 
* `import unicodedata`
* `import codecs`
* `import json`
* `import sys`
* `import re`
* `import urllib.request`

## python hgvs

Python mysql example: hgvs

```python
import urllib.request
import re
import sys
import json
import codecs
## Den anagnorize unicode sta linux para to 'encoding='utf-8' ##
import unicodedata
#### Passing command line args. Remove '#' and comment out 'testing' region to 
## gene_name = sys.argv[1]
## size = sys.argv[2]

## For testing
gene_name = 'BRCA1'
size = '500'

## Downloading Data. Den 3erw an to query einai swsto,
## pantws bgazei results otan to ekana cpoy paste se browser
link = 'http://www.ebi.ac.uk/europepmc/webservices/rest/search?query=mutation+{}&resulttype=core&pageSize={}&format=json'.format(gene_name, size)
filename = 'abstracts.json'
urllib.request.urlretrieve(link, filename)
## Opening abstracts with utf-8 encoding
with codecs.open('abstracts.json', encoding='utf-8') as f:
        data = json.load(f)
## Output filename
output = open('result.txt', 'w+', encoding = 'utf-8')

## Where the magic starts!!
for x in data['resultList']['result']:
    if 'abstractText' in x.keys():
        x['abstractText'] = unicodedata.normalize("NFKD",x['abstractText'])
        all_hvgs_temp = re.findall(r'[cgp]\.[\d]+...........', x['abstractText']  )
        title = x['title']
        for y in all_hvgs_temp:
            if '>' in y:
                ## print( 'Found substitution\n  y: {}'.format(y.replace(' ','')) )
                category = 'Substitution'
                searching = re.search(r'([cgp]\.[\d]+[_\-\+]?[[\d]+]?([ACGT])>[ACGT]).+', y.replace(' ','') )
                if searching:
                    name  = searching.group(1)
                    refseq = searching.group(2)
                    output.write('{}\t{}\t{}\t{}\n'.format(name, title, category, refseq) )
                else: 
                    print( 'Mutation has a bad format: {} \n'.format(y))
                    continue
            elif 'ins' in y:
                ## print( 'Found insertion\n  y: {}'.format(y.replace(' ','')) )
                category = 'Insertion'
                searching = re.search(r'([cgp]\.[\d]+[_\-\+]?[[\d]+]?ins[ACGT]+)', y.replace(' ',''))
                if searching:
                    name = searching.group(1)
                    refseq = '-'
                    output.write('{}\t{}\t{}\t{}\n'.format(name, title, category, refseq) )
                else:
                    print( 'Mutation has a bad format: {} \n'.format(y))
                    continue
            elif 'del' in y:
                ## print( 'Found deletion\n y: {}'.format(y.replace(' ','')) )
                category = 'Deletion'
                searching = re.search(r'([cgp]\.[\d]+[_\-\+]?[[\d]+]?del([ACGT]+)?)', y.replace(' ',''))
                ## print( searching )
                if searching:
                    name = searching.group(1)
                    refseq = searching.group(2)
                    output.write('{}\t{}\t{}\t{}\n'.format(name, title, category, refseq) )
                else:
                    print( 'Mutation has a bad format: {} \n'.format(y))
                    continue
            elif 'dup' in y:
                ## print( 'Found duplication\n  y: {}'.format(y.replace(' ','')) )
                category = 'Duplication'
                searching = re.search(r'([cgp]\.[\d]+[_\-\+]?[[\d]+]?dup([ACGT]+)?)', y.replace(' ',''))
                if searching:
                    name = searching.group(1)
                    refseq = searching.group(2)
                    ## print( '{}\t{}\t{}\t{}\n'.format(name, title, category, refseq) )
                    output.write('{}\t{}\t{}\t{}\n'.format(name, title, category, refseq) )
                else:
                    print( 'Mutation has a bad format: {} \n'.format(y))
                    continue
## 8a kanw attach kai ta files opou to testarw
output.close()




```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
