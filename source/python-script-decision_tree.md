---
title: python script decision tree (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'decision tree'


Modules used in program: 
* `import numpy`

## python decision tree

Python example: decision tree

```python
# coding: utf-8

from itertools import combinations
import numpy


class FeatureComparisonTree:

    def __init__(self, samples, targets, impurity=None, max_depth=None, groups=[]):
        self.samples = samples
        self.targets = targets
        self.classes = numpy.unique(targets)
        self.impurity = impurity if impurity else self.gini_impurity(targets)
        self.max_depth = max_depth
        self.groups = groups
        self.feature = None
        self.feature_pair = None
        self.label = None

    def split_node(self):
        if self.classes.shape[0] == 1:
            self.label = self.classes[0]
            return

        if self.max_depth == 0:
            self.label_by_vote()
            return

        single_split = self.single_feature_split_point()
        pair_split = self.inter_feature_comparison_split()

        if single_split['info_gain'] == pair_split['info_gain'] == 0:
            self.label_by_vote()
            return

        if single_split['info_gain'] < pair_split['info_gain']:
            self.feature_pair = pair_split['feature_pair']
            samples_l = self.samples[self.samples[:, self.feature_pair[0]] <= self.samples[:, self.feature_pair[1]]]
            samples_r = self.samples[self.samples[:, self.feature_pair[0]] > self.samples[:, self.feature_pair[1]]]
            split_info = pair_split
        else:
            self.feature = single_split['feature']
            self.threshold = single_split['threshold']
            samples_l = self.samples[self.samples[:, self.feature] <= self.threshold]
            samples_r = self.samples[self.samples[:, self.feature] > self.threshold]
            split_info = single_split

        self.left = FeatureComparisonTree(samples_l, split_info['targets_l'], split_info['impurity_l'], self.max_depth - 1, self.groups)
        self.right = FeatureComparisonTree(samples_r, split_info['targets_r'], split_info['impurity_r'], self.max_depth - 1, self.groups)
        self.left.split_node()
        self.right.split_node()

        # メモリ節約のため、最下層のノードが持つデータ以外は捨てる
        self.samples = None
        self.targets = None
        self.classes = None

    def add_depth(self):
        # 深さを増やす
        self.max_depth += 1
        if self.label is not None:
            self.label = None
            self.split_node()
        else:
            self.left.add_depth()
            self.right.add_depth()

    def gini_impurity(self, targets):
        n_samples = targets.shape[0]
        classes = numpy.unique(targets)

        impurity = 1
        n_samples_in_last_class = n_samples
        for i in range(len(classes) - 1):
            n_samples_in_class = targets[targets == classes[i]].shape[0]
            impurity -= (n_samples_in_class / n_samples) ** 2
            n_samples_in_last_class -= n_samples_in_class
        impurity -= (n_samples_in_last_class / n_samples) ** 2

        return impurity

    def single_feature_split_point(self):
        best_split_point = {
            'info_gain': 0,
            'feature': None,
            'threshold': None,
            'targets_l': None,
            'targets_r': None,
            'impurity_l': None,
            'impurity_r': None
        }

        n_samples = float(self.samples.shape[0])
        for f_idx in range(self.samples.shape[1]):
            uniq_feature = numpy.unique(self.samples[:, f_idx])
            if uniq_feature.shape[0] == 1:
                continue
            split_points = (uniq_feature[:-1] + uniq_feature[1:]) / 2.0
            for th_candidate in split_points:
                targets_l = self.targets[self.samples[:, f_idx] <= th_candidate]
                targets_r = self.targets[self.samples[:, f_idx] > th_candidate]
                impurity_l = self.gini_impurity(targets_l)
                impurity_r = self.gini_impurity(targets_r)
                info_gain = self.impurity \
                          - impurity_l * targets_l.shape[0]/n_samples \
                          - impurity_r * targets_r.shape[0]/n_samples
                if info_gain > best_split_point['info_gain']:
                    best_split_point = {
                        'info_gain': info_gain,
                        'feature': f_idx,
                        'threshold': th_candidate,
                        'targets_l': targets_l,
                        'targets_r': targets_r,
                        'impurity_l': impurity_l,
                        'impurity_r': impurity_r
                    }

        return best_split_point

    def inter_feature_comparison_split(self):
        best_split_point = {
            'info_gain': 0,
            'feature_pair': None,
            'targets_l': None,
            'targets_r': None,
            'impurity_l': None,
            'impurity_r':None
        }

        n_samples = float(self.samples.shape[0])
        for group in self.groups:
            for feature1, feature2 in combinations(group, 2):
                targets_l = self.targets[self.samples[:, feature1] <= self.samples[:, feature2]]
                if targets_l.shape[0] in (self.targets.shape[0], 0):
                    continue
                targets_r = self.targets[self.samples[:, feature1] > self.samples[:, feature2]]
                impurity_l = self.gini_impurity(targets_l)
                impurity_r = self.gini_impurity(targets_r)
                info_gain = self.impurity \
                          - impurity_l * targets_l.shape[0]/n_samples \
                          - impurity_r * targets_r.shape[0]/n_samples
                if info_gain > best_split_point['info_gain']:
                    best_split_point = {
                        'info_gain': info_gain,
                        'feature_pair': (feature1, feature2),
                        'targets_l': targets_l,
                        'targets_r': targets_r,
                        'impurity_l': impurity_l,
                        'impurity_r': impurity_r
                }

        return best_split_point

    def label_by_vote(self):
        largest_class = 0
        largest_count = 0
        for c in self.classes:
            nc = self.targets[self.targets == c].shape[0]
            if nc > largest_count:
                largest_class = c
                largest_count = nc
        self.label = largest_class

    def predict(self, samples):
        predictions = []
        for sample in samples:
            predictions.append(self.predict_one(sample))
        return numpy.array(predictions)

    def predict_one(self, sample):
        if self.label is not None:
            return self.label

        if self.feature is not None:
            if sample[self.feature] <= self.threshold:
                return self.left.predict_one(sample)
            else:
                return self.right.predict_one(sample)
        elif self.feature_pair is not None:
            if sample[self.feature_pair[0]] <= sample[self.feature_pair[1]]:
                return self.left.predict_one(sample)
            else:
                return self.right.predict_one(sample)
        else:
            raise Exception('なんかバグってる')

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
