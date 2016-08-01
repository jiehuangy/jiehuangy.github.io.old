---
layout: post
title: "tensorflow basic tutorial"
date: 2016-08-01 15:22:38 +0800
comments: true
categories: "Tensorflow"
---
 
{% img center /images/2016-08-01-tensorflow-basic-tutorial-tensorflow.jpg 612 256 %}
<!--more-->

- list element with functor item
{:toc}

### Tensors
TensorFlow programs use a tensor data structure to represent all data -- only tensors are passed between operations in the computation graph. You can think of a TensorFlow tensor as an n-dimensional array or list. 

### Variables
A Variable is a modifiable tensor that lives in TensorFlow's graph of interacting operations. It can be used and even modified by the computation.

{% coderay lang:python Tensors & Variables %}
>>> x = tf.Variable([1.0, 2.0])
<tensorflow.python.ops.variables.Variable object at 0x117cfd790>
>>> a = tf.constant([3.0, 3.0])
<tf.Tensor 'Const_3:0' shape=(2,) dtype=float32>
>>> y = x + a
<tf.Tensor 'add_2:0' shape=(2,) dtype=float32>
{% endcoderay %}

### Interactive Usage
You can instead use the InteractiveSession class, and the `Tensor.eval()` and `Operation.run()` methods. This avoids having to keep a variable holding the session.

{% coderay lang:python Interactive Usage %}
# Enter an interactive TensorFlow Session.
>>> import tensorflow as tf
>>> sess = tf.InteractiveSession()

>>> x = tf.Variable([1.0, 2.0])
>>> a = tf.constant([3.0, 3.0])

# Initialize 'x' using the run() method of its initializer op.
>>> x.initializer.run()

# Add an op to subtract 'a' from 'x'.  Run it and print the result
>>> sub = tf.sub(x, a)
>>> print(sub.eval())
# ==> [-2. -1.]

# Close the Session when we're done.
>>> sess.close()
{% endcoderay %}

### Fetches
To fetch the outputs of operations, execute the graph with a run() call on the Session object and pass in the tensors to retrieve.

{% coderay lang:python Fetches %}
>>> input1 = tf.constant([3.0])
>>> input2 = tf.constant([2.0])
>>> add = tf.add(input1, input2)
>>> sub = tf.add(input1, input2)

>>> with tf.Session() as sess:
>>>   result = sess.run([mul, intermed])
>>>   print(result)

# output:
# [array([ 5.], dtype=float32), array([ 1.], dtype=float32)]
{% endcoderay %}

### Feeds
The examples above introduce tensors into the computation graph by storing them in Constants and Variables. TensorFlow also provides a feed mechanism for patching a tensor directly into any operation in the graph.

{% coderay lang:python Feeds %}
>>> input1 = tf.placeholder(tf.float32)
>>> input2 = tf.placeholder(tf.float32)
>>> output = tf.mul(input1, input2)

>>> with tf.Session() as sess:
>>>   print(sess.run([output], feed_dict={input1:[7.], input2:[2.]}))

# output:
# [array([ 14.], dtype=float32)]
{% endcoderay %}


