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

Then type 'print(tensorflow.__version__)' to print version for testing. My version is 1.14.0.