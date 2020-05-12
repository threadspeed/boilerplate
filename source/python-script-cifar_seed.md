---
title: python script cifar seed (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'cifar seed'


Modules used in program: 
* `import random`
* `import time`
* `import csv`
* `import tensorflow as tf`
* `import numpy as np`
* `import random`
* `import os`
* `import sys`

## python cifar seed

Python example: cifar seed

```python
from __future__ import absolute_import, division, print_function, unicode_literals
import sys
from os.path import abspath
sys.path.append(abspath('.'))
import os
os.environ['PYTHONHASHSEED']=str(42)
os.environ["CUDA_VISIBLE_DEVICES"]="0"
import random
random.seed(0)

import numpy as np
np.random.seed(0)
np.random.RandomState(0)
import tensorflow as tf
tf.random.set_seed(0)
tf.compat.v1.disable_eager_execution()
import csv
from art.classifiers import KerasClassifier
from art.attacks import CarliniLInfMethod as cw
from art.attacks import ProjectedGradientDescent as pgd
import time
import random
from art.utils import load_dataset


# Configure a logger to capture ART outputs; these are printed in console and the level of detail is set to INFO

# Build and compile the discriminator
classifier_model = tf.keras.models.load_model('cifar_resnet.h5')

(x_train, y_train), (x_test, y_test), min_, max_ = load_dataset(str('cifar10'))
epsilon = .30

if __name__ == '__main__':
    classifier = KerasClassifier(clip_values=(0.0, 1.0), model=classifier_model, use_logits=False)
    attack_pgd = pgd(classifier, eps=epsilon, eps_step=epsilon/3, max_iter=40)
    attack_cw = cw(classifier, targeted=False, batch_size=128)
    adv_sample = 256
    for attack_method in [ attack_pgd, attack_cw ]:
        for run in range(31):
            print(' ----------------------------------------------run #' + str(run), flush = True)
            names = list(locals().keys())
            for name in names:
            	print(str(name) + ': ' + str(sys.getsizeof(locals()[name])), flush = True)
            attack_method.generate(x_train[:adv_sample])


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
