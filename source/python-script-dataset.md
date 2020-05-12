---
title: python script dataset (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'dataset'

Functions in program: 
* `def get_dataset_augmented():`
* `def augment_dataset():`
* `def _decode_onehot_dataset(one_hot_y):`
* `def _get_class(one_hot):#[0,0,0,1] - >3`
* `def get_onehot_dataset():`

Modules used in program: 
* `import numpy as np`

## python dataset

Python example: dataset

```python
# -*- coding: utf-8 -*
# аугментация датасета
import numpy as np
from sklearn.model_selection import train_test_split

from collections import Counter
from imblearn.over_sampling import RandomOverSampler
from imblearn.under_sampling import RandomUnderSampler

from utils import (
    open_pickle,
    save_set_to_pkl
)

RANDOM_STATE=433

# не забываем создать в проекте папку dataset и положить туда подлежащий аугментации датасет axis.pkl
raw_name = './dataset/axis.pkl'
test_name = './dataset/axis_test.pkl'
train_name = './dataset/axis_train.pkl'

def get_onehot_dataset():
    dict = open_pickle(path=raw_name)
    x = np.array(dict['x'])
    y = np.array(dict['y'])
    x = np.swapaxes(x,2,1) # время для кераса должно быть в позиции 1
    print(("x shape:" + str(x.shape)))
    print("y shape:" + str(y.shape))
    return x, y

def _get_class(one_hot):#[0,0,0,1] - >3
    return next((i for i, x in enumerate(one_hot) if x), len(one_hot))# индекс первого ненулевого итема в списке

def _decode_onehot_dataset(one_hot_y):
    no_one_hot_y = []
    for oh_y in one_hot_y:
        class_id = _get_class(oh_y)
        no_one_hot_y.append(class_id)
    return np.array(no_one_hot_y)

def augment_dataset():
    x, one_hot_y = get_onehot_dataset()
    ids_list = list(range(len(x)))
    ids = (np.array(ids_list)).reshape(-1, 1) # требуется двумерный масивчик, а у нас одномертный
    y = _decode_onehot_dataset(one_hot_y) # требуется классы а на ван хот коды классов
    # смотрим ситуацию с классами - насколько все плохо?
    print("исходная ситуация с классами:")
    print(sorted(Counter(y).items()))

    # честно балансируем весь сет - выкидываем излишки
    rus = RandomUnderSampler(random_state=RANDOM_STATE)
    ids_rus, y_rus = rus.fit_sample(ids, y)
    print("андерсемплинг на всем сете:")
    print(sorted(Counter(y_rus).items()))

    # выделяем пациентов которые попадут в тест - в тесте должен быть баланс
    _, ids_test, _, y_test = train_test_split(ids_rus, y_rus, test_size=0.33, random_state=RANDOM_STATE)
    ids_rus_t, y_rus_t = rus.fit_sample(ids_test, y_test)
    print("в тест есте осталось:")
    print(sorted(Counter(y_rus_t).items()))
    # обходим выделенных пациентов и складываем их в итоговый тестовы сет:
    X_test=[]
    Y_test=[]
    for id in ids_rus_t:
        ids_list.remove(id[0]) # вычеркиваем из списка всех тестовых пациентов...
        X_test.append(x[id[0]])
        Y_test.append(one_hot_y[id[0]])
    save_set_to_pkl(x=np.array(X_test),
                    y=np.array(Y_test),
                    name_pkl=test_name)

    # собираем всех пациентов, которые не попали в тест - кладем их в трейн
    print(("для трейна осталось пациентов - " + str(len(ids_list))))
    ids_train = (np.array(ids_list)).reshape(-1, 1)  # требуется двумерный масивчик, а у нас одномертный
    y_train = []
    for id in ids_train:
        y_train.append(y[id[0]])
    y_train = np.array(y_train)
    print("ситуация с классами в трейне при этом:")
    print(sorted(Counter(y_train).items()))

    # аугментим трейновую часть
    ros = RandomOverSampler(random_state=RANDOM_STATE)
    ids_train_ros, y_train_ros = ros.fit_sample(ids_train, y_train)
    print("после андерсемплинга в трейне имеем:")
    print(sorted(Counter(y_train_ros).items()))

    # сохраняем трейновый сет в файл
    X_train = []
    Y_train = []
    for id in ids_train_ros:
        X_train.append(x[id[0]])
        Y_train.append(one_hot_y[id[0]])
    save_set_to_pkl(x=np.array(X_train),
                    y=np.array(Y_train),
                    name_pkl=train_name)


def get_dataset_augmented():
    test_set = open_pickle(test_name)
    train_set = open_pickle(train_name)
    return train_set, test_set

if __name__ == "__main__":
    augment_dataset()
    get_dataset_augmented()

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
