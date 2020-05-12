---
title: python script KMeans (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'KMeans'


Modules used in program: 
* `import random as rand`
* `import numpy as np`

## python KMeans

Python example: KMeans

```python
import numpy as np
import random as rand


class KMeans:
    # Maximum runs K-Means should perform
    __RUN_TRESHOLD = 100
    # To wich difference K-Means should aim for (if distance between old and new centroids is smaller, break)
    __DISTANCE_TRESHOLD = 0.001

    def __init__(self, coordinates, k):
        self.coordinates = coordinates
        self.k = k
        self.centroids = KMeans.getRandomCentroids(coordinates, k)
        self.clusters = KMeans.empytClusters(k)

        # Contains Callbacks which are getting called after every clustering - see KMeans.__onCluster()
        self.__onClusterListeners = []

    def run(self) -> int:
        """
        Calls self.cluster until the __RUN_TRESHOLD or __DISTANCE_TRESHOLD gets reached
        :return: number of self.cluster calls
        """
        difference = self.__DISTANCE_TRESHOLD + 1
        runs = 0
        while runs < self.__RUN_TRESHOLD and difference > self.__DISTANCE_TRESHOLD:
            difference = 0
            oldCentroids = self.centroids.copy()
            self.__cluster()
            for i, c in enumerate(self.clusters):
                self.centroids[i] = KMeans.meanOfCluster(c)
                difference += KMeans.distanceOfTuples(oldCentroids[i], self.centroids[i])
            difference = difference / self.k
            runs += 1
        return runs

    def __cluster(self):
        """
        Clusters the data according to the chosen centroids
        """
        self.clusters = KMeans.empytClusters(self.k)
        for point in self.coordinates:
            distances = []
            for centroid in self.centroids:
                distances.append(KMeans.distanceOfTuples(point, centroid))
            minIndex = distances.index(np.min(distances))
            self.clusters[minIndex].append(point)
        self.__onCluster()

    # ----- Status Functions for educational purposes -----
    def status(self) -> object:
        """
        Returns the current status of K-Means Clustersing
        :return: {coordinates, centroids, clusters, cluster_member_count, coordinates_count}
        """
        cluster_member_count = []
        for c in self.clusters:
            cluster_member_count.append(c.__len__())
        return {
            "coordinates": self.coordinates,
            "centroids": self.centroids,
            "clusters": self.clusters,
            "cluster_member_count": cluster_member_count,
            "coordinates_count": self.coordinates.__len__()
        }

    def __onCluster(self):
        """
        Runs the callbacks in self.__onClusterListeners
        """
        for l in self.__onClusterListeners:
            l(self.status())

    def onCluster(self, callback):
        """
        registers a callback for self.__onCluster
        :param callback: the callback to be called after every self.cluster()
        """
        self.__onClusterListeners.append(callback)

    # ----- static helper functions
    @staticmethod
    def getRandomCentroids(coordinates, k):
        """
        Generates _k_ random centroids to given coordinates
        :param coordinates: Coordinates as Tuple[]
        :param k: how many centroids to generate
        :return: A Tuple[] with the centroids
        """
        transposed = np.array(coordinates).transpose()
        x = transposed[0]
        y = transposed[1]

        centroids = []
        maxValue = [int(np.max(x)), int(np.max(y))]
        minValue = [int(np.min(x)), int(np.min(y))]
        for i in range(k):
            centroids.append([
                rand.randint(minValue[0], maxValue[0]),
                rand.randint(minValue[1], maxValue[1])
            ])
        return centroids

    @staticmethod
    def empytClusters(k):
        """
        Returns an Array with _k_ empty Arrays
        :param k: how many empty arrays to generate
        :return: Array of empty Arrays
        """
        clusters = []
        for i in range(k):
            clusters.append([])
        return clusters

    @staticmethod
    def distanceOfTuples(p1, p2):
        """
        calculates the distance between two points
        :param p1: Point 1 as [x, y]
        :param p2: Point 2 as [x, y]
        :return: distance between the two points as number
        """
        if p1 is None or p2 is None:
            return 0
        return np.linalg.norm(np.array(p1) - np.array(p2))

    @staticmethod
    def meanOfCluster(cluster):
        """
        calculates the Center of Mass - see (Wikipedia)[https://en.wikipedia.org/wiki/Center_of_mass#Definition]
        :param cluster: The Tuple[] to calculate the Center of
        :return: the Center of the Cluster as Tuple[]
        """
        n = cluster.__len__()
        if n <= 0:
            return
        transposed = np.array(cluster).transpose()
        c = 1 / cluster.__len__()
        x = sum(transposed[0]) * c
        y = sum(transposed[1]) * c
        return [x, y]


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
