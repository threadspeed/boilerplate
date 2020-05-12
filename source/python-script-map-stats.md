---
title: python script map-stats (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'map-stats'

Functions in program: 
* `def mapped_dfs(paths):`
* `def get_freq_stats(vol):`
* `def main():`

Modules used in program: 
* `import string`
* `import random`
* `import numpy as np`
* `import pandas as pd`
* `import argparse`

## python map-stats

Python mysql example: map-stats

```python
from htrc_features import FeatureReader
import argparse
import pandas as pd
import numpy as np
import random
import string


def main():
    parser = argparse.ArgumentParser(description='Calculate Collection '
                                     'Frequency, Page Frequency, and Book '
                                     'Frequency for a set of EF files.')
    parser.add_argument('--outpath', type=str, default='pickles',
                        help='Directory to save pickles to.')
    parser.add_argument('files', type=str, nargs='+',
                        help='list of bzip\'d EF data files')

    args = parser.parse_args()
    
    df = mapped_dfs(args.files)
    # Save DF to a randomly generated pickle
    filename = ''.join(random.choice(string.ascii_uppercase + string.digits)
                       for _ in range(8))
    df.to_pickle("%s/%s.pickle" % (args.outpath, filename))


def get_freq_stats(vol):
    tf = vol.tokenlist(pos=False)
    tf.index = tf.index.droplevel(1).droplevel(0)
    # Calculate collection frequency (for this book), page frequency,
    # and book frequency
    grouped = tf.groupby('token', level=0)
    return grouped['count'].agg({'CF': np.sum, 'PF': len, 'BF': lambda x: 1})


def mapped_dfs(paths):
    fr = FeatureReader(paths)
    all_df = []
    for vol in fr.volumes():
        try:
            all_df.append(get_freq_stats(vol))
        except:
            continue
    return pd.concat(all_df)


if __name__ == '__main__':
    main()


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
