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

$ wget https://developer.download.nvidia.com/compute/cuda/repos/ubuntu1804/x86_64/cuda-repo-ubuntu1804_10.1.243-1_amd64.deb
$ sudo dpkg -i cuda-repo-ubuntu1804_10.1.243-1_amd64.deb
$ sudo apt-key adv --fetch-keys https://developer.download.nvidia.com/compute/cuda/repos/ubuntu1804/x86_64/7fa2af80.pub
$ sudo apt-get update
$ sudo apt-get install cuda-10-1

# Reboot. Check that GPUs are visible using the command: nvidia-smi
$ sudo reboot

$ sudo gedit ~/.profile

export PATH=/usr/local/cuda-10.1/bin:$PATH 
export LD_LIBRARY_PATH=/usr/local/cuda-10.1/lib64:$LD_LIBRARY_PATH

# https://developer.nvidia.com/rdp/cudnn-download 에서
# cuDNN Library for Linux 눌러서 다운로드(tgz 파일)
# 다운로드 받은 폴더로 이동하여 파일 압축풀기
$ tar -zxvf cudnn-10.1-linux-x64-v7.6.5.32.tgz

# cuda/include 폴더 이동 후 파일 복사
$ cd cuda/include
$ sudo cp cudnn.h /usr/local/cuda/include

# ../lib64 폴더 이동 후 파일 복사
$ cd ../lib64
$ sudo cp libcudnn* /usr/local/cuda/lib64

# 모두 설치가 되었다면 다운받은 sample로 MNIST를 돌려보아 test passed라고 나온다면 성공
$ cd /usr/src/cudnn_samples_v7/mnistCUDNN/
$ sudo make clean && sudo make
$ ./mnistCUDNN


```
아나콘다 설치
 
```
$ sudo apt install curl
$ curl -O https://repo.anaconda.com/archive/Anaconda3-2019.10-Linux-x86_64.sh
$ bash Anaconda3-2019.10-Linux-x86_64.sh

$ conda create -n py36 python=3.6
```

GPU 확인

```python

import tensorflow as tf
tf.test.is_gpu_available()

```

