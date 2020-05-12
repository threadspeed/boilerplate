---
title: python script windowing aggregations (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'windowing aggregations'

Functions in program: 
* `def windowing_between(dg, agg_col, dt_col, left_window_str, right_window_str):`
* `def windowing_aggreg(dg, agg_col, dt_col, window):`

## python windowing aggregations

Python mysql example: windowing aggregations

```python
def windowing_aggreg(dg, agg_col, dt_col, window):
    dgs = dg.sort(dt_col)
    s = pd.Series(index=dg[dt_col], data=dg[agg_col].values)
    return pd.rolling_mean(s, window).max()
    
def windowing_between(dg, agg_col, dt_col, left_window_str, right_window_str):
    dgf = dg[dg[dt_col].between(left_window_str, right_window_str)]
    return dgf[agg_col].sum()

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
