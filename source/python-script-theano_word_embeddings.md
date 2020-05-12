---
title: python script theano word embeddings (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'theano word embeddings'


Modules used in program: 
* `import random`
* `import numpy as np`
* `import theano.tensor as T`
* `import theano`

## python theano word embeddings

Python mysql example: theano word embeddings

```python
#!/usr/bin/env python
# see http://matpalm.com/blog/2015/03/28/theano_word_embeddings/
import theano
import theano.tensor as T
import numpy as np
import random

E = np.asarray(np.random.randn(6, 2), dtype='float32')
t_E = theano.shared(E)
t_idxs = T.ivector()
t_embedding_output = t_E[t_idxs]
t_dot_product = T.dot(t_embedding_output[0], t_embedding_output[1])
t_label = T.iscalar()
gradient = T.grad(cost=abs(t_label - t_dot_product), wrt=t_E)
updates = [(t_E, t_E - 0.01 * gradient)]
train = theano.function(inputs=[t_idxs, t_label], outputs=[], updates=updates)
print("i n d0 d1")
for i in range(0, 10000):
    v1, v2 = random.randint(0, 5), random.randint(0, 5)
    label = 1.0 if (v1/2 == v2/2) else 0.0
    train([v1, v2], label)
    if i % 100 == 0:
        for n, embedding in enumerate(t_E.get_value()):
            print(i, n, embedding[0], embedding[1])


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
