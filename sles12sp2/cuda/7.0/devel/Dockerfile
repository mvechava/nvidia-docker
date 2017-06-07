FROM cuda:7.0-runtime
MAINTAINER NVIDIA CORPORATION <digits@nvidia.com>

ENV GPUDK_URL http://developer.download.nvidia.com/compute/cuda/repos/sles12/x86_64/gpu-deployment-kit-352.93-0.x86_64.rpm

RUN zypper --gpg-auto-import-keys ref -s; \
    zypper -n install \
        cuda-core-$CUDA_PKG_VERSION \
        cuda-misc-headers-$CUDA_PKG_VERSION \
        cuda-command-line-tools-$CUDA_PKG_VERSION \
        cuda-license-$CUDA_PKG_VERSION \
        cuda-nvrtc-dev-$CUDA_PKG_VERSION \
        cuda-cusolver-dev-$CUDA_PKG_VERSION \
        cuda-cublas-dev-$CUDA_PKG_VERSION \
        cuda-cufft-dev-$CUDA_PKG_VERSION \
        cuda-curand-dev-$CUDA_PKG_VERSION \
        cuda-cusparse-dev-$CUDA_PKG_VERSION \
        cuda-npp-dev-$CUDA_PKG_VERSION \
        cuda-cudart-dev-$CUDA_PKG_VERSION \
        cuda-driver-dev-$CUDA_PKG_VERSION \
        gcc-c++ && \
    zypper clean -a

RUN mkdir /tmp/gpu-deployment-kit
ADD $GPUDK_URL /tmp/gpu-deployment-kit/
RUN rpm2cpio /tmp/gpu-deployment-kit/gpu-deployment-kit-352.93-0.x86_64.rpm | cpio -id && \
    mv usr/include/nvidia/gdk/* /usr/local/cuda/include && \
    mv usr/src/gdk/nvml/lib/* /usr/local/cuda/lib64/stubs && \
    rm -rf /tmp/gpu-deployment-kit* && \
    zypper clean -a

ENV LIBRARY_PATH /usr/local/cuda/lib64/stubs:${LIBRARY_PATH}
