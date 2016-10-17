FROM cuda:7.5-runtime
MAINTAINER NVIDIA CORPORATION <digits@nvidia.com>

ENV CUDNN_VERSION 4
LABEL com.nvidia.cudnn.version="4"

ENV CUDNN_DOWNLOAD_SUM 4e64ef7716f20c87854b4421863328e17cce633330c319b5e13809b61a36f97d
COPY curl-7.19.7-1.46.1.x86_64.rpm /tmp
COPY tar-1.26-1.2.4.1.x86_64.rpm /tmp
#RUN zypper -n in curl tar
RUN zypper -n in /tmp/curl-7.19.7-1.46.1.x86_64.rpm  /tmp/tar-1.26-1.2.4.1.x86_64.rpm
RUN curl -fsSL http://developer.download.nvidia.com/compute/redist/cudnn/v4/cudnn-7.0-linux-x64-v4.0-prod.tgz -O && \
    echo "$CUDNN_DOWNLOAD_SUM  cudnn-7.0-linux-x64-v4.0-prod.tgz" | sha256sum -c - && \
    tar -xzf cudnn-7.0-linux-x64-v4.0-prod.tgz -C /usr/local --wildcards 'cuda/lib64/libcudnn.so.*' && \
    rm cudnn-7.0-linux-x64-v4.0-prod.tgz && \
ldconfig
