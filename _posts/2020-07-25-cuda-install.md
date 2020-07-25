---
title: "Nvidia driver 및 Cuda 설치"
date: 2020-07-25 15:26:28 -0400
categories: Settings
---


### Cuda 설치

나중에 한번쯤은 다시 설치할 일이 있을거 같아서 메모해두는거..

https://www.tensorflow.org/install/gpu#linux_setup

- Ubuntu 18.04
- GPU: RTX 2080 ti
- nvidia-driver-450
- python 3.7.4
- CUDA 10.1 
- cuDNN 7.6.4


```
# Add NVIDIA package repositories : Ubuntu 18.04(CUDA 10.1)

$  wget https://developer.download.nvidia.com/compute/cuda/repos/ubuntu1804/x86_64/cuda-repo-ubuntu1804_10.1.243-1_amd64.deb
$ sudo apt-key adv --fetch-keys https://developer.download.nvidia.com/compute/cuda/repos/ubuntu1804/x86_64/7fa2af80.pub
$ sudo dpkg -i cuda-repo-ubuntu1804_10.1.243-1_amd64.deb
$ sudo apt-get update
$ wget http://developer.download.nvidia.com/compute/machine-learning/repos/ubuntu1804/x86_64/nvidia-machine-learning-repo-ubuntu1804_1.0.0-1_amd64.deb
$ sudo apt install ./nvidia-machine-learning-repo-ubuntu1804_1.0.0-1_amd64.deb
$ sudo apt-get update

# Install NVIDIA driver
$ sudo apt-get install --no-install-recommends nvidia-driver-450

# Reboot. Check that GPUs are visible using the command: nvidia-smi
$ sudo reboot

# Install development and runtime libraries (~4GB)
$ sudo apt-get install --no-install-recommends \
    cuda-10-1 \
    libcudnn7=7.6.4.38-1+cuda10.1  \
    libcudnn7-dev=7.6.4.38-1+cuda10.1

# Install TensorRT. Requires that libcudnn7 is installed above.
$ sudo apt-get install -y --no-install-recommends libnvinfer6=6.0.1-1+cuda10.1 \
    libnvinfer-dev=6.0.1-1+cuda10.1 \
    libnvinfer-plugin6=6.0.1-1+cuda10.1

```
GPU 확인

```python

import tensorflow as tf
tf.test.is_gpu_available()

```

아나콘다 설치
 
```
$ sudo apt install curl
$ curl -O https://repo.anaconda.com/archive/Anaconda3-2019.10-Linux-x86_64.sh
$ bash Anaconda3-2019.10-Linux-x86_64.sh

$ conda create -n py36 python=3.6
```
