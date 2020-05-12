---
title: python script elapsedTimeDataAggrWithJoin (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'elapsedTimeDataAggrWithJoin'


Modules used in program: 
* `import string`
* `import random`
* `import numpy as np`
* `import pandas as pd`
* `import timeit`

## python elapsedTimeDataAggrWithJoin

Python mysql example: elapsedTimeDataAggrWithJoin

```python
import timeit


createTable = '''
import pandas as pd
import numpy as np
import random
import string
rowCount = 100*1000
t = pd.DataFrame({'bucket': [''.join(random.choices(string.ascii_lowercase, k=2)) for _ in range(rowCount)],
                  'weight': [random.uniform(0, 2) for _ in range(rowCount)],
                  'qty': [random.randint(0, 100) for _ in range(rowCount)],
                  'risk': [random.randint(0, 10) for _ in range(rowCount)]})
'''

aggrWithJoin = '''
res = t.groupby('bucket').agg({'bucket': len, 'qty': [sum, np.mean], 'risk': [sum, np.mean]})
res.columns = res.columns.map('_'.join)
res.rename(columns={'bucket_len': 'NR', 'qty_sum': 'TOTAL_QTY', 'qty_mean': 'AVG_QTY',
                        'risk_sum': 'TOTAL_RISK', 'risk_mean': 'AVG_RISK'}).join(
        t.groupby('bucket').apply(lambda g: np.average(g.qty, weights=g.weight)).to_frame('W_AVG_QTY')).join(
        t.groupby('bucket').apply(lambda g: np.average(g.risk, weights=g.weight)).to_frame('W_AVG_RISK')
)
'''

print("Python with Join 1:", timeit.timeit(setup=createTable, stmt=aggrWithJoin, number = 100))



```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
