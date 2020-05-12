---
title: python script step 1 nltk yhat example (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'step 1 nltk yhat example'

Functions in program: 
* `def document_features(document): `

Modules used in program: 
* `import random`
* `import nltk`

## python step 1 nltk yhat example

Python example: step 1 nltk yhat example

```python
import nltk
from nltk.corpus import movie_reviews
import random
from yhat import Yhat, BaseModel# pip install yhat

# import some movie data from nltk
documents = [(list(movie_reviews.words(fileid)), category)
              for category in movie_reviews.categories()
              for fileid in movie_reviews.fileids(category)]

# randomize the trial
random.shuffle(documents)

# only use the 2000 most common words
all_words = nltk.FreqDist(w.lower() for w in movie_reviews.words())
word_features = all_words.keys()[:2000] 

# create a feature extractor
def document_features(document): 
    document_words = set(document) 
    features = {}
    for word in word_features:
        features['contains(%s)' % word] = (word in document_words)
    return features


# extract features and define a training and test set
featuresets = [(document_features(d), c) for (d,c) in documents]
train_set, test_set = featuresets[100:], featuresets[:100]

# train the classifier
classifier = nltk.NaiveBayesClassifier.train(train_set)

# check to see how it works
print(nltk.classify.accuracy(classifier, test_set))


# start of yhat specific code
class TextClassifier(BaseModel):
    def transform(self, raw_data):
        document_words = set(raw_data.lower().split()) 
        features = {}
        for word in self.word_features:
            features['contains(%s)' % word] = (word in document_words)
        return features

    def predict(self, data):
        preds = self.classifier.prob_classify(data)
        response = {"probability": {}}
        for klass in preds.samples():
            response["probability"][klass] = preds.prob(klass)

        return response

# create a class that extends the yhat.BaseModel object
tc = TextClassifier(word_features=word_features, classifier=classifier)
# login to yhat
yh = Yhat("YOUR USERNAME/EMAIL", "YOUR APIKEY")

# upload to yhat
print("uploading now...")
print(yh.upload("movieReviewClassifier", tc))

# test on a new document
# assuming that you want to do the tokenization yourself so i'm making this a big string
doc, _ = documents[-1]
doc = " ".join(doc)
print(yh.predict("movieReviewClassifier", 1, doc))





```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
