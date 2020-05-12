---
title: python script cv (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'cv'

Functions in program: 
* `def create_new_conv_layer(input_data, num_input_channels, num_filters, filter_shape, pool_shape, name):`
* `def load_obj(name ):`
* `def save_obj(obj, name ):`

Modules used in program: 
* `import tensorflow as tf`
* `import pickle`
* `import statistics`
* `import cv2`
* `import random`
* `import sys`
* `import pickle`
* `import glob `
* `import math`
* `import time`
* `import numpy as np`

## python cv

Python mysql example: cv

```python
#!/usr/bin/env python3
# -*- coding: utf-8 -*-
"""
Created on Fri Sep 14 16:28:23 2018

@author: shahrzad
"""

#!/usr/bin/env python3
# -*- coding: utf-8 -*-
"""
Created on Fri Sep 14 15:53:04 2018

@author: shahrzad
"""

import numpy as np
import time
import math
import glob 
from sklearn.ensemble import RandomForestClassifier
from sklearn.metrics import confusion_matrix
from collections import Counter        
import pickle
from sklearn.metrics import classification_report
from sklearn.metrics import roc_auc_score
import sys
import random
from matplotlib import pyplot as plt
import cv2
import statistics
import pickle

####################################
def save_obj(obj, name ):
    with open( name + '.pkl', 'wb') as f:
        pickle.dump(obj, f, pickle.HIGHEST_PROTOCOL)

def load_obj(name ):
    with open( name + '.pkl', 'rb') as f:
        return pickle.load(f)
#####################################################
            #receptor
#####################################################
size=20
receptors_folder='/home/shahrzad/src/DeepDrug/pockets_dude_tiff_'+str(size)
date_str='2018-08-26-0025'
#savepath='/home/shahrzad/src/DeepDrug/train_test_data/'+date_str+'/'
#default_stdout=sys.stdout

receptors = glob.glob(receptors_folder + '/*.tiff')
train_input=np.zeros((len(receptors)-1, 47,48))
train_labels=np.ones((len(receptors)-1,2))
test_input=np.zeros((1, 47,48))
test_labels=np.ones((1,2))

image_dict={}
k=1
trc=0
tec=0
for i in range(len(receptors)):
    filename = receptors[i]
    receptor=filename.split('.')[0].split('/')[-1][:-3]
    img = cv2.imread(filename,cv2.IMREAD_GRAYSCALE)
    image_dict[receptor]=img.reshape(-1,47*48)
    if img is None:
        print("error")


#####################################################
            #ligand
#####################################################
directory='/home/shahrzad/src/DeepDrug/'
date_str='2018-08-26-0025'

ligand_dict=load_obj(directory + 'train_test_data/'+date_str+'/receptorname_ligand_dict_'+str(date_str))
receptor_list=sorted(list(set([k.split('_')[0] for k in ligand_dict.keys()])))


all_dict=[]
for i in range(0,1):
    test_receptor=receptor_list[i]  
    print('test receptor: ',test_receptor)

    training_set_0=[]
    training_set_1=[]
    test_set_0=[]
    test_set_1=[]
    
    for k in ligand_dict.keys():
        if k.split('_')[0]!=test_receptor:
            if k.endswith('_0'):
                for r in ligand_dict[k]:
                    r_reshaped=np.reshape(np.asarray(r),[-1,166])
                    training_set_0.append(np.hstack((r_reshaped,image_dict[k.split('_')[0]])))
            else:
                for r in ligand_dict[k]:
                    r_reshaped=np.reshape(np.asarray(r),[-1,166])
                    training_set_1.append(np.hstack((r_reshaped,image_dict[k.split('_')[0]])))
        else:
            if k.endswith('_0'):
                for r in ligand_dict[k]:
                    r_reshaped=np.reshape(np.asarray(r),[-1,166])
                    test_set_0.append(np.hstack((r_reshaped,image_dict[k.split('_')[0]])))
            else:
                for r in ligand_dict[k]:
                    r_reshaped=np.reshape(np.asarray(r),[-1,166])
                    test_set_1.append(np.hstack((r_reshaped,image_dict[k.split('_')[0]])))

    j=0
    training_set=np.zeros((4*len(training_set_1), 166 + 47*48))
    training_labels=np.zeros((4*len(training_set_1),2))
    temp=random.sample(training_set_0, 2*len(training_set_1))

    for p in range(len(training_set_1)):
        training_set[p,:]=training_set_1[p]
        training_labels[p,0]=1
        training_set[len(training_set_1)+p,:]=training_set_1[p]
        training_labels[len(training_set_1)+p,1]=1
        
    for p in range(2*len(training_set_1)):
        training_set[2*len(training_set_1)+p,:]=temp[p]
        training_labels[len(training_set_1)+p,0]=1
        
    test_set=np.zeros((4*len(test_set_1), 166 + 47*48))
    test_labels=np.zeros((4*len(test_set_1),2))
    temp=random.sample(test_set_0, 2*len(test_set_1))

    for p in range(len(test_set_1)):
        test_set[p,:]=test_set_1[p]
        test_labels[p,0]=1
        test_set[len(test_set_1)+p,:]=test_set_1[p]
        test_labels[len(test_set_1)+p,1]=1
        
    for p in range(2*len(test_set_1)):
        test_set[2*len(test_set_1)+p,:]=temp[p]
        test_labels[len(test_set_1)+p,0]=1
    

import tensorflow as tf

def create_new_conv_layer(input_data, num_input_channels, num_filters, filter_shape, pool_shape, name):
    # setup the filter input shape for tf.nn.conv_2d
    conv_filt_shape = [filter_shape[0], filter_shape[1], num_input_channels,
                      num_filters]
    
    # initialise weights and bias for the filter
    weights = tf.Variable(tf.truncated_normal(conv_filt_shape, stddev=0.03),
                                      name=name+'_W')
    bias = tf.Variable(tf.truncated_normal([num_filters]), name=name+'_b')
    
    # setup the convolutional layer operation
    out_layer = tf.nn.conv2d(input_data, weights, [1, 1, 1, 1], padding='SAME')
    
    # add the bias
    out_layer += bias
    
    # apply a ReLU non-linear activation
    out_layer = tf.nn.relu(out_layer)
    
    # now perform max pooling
    ksize = [1, pool_shape[0], pool_shape[1], 1]
    strides = [1, 2, 2, 1]
    out_layer = tf.nn.max_pool(out_layer, ksize=ksize, strides=strides, 
                               padding='SAME')
    
    return out_layer


# Python optimisation variables
learning_rate = 0.0001
epochs = 2
batch_size = 10

# declare the training data placeholders
# input x - for 20 x 20 pixels = 400 - this is the flattened image data t
x = tf.placeholder(tf.float32, [None,47*48])
# dynamically reshape the input
x_shaped = tf.reshape(x, [-1, 47, 48, 1])
# now declare the output data placeholder - 2 classes
y = tf.placeholder(tf.float32, [None, 2])

# create some convolutional layers
layer1 = create_new_conv_layer(x_shaped, 1, 32, [5, 5], [2, 2], name='layer1')
layer2 = create_new_conv_layer(layer1, 32, 64, [5, 5], [2, 2], name='layer2')

flattened = tf.reshape(layer2, [-1, 12 * 12 * 64])
# setup some weights and bias values for this layer, then activate with ReLU
wd1 = tf.Variable(tf.truncated_normal([12 * 12 * 64, 1000], stddev=0.03), name='wd1')
bd1 = tf.Variable(tf.truncated_normal([1000], stddev=0.01), name='bd1')
dense_layer1 = tf.matmul(flattened, wd1) + bd1
dense_layer1 = tf.nn.relu(dense_layer1)

# another layer with softmax activations
wd2 = tf.Variable(tf.truncated_normal([1000, 2], stddev=0.03), name='wd2')
bd2 = tf.Variable(tf.truncated_normal([2], stddev=0.01), name='bd2')
dense_layer2 = tf.matmul(dense_layer1, wd2) + bd2
y_ = tf.nn.softmax(dense_layer2)

cross_entropy = tf.reduce_mean(tf.nn.softmax_cross_entropy_with_logits(logits=dense_layer2, labels=y))


# add an optimiser
optimiser = tf.train.AdamOptimizer(learning_rate=learning_rate).minimize(cross_entropy)

# define an accuracy assessment operation
correct_prediction = tf.equal(tf.argmax(y, 1), tf.argmax(y_, 1))
accuracy = tf.reduce_mean(tf.cast(correct_prediction, tf.float32))

# setup the initialisation operator
init_op = tf.global_variables_initializer()

with tf.Session() as sess:
    # initialise the variables
    sess.run(init_op)
    total_batch = int(len(train_labels) / batch_size)
    for epoch in range(epochs):
        avg_cost = 0
        for i in range(total_batch):
            batch_x, batch_y = training_set[i*batch_size:(i+1)*batch_size,166:], training_labels[i*batch_size:(i+1)*batch_size,:]
            _, c = sess.run([optimiser, cross_entropy], feed_dict={x: batch_x, y: batch_y})

            avg_cost += c / total_batch
        test_acc = sess.run(accuracy, feed_dict={x: test_set[:,166:], y: test_labels})
        print("Epoch:", (epoch + 1), "cost =", "{:.3f}".format(avg_cost), " test accuracy: {:.3f}".format(test_acc))
    
    print("\nTraining complete!")
    print(sess.run(accuracy, feed_dict={x: test_set[:,166:], y: test_labels}))


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
