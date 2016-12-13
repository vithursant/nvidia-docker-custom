FROM ubuntu:16.04
MAINTAINER vithu

# A docker container with the Nvidia kernel module and CUDA drivers installed

ENV CUDA_DEB http://developer.download.nvidia.com/compute/cuda/repos/ubuntu1604/x86_64/cuda-repo-ubuntu1604_8.0.44-1_amd64.deb
ENV CUDNN_TAR http://developer.download.nvidia.com/compute/redist/cudnn/v5.1/cudnn-8.0-linux-x64-v5.1.tgz
ENV DEBIAN_FRONTEND noninteractive

RUN apt-get update && apt-get install -q -y wget 

RUN cd /opt && \
  wget $CUDA_DEB && \
  dpkg -i cuda-repo-ubuntu1604_8.0.44-1_amd64.deb && \
  apt-get update && \
  apt-get install -y cuda && \
  wget $CUDNN_TAR && \
  tar xvzf cudnn-8.0-linux-x64-v5.1.tgz && \
  cp cuda/include/cudnn.h /usr/local/cuda/include && \
  cp cuda/lib64/libcudnn* /usr/local/cuda/lib64 && \
  chmod a+r /usr/local/cuda/include/cudnn.h /usr/local/cuda/lib64/libcudnn*

# Ensure the CUDA libs and binaries are in the correct environment variables
ENV LIBRARY_PATH=$LD_LIBRARY_PATH:/usr/local/cuda-8.0/lib64
ENV PATH=$PATH:/usr/local/cuda-8.0/bin

RUN cd /usr/local/cuda-8.0/samples/1_Utilities/deviceQuery &&\ 
    make

WORKDIR /usr/local/cuda-8.0/samples/1_Utilities/deviceQuery
