FROM cuda

RUN zypper --gpg-auto-import-keys ref -s; \
    zypper -n install \
        cuda-samples-$CUDA_PKG_VERSION && \
    zypper clean -a

WORKDIR /usr/local/cuda/samples/1_Utilities/bandwidthTest
RUN make

CMD ./bandwidthTest --mode=shmoo
