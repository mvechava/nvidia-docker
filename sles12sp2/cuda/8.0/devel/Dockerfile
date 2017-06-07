FROM cuda:8.0-runtime
MAINTAINER NVIDIA CORPORATION <digits@nvidia.com>

#BSC #974556 workaround
#COPY zypp/services.d /etc/zypp/services.d
#COPY zypp/repos.d /etc/zypp/repos.d
#COPY zypp/credentials.d /etc/zypp/credentials.d
#COPY hosts /tmp/hosts

#RUN tail -1 /tmp/hosts >> /etc/hosts; cat /etc/hosts; zypper --gpg-auto-import-keys ref -s; \
RUN zypper --gpg-auto-import-keys ref -s; \
    zypper -n install \
        cuda-core-$CUDA_PKG_VERSION \
        cuda-misc-headers-$CUDA_PKG_VERSION \
        cuda-command-line-tools-$CUDA_PKG_VERSION \
        cuda-license-$CUDA_PKG_VERSION \
        cuda-nvrtc-dev-$CUDA_PKG_VERSION \
        cuda-nvml-dev-$CUDA_PKG_VERSION \
        cuda-nvgraph-dev-$CUDA_PKG_VERSION \
        cuda-cusolver-dev-$CUDA_PKG_VERSION \
        cuda-cublas-dev-$CUDA_PKG_VERSION \
        cuda-cufft-dev-$CUDA_PKG_VERSION \
        cuda-curand-dev-$CUDA_PKG_VERSION \
        cuda-cusparse-dev-$CUDA_PKG_VERSION \
        cuda-npp-dev-$CUDA_PKG_VERSION \
        cuda-cudart-dev-$CUDA_PKG_VERSION \
        cuda-driver-dev-$CUDA_PKG_VERSION && \
    zypper clean -a

ENV LIBRARY_PATH /usr/local/cuda/lib64/stubs:${LIBRARY_PATH}
