---
title: python script imbalance (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'imbalance'

Functions in program: 
* `def get_resampled_df(df, y_col, count, strategy='max'):`
* `def get_resampled_count_dict(count_dict, count, strategy='max'):`
* `def get_class_weights(y, one_hot=False):`

Modules used in program: 
* `import pandas as pd`
* `import numpy as np`

## python imbalance

Python example: imbalance

```python
import numpy as np
import pandas as pd
from imblearn.over_sampling import RandomOverSampler
from imblearn.under_sampling import RandomUnderSampler
from sklearn.utils import class_weight


def get_class_weights(y, one_hot=False):
    """Returns a dict of class weights for label encoded as well as one-hot encoded y."""
    if one_hot:
        y = np.argmax(y, axis=1)
    class_weights = class_weight.compute_class_weight('balanced', np.unique(y), y)
    return dict(enumerate(class_weights))


def get_resampled_count_dict(count_dict, count, strategy='max'):
    """count_dict is df.y.value_counts()
    strategy:
    fixed - makes value to a fixed value
    min - makes value to a min value for those below it
    max - makes value to a max value for those above it
    """
    if not isinstance(count_dict, dict):
        count_dict = dict(count_dict)
    if strategy == 'max':
        return {k: min(v, count) for k, v in count_dict.items()}
    if strategy == 'min':
        return {k: max(v, count) for k, v in count_dict.items()}
    if strategy == 'fixed':
        return {k: count for k, v in count_dict.items()}


def get_resampled_df(df, y_col, count, strategy='max'):
    """Resampling dataframe for imbalanced dataset.
    count: The number used by strategy for sampling
    strategy:
    min - oversamples minority below the count for respective y
    max - undersamples majority over the count for respective y
    # TODO: fixed - makes same number of samples for all y
    """
    print('Dropping NA by %s.'%y_col)
    df = df.dropna(subset=[y_col])
    df = df.reset_index()
    vc = df[y_col].value_counts()

    y_count = vc[vc == count]
    df_count = df[df[y_col].isin(y_count.keys())]

    if strategy in ['fixed', 'min']:
        y_less = vc[vc < count]
        y_less = get_resampled_count_dict(y_less, count, strategy='min')
        sampler = RandomOverSampler(sampling_strategy=y_less, random_state=42)
        if strategy == 'fixed':
            temp = df[df[y_col].isin(y_less.keys())]
        else:
            temp = df

        x, y = np.arange(len(temp)), temp[y_col].values
        x = np.reshape(x, (-1, 1))
        _, _ = sampler.fit_resample(x, y)
        df_resampled = temp.iloc[sampler.sample_indices_]  # df_oversampled

    if strategy in ['fixed', 'max']:
        y_more = vc[vc > count]
        y_more = get_resampled_count_dict(y_more, count, strategy='max')
        sampler = RandomUnderSampler(sampling_strategy=y_more, random_state=42)
        if strategy == 'fixed':
            temp = df[df[y_col].isin(y_more.keys())]
        else:
            temp = df
        x, y = np.arange(len(temp)), temp[y_col].values
        x = np.reshape(x, (-1, 1))
        _, _ = sampler.fit_resample(x, y)
        df_undersampled = temp.iloc[sampler.sample_indices_]
        if strategy in ['fixed']:
            df_resampled = pd.concat([df_resampled, df_undersampled], ignore_index=False)
        else:
            df_resampled = df_undersampled

    return df_resampled.set_index('index')

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
