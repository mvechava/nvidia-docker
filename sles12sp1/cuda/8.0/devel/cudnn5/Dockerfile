FROM cuda:8.0-devel
MAINTAINER NVIDIA CORPORATION <digits@nvidia.com>

ENV CUDNN_VERSION 5
LABEL com.nvidia.cudnn.version="5"
ENV CUDNN_DOWNLOAD_SUM c10719b36f2dd6e9ddc63e3189affaa1a94d7d027e63b71c3f64d449ab0645ce

RUN zypper --gpg-auto-import-keys ref -s; \
    zypper -n install \
        curl \
        tar && \
    zypper clean -a

RUN curl -fsSL http://developer.download.nvidia.com/compute/redist/cudnn/v5.1/cudnn-8.0-linux-x64-v5.1.tgz -O && \
    echo "$CUDNN_DOWNLOAD_SUM  cudnn-8.0-linux-x64-v5.1.tgz" | sha256sum -c --strict - && \
    tar -xzf cudnn-8.0-linux-x64-v5.1.tgz -C /usr/local && \
    rm cudnn-8.0-linux-x64-v5.1.tgz && \
    ldconfig
