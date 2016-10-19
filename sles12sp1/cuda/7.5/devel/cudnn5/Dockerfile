FROM cuda:7.5-devel
MAINTAINER NVIDIA CORPORATION <digits@nvidia.com>

ENV CUDNN_VERSION 5
LABEL com.nvidia.cudnn.version="5"
ENV CUDNN_DOWNLOAD_SUM 40d506d0a8a00a3faccce1433346806b8cd2535683b6f08a63683ce6e474419f

COPY curl-7.37.0-28.1.x86_64.rpm /tmp
COPY tar-1.27.1-8.1.x86_64.rpm /tmp

RUN rpm -ivh /tmp/curl-7.37.0-28.1.x86_64.rpm /tmp/tar-1.27.1-8.1.x86_64.rpm
RUN curl -fsSL http://developer.download.nvidia.com/compute/redist/cudnn/v5.1/cudnn-7.5-linux-x64-v5.1.tgz -O && \
    echo "$CUDNN_DOWNLOAD_SUM  cudnn-7.5-linux-x64-v5.1.tgz" | sha256sum -c --strict - && \
    tar -xzf cudnn-7.5-linux-x64-v5.1.tgz -C /usr/local --wildcards 'cuda/lib64/libcudnn.so.*' && \
    rm cudnn-7.5-linux-x64-v5.1.tgz && \
    ldconfig