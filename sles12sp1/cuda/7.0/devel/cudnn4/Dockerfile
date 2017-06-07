FROM cuda:7.0-devel
MAINTAINER NVIDIA CORPORATION <digits@nvidia.com>

ENV CUDNN_VERSION 4
LABEL com.nvidia.cudnn.version="4"
ENV CUDNN_DOWNLOAD_SUM cd091763d5889f0efff1fbda83bade191f530743a212c6b0ecc2a64d64d94405

RUN zypper --gpg-auto-import-keys ref -s; \
    zypper -n install \
        curl \
	tar && \
    zypper clean -a
	
RUN curl -fsSL http://developer.download.nvidia.com/compute/redist/cudnn/v4/cudnn-7.0-linux-x64-v4.0-prod.tgz -O && \
    echo "$CUDNN_DOWNLOAD_SUM  cudnn-7.0-linux-x64-v4.0-prod.tgz" | sha256sum -c --strict - && \
    tar -xzf cudnn-7.0-linux-x64-v4.0-prod.tgz -C /usr/local && \
    rm cudnn-7.0-linux-x64-v4.0-prod.tgz && \
    ldconfig
