FROM cuda

RUN zypper --gpg-auto-import-keys ref -s; \
    zypper -n install \
        cuda-samples-$CUDA_PKG_VERSION && \
    zypper clean -a

WORKDIR /usr/local/cuda/samples/0_Simple/matrixMulCUBLAS
RUN make

CMD ./matrixMulCUBLAS -sizemult=10
