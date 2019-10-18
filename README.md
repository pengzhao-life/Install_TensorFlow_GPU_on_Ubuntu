How to install TensorFLow with GPU support on Ubuntu 16.04 desktop
====
## Make sure you have Nvidia Graphic card 

On your Ubuntu desktop 16.04, click the icon on upper left corner 'Search on your computer' -> 'System Settings' -> 'Details'

Look at 'Graphics' to check the gpu in use. If Nvidia gpu is not in use, turn it on. 

Mine is 'GeForce GTX 1050 Ti'. 
Go to tensor flow website to see whether this model is supported.

## Install Dependencies and Tensorflow
Follow the section 'Ubuntu 16.04 (CUDA 10)' on this website 
https://www.tensorflow.org/install/gpu

I got error message that complained about Nvidia driver version. I reinstalled nvidia-driver-418, rather than 410. That helped.

## Test
Open an terminal, type 'python3' to enter python. 
Then type 'import tensorflow' to import tensorflow module. It should have no error. I got error that complained 'protobuf' version incompatible. Run 'pip3 install protobuf' fixed the issue.

Then type

`sess = tf.Session(config=tf.ConfigProto(log_device_placement=True))`

or 

```import tensorflow as tf
with tf.device('/gpu:0'):
    a = tf.constant([1.0, 2.0, 3.0, 4.0, 5.0, 6.0], shape=[2, 3], name='a')
    b = tf.constant([1.0, 2.0, 3.0, 4.0, 5.0, 6.0], shape=[3, 2], name='b')
    c = tf.matmul(a, b)

with tf.Session() as sess:
    print (sess.run(c))
```
