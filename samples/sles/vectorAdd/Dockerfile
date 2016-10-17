FROM cuda

RUN zypper -n install \
        cuda-samples-$CUDA_PKG_VERSION && \
    zypper clean -a

WORKDIR /usr/local/cuda/samples/0_Simple/vectorAdd
RUN make

CMD ./vectorAdd
