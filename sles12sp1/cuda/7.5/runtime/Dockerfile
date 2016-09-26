FROM suse/sles12sp1:latest
MAINTAINER NVIDIA CORPORATION <digits@nvidia.com>

LABEL com.nvidia.volumes.needed="nvidia_driver"

ENV NVIDIA_GPGKEY_SUM bd841d59a27a406e513db7d405550894188a4c1cd96bf8aa4f82f1b39e0b5c1c


#ADD http://smt-ec2/smt.crt /etc/pki/trust/anchors/smt.crt
#RUN update-ca-certificates
#RUN echo "54.93.130.182 smt-ec2.susecloud.net smt-ec2" >> /etc/hosts && \
#    echo "credentials.global.dir = /run/secrets/credentials.d" >> /etc/zypp/zypp.conf && \
#    zypper --gpg-auto-import-keys ref -s
#RUN mkdir -p /etc/pki/rpm-gpg/
#ADD http://developer.download.nvidia.com/compute/cuda/repos/GPGKEY /etc/pki/rpm-gpg/RPM-GPG-KEY-NVIDIA
#RUN sed -i '/^Version/d' /etc/pki/rpm-gpg/RPM-GPG-KEY-NVIDIA && \
#    echo "$NVIDIA_GPGKEY_SUM  /etc/pki/rpm-gpg/RPM-GPG-KEY-NVIDIA" | sha256sum -c --strict -

COPY cuda.repo /etc/zypp/repos.d/cuda.repo

ENV CUDA_VERSION 7.5
LABEL com.nvidia.cuda.version="7.5"

ENV CUDA_PKG_VERSION 7-5-7.5-18
RUN zypper --gpg-auto-import-keys ref -s
RUN zypper -n install \
        cuda-nvrtc-$CUDA_PKG_VERSION \
        cuda-cusolver-$CUDA_PKG_VERSION \
        cuda-cublas-$CUDA_PKG_VERSION \
        cuda-cufft-$CUDA_PKG_VERSION \
        cuda-curand-$CUDA_PKG_VERSION \
        cuda-cusparse-$CUDA_PKG_VERSION \
        cuda-npp-$CUDA_PKG_VERSION \
        cuda-cudart-$CUDA_PKG_VERSION && \
    ln -s cuda-$CUDA_VERSION /usr/local/cuda && \
    zypper clean -a

RUN echo "/usr/local/cuda/lib" >> /etc/ld.so.conf.d/cuda.conf && \
    echo "/usr/local/cuda/lib64" >> /etc/ld.so.conf.d/cuda.conf && \
    ldconfig

RUN echo "/usr/local/nvidia/lib" >> /etc/ld.so.conf.d/nvidia.conf && \
    echo "/usr/local/nvidia/lib64" >> /etc/ld.so.conf.d/nvidia.conf

ENV PATH /usr/local/nvidia/bin:/usr/local/cuda/bin:${PATH}
ENV LD_LIBRARY_PATH /usr/local/nvidia/lib:/usr/local/nvidia/lib64:${LD_LIBRARY_PATH}
