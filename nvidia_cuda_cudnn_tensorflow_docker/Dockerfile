FROM nvidia/cuda:8.0-cudnn5-devel
MAINTAINER vithu

# A docker container with the Nvidia kernel module and CUDA drivers installed
ENV TF_BINARY_URL=https://storage.googleapis.com/tensorflow/linux/gpu/tensorflow_gpu-0.12.0rc0-cp34-cp34m-linux_x86_64.whl

RUN \
    apt-get -qq -y update && apt-get -y install \
    python3-pip && \
    pip3 install -U $TF_BINARY_URL
