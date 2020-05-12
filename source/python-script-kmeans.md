---
title: python script kmeans (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'kmeans'


Modules used in program: 
* `import sys`
* `import random`
* `import rhinoscriptsyntax as rs`

## python kmeans

Python example: kmeans

```python
import rhinoscriptsyntax as rs
import random
import sys

#k means in rhino

class Kmeans():
    
    def __init__(self,_points,_cluster_num=3):
        
        #variables
        self.points = _points
        self.clusters = []
        
        self.points_num = len(_points)
        self.cluster_num = _cluster_num
        
        self.point_closest_cluster = []
        self.cluster_means = [[0.0]*3]*self.cluster_num
        
        #layer preparation
        layer_names = rs.LayerNames()
        
        if not 'cluster' in layer_names:
            rs.AddLayer('cluster',(255,255,255))
        
        for i in range(self.cluster_num):
            layer_name = 'cluster_'+str(i)
            if not layer_name in layer_names:
                rs.AddLayer(layer_name,rs.ColorHLSToRGB(((270/(self.cluster_num+1))*i,120,100)))
        
        # make clusters with random coordinates
        coord_range = [[sys.float_info.min,sys.float_info.max],[sys.float_info.min,sys.float_info.max]]         # [[minx,maxx],[miny,maxy]]
        for point in self.points:
            pc = rs.PointCoordinates(point)
            #x
            if pc[0] > coord_range[0][0]:
                coord_range[0][0] = pc[0]
            elif pc[0] < coord_range[0][1]:
                coord_range[0][1] = pc[0]
            #y
            if pc[1] > coord_range[1][0]:
                coord_range[1][0] = pc[1]
            elif pc[1] < coord_range[1][1]:
                coord_range[1][1] = pc[1]
        
        for i in range(self.cluster_num):
            cluster = rs.AddPoint([random.uniform(coord_range[0][0],coord_range[0][1]),random.uniform(coord_range[1][0],coord_range[1][1]),0.0])
            rs.ObjectLayer(cluster,'cluster')
            
            self.clusters.append(cluster)
            
        
        # assign random guid for closest cluster
        for point in self.points:
            self.point_closest_cluster.append(random.choice(self.clusters))
        
    
    def update_closest_cluster(self):
        
        #init point
        self.point_closest_cluster = []
        
        # records the guid of the closest cluster of all points
        for point in self.points:
            self.point_closest_cluster.append(rs.PointClosestObject(rs.PointCoordinates(point),self.clusters)[0])
        
        
    def update_cluster_means(self):
        
        #init
        self.cluster_means = [[0.0]*3]*self.cluster_num
        cluster_point_num = [0]*self.cluster_num
        
        # sum up the points
        for p_id in range(self.points_num):
            for c_id in range(self.cluster_num):
                if self.point_closest_cluster[p_id] is self.clusters[c_id]:
                    self.cluster_means[c_id] = rs.VectorAdd(self.cluster_means[c_id],rs.PointCoordinates(self.points[p_id]))
                    rs.ObjectLayer(self.points[p_id],'cluster_'+str(c_id))
                    cluster_point_num[c_id] += 1
        
        # divide by size
        for c_id in range(self.cluster_num):
            self.cluster_means[c_id] = rs.VectorDivide(self.cluster_means[c_id],float(cluster_point_num[c_id]))
            
            
    def update(self):
        
        self.update_closest_cluster()
        self.update_cluster_means()
     
    def move_cluster_to_mean(self,_velocity=0.01):
        
        
        for c_id in range(self.cluster_num):
            trans = rs.VectorScale(rs.VectorSubtract(self.cluster_means[c_id],rs.PointCoordinates(self.clusters[c_id])),_velocity)
            self.clusters[c_id] = rs.MoveObject(self.clusters[c_id],trans)
            
            


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
