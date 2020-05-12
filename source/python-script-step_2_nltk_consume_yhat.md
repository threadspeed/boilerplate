---
title: python script step 2 nltk consume yhat (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'step 2 nltk consume yhat'


Modules used in program: 
* `import random`

## python step 2 nltk consume yhat

Python mysql example: step 2 nltk consume yhat

```python
from yhat import Yhat
from nltk.corpus import movie_reviews
import random

# let's get some data to test with; just going to use the same data for simplicity
documents = [(list(movie_reviews.words(fileid)), category)
              for category in movie_reviews.categories()
              for fileid in movie_reviews.fileids(category)]

# so we get a mix of positive and negative reviews
random.shuffle(documents)

yh = Yhat("YOUR USERNAME/EMAIL", "YOUR APIKEY")

# iterate through the documents and execute on yhat
for doc, klass in documents:
    # making the document a big string
    doc = " ".join(doc)
    print(klass, "=>", yh.predict("movieReviewClassifier", 1, doc))



```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
