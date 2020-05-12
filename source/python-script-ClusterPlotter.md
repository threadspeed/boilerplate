---
title: python script ClusterPlotter (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'ClusterPlotter'


Modules used in program: 
* `import numpy as np`
* `import matplotlib.pyplot as plt`

## python ClusterPlotter

Python mysql example: ClusterPlotter

```python
import matplotlib.pyplot as plt
import numpy as np
from KMeans import KMeans


class ClusterPlotter:

    @staticmethod
    def getColor(i):
        colors = ['r', 'b', 'g', 'orange', 'purple']
        return colors[i % colors.__len__()]

    @staticmethod
    def cartesian(clusters, centroids) -> None:
        for i, cluster in enumerate(clusters):
            npCluster = np.array(cluster).transpose()
            plt.scatter(npCluster[0], npCluster[1], color=ClusterPlotter.getColor(i))
            plt.scatter(centroids[i][0], centroids[i][1], color='#464646', marker='X', s=100)
        plt.title('K-Means Cluster')
        plt.show()


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
