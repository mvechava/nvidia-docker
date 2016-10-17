FROM cuda

RUN zypper -n install \
        cuda-samples-$CUDA_PKG_VERSION && \
    zypper clean -a

WORKDIR /usr/local/cuda/samples/1_Utilities/deviceQuery
RUN make

CMD ./deviceQuery
