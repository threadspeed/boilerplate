---
title: python script sampling (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'sampling'


## python sampling

Python example: sampling

```python
### 采样少数类 ###
# 1.朴素随机过采样：从少数类的样本中进行随机采样来增加新的样本
# 通过简单的随机采样少数类的样本，使得每类样本比例为1：1：1
from sklearn.datasets import make_classification
from collections import Counter
X, y = make_classification(n_samples=5000, n_features=2, n_informative=2,
                           n_redundant=0, n_repeated=0, n_classes=3,
                           n_clusters_per_class=1,
                           weights=[0.01, 0.05, 0.94],
                           class_sep=0.8, random_state=0)
Counter(y)
# Counter({0: 64, 1: 262, 2: 4674})

from imblearn.over_sampling import RandomOverSampler
ros = RandomOverSampler(random_state=0)
X_resampled, y_resampled = ros.fit_sample(X, y)

sorted(Counter(y_resampled).items())
Out[13]:
# [(0, 4674), (1, 4674), (2, 4674)]

# 从随机过采样到SMOTE与ADASYN
# 2.Synthetic Minority Oversampling Technique(SMOTE)
# 3.Adaptive Synthetic(ADASYN)
from imblearn.over_sampling import SMOTE, ADASYN
X_resampled_smote, y_resampled_smote = SMOTE().fit_sample(X, y)
X_resampled_adasyn, y_resampled_adasyn = ADASYN().fit_sample(X,y)

# SMOTE函数中的kind参数控制了选择哪种变体 1）borderline1 2)borderline2 3)SVM
from imblearn.over_sampling import SMOTE, ADASYN
X_resampled, y_resampled = SMOTE(kind='borderline1').fit_sample(X, y)
clf_adasyn = LinearSVC().fit(X_resampled, y_resampled)

from imblearn.over_sampling import BorderlineSMOTE
X_resampled, y_resampled = BorderlineSMOTE().fit_sample(X, y)

SVMSMOTE 
KMeansSMOTE
SMOTENC # 对待不同的分类数据特征

### under-sampleing ###
#原型生成 prototype generation
ClusterCentroids：每一个类别的样本都会用K-Means算法的中心点来进行合成，而不是随机从原始样本中进行抽取；提供了一种高效的方法来减少样本数量，但要求原始数据集最好能聚类成簇，此外，中心点的数量应设置好，这样下采样的数据能很好地代表原始数据
# 原型选择 prototype selection
直接从原始数据集中进行抽取，分为the controlled under-sampling technique(可由用户指定下采样抽取的子集种样本的数量)和the cleaning under-sampling techniques(不接受用户的干预).
from imblearn.under_sampling import RandomUnderSampler
rus = RandomUnderSample(random_state=0) # replacement=True 实现自助法(boostrap)抽样，默认是不重复采样
X_resampled, y_resampled = rus.fit_sample(X, y)             

from imblearn.under_sampling import ClusterCentroids
cc = ClusterCentroids(random_state=0)
X_resampled, y_resampled = cc.fit_sample(X, y)


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
