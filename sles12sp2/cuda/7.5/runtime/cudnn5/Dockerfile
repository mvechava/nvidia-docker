FROM cuda:7.5-runtime
MAINTAINER NVIDIA CORPORATION <digits@nvidia.com>

ENV CUDNN_VERSION 5
LABEL com.nvidia.cudnn.version="5"
ENV CUDNN_DOWNLOAD_SUM 69ca71f7728b54b6e003393083f419b24774fecd3b08bbf41bceac9a9fe16345

RUN zypper --gpg-auto-import-keys ref -s; \
    zypper -n install \
        curl \
        tar && \
    zypper clean -a

RUN curl -fsSL http://developer.download.nvidia.com/compute/redist/cudnn/v5.1/cudnn-7.5-linux-x64-v5.1.tgz -O && \
    echo "$CUDNN_DOWNLOAD_SUM  cudnn-7.5-linux-x64-v5.1.tgz" | sha256sum -c --strict - && \
    tar -xzf cudnn-7.5-linux-x64-v5.1.tgz -C /usr/local --wildcards 'cuda/lib64/libcudnn.so.*' && \
    rm cudnn-7.5-linux-x64-v5.1.tgz && \
    ldconfig
