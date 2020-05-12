---
title: python script K-means%2520Console Kmeans (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'K-means%2520Console Kmeans'


Modules used in program: 
* `import copy`
* `import random`
* `import time`

## python K-means%2520Console Kmeans

Python mysql example: K-means%2520Console Kmeans

```python
import time
import random
import copy
from statistics import mean

if __name__ == '__main__':
    print("Bienvenue sur l'application Calcul K-means")
    # Saisi des input
    n = 0
    while n <= 0:
        n = int(input("Donner le nombre d'objet : "))

    liste = []
    for i in range(n):
        liste.append(int(input("Donner le {} objet : ".format(i + 1))))

    print("La liste : ", liste)
    k = int(input("Donner 0 < K < {} : ".format(n)))
    print("K = ", k)

    # Affectation des clusters
    print("Affectation aléatoire des clusters...")
    time.sleep(2)
    cluster = [[] for i in range(k)]
    liste_tempo = copy.deepcopy(liste)
    for i in range(k):
        randomobjet = random.choice(liste_tempo)
        cluster[i].append(randomobjet)
        liste_tempo.remove(randomobjet)

    print(cluster)

    # Traitement des clusters
    mcluster = []
    for i in range(k):
        mcluster.append(mean(cluster[i]))
    # 2, 4, 6, 7, 8, 11, 13
    etat = 0
    while etat == 0:
        #   7, 8, 11, 13
        liste_tempo = copy.deepcopy(liste)

        for i in range(liste_tempo.__len__()):
            min = abs(mcluster[0] - liste_tempo[0])
            # Calcul distance manhattan
            for j in range(k):
                if (abs(mcluster[j] - liste_tempo[i])) <= min:
                    min = abs((mcluster[j] - liste_tempo[i]))
                    indicecluster = j
            # Supprimer les redondances
            for u in range(cluster.__len__()):
                if cluster[u].__contains__(liste_tempo[i]):
                    cluster[u].remove(liste_tempo[i])

            cluster[indicecluster].append(liste_tempo[i])
            # ReCalcul des moyenne
            for u in range(k):
                mcluster[u] = mean(cluster[u])
            print("Les Clusters", cluster)
            print("Les Moyennes des clusters", mcluster)
        liste_tempo2 = cluster


        if cluster == liste_tempo2:
            etat = 1


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
