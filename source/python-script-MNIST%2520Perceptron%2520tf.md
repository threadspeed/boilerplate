---
title: python script MNIST%2520Perceptron%2520tf (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'MNIST%2520Perceptron%2520tf'


Modules used in program: 
* `import tensorflow as tf`

## python MNIST%2520Perceptron%2520tf

Python example: MNIST%2520Perceptron%2520tf

```python
#! python3
#This is a perceptron implementation written using tensor flow to learn basics of tensor flow
#from tensorflow.examples.tutorials.mnist import input_data
#mnist = input_data.read_data_sets("MNIST_data/", one_hot=True)
#(Train 55k / Test 10k / Validate 10k)
#structure of Data : x:mnist.train.images y:mnist.train.label
#mnist.train.images : rc [55000, 784]
#mnist.train.labels : rc [55000, 10]
#y=softmax(Wx+b)
from tensorflow.examples.tutorials.mnist import input_data
mnist = input_data.read_data_sets("MNIST_data/", one_hot=True)
import tensorflow as tf
x = tf.placeholder(tf.float32, [None, 784])
W = tf.Variable(tf.zeros([784, 10]))
b = tf.Variable(tf.zeros([10]))
y = tf.nn.softmax(tf.matmul(x, W) + b)
y_ = tf.placeholder(tf.float32, [None, 10])
cross_entropy = tf.reduce_mean(-tf.reduce_sum(y_ * tf.log(y), reduction_indices=[1]))
train_step = tf.train.GradientDescentOptimizer(0.5).minimize(cross_entropy)
sess = tf.InteractiveSession()
tf.global_variables_initializer().run()
for _ in range(1000):
    batch_xs, batch_ys = mnist.train.next_batch(100)
    sess.run(train_step, feed_dict={x: batch_xs, y_: batch_ys})
correct_prediction = tf.equal(tf.argmax(y,1), tf.argmax(y_,1))
accuracy = tf.reduce_mean(tf.cast(correct_prediction, tf.float32))
print(sess.run(accuracy, feed_dict={x: mnist.test.images, y_: mnist.test.labels}))


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
