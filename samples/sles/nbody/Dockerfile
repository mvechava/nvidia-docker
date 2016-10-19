FROM cuda

#BSC #974556 workaround
COPY zypp/services.d /etc/zypp/services.d
COPY zypp/repos.d /etc/zypp/repos.d
COPY zypp/credentials.d /etc/zypp/credentials.d
COPY hosts /tmp/hosts

RUN tail -1 /tmp/hosts >> /etc/hosts; cat /etc/hosts; zypper --gpg-auto-import-keys ref -s; \
    zypper -n install \
        cuda-samples-$CUDA_PKG_VERSION && \
    zypper clean -a

WORKDIR /usr/local/cuda/samples/5_Simulations/nbody
RUN make

CMD ./nbody -benchmark
