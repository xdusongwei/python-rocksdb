FROM python:3.8-buster
ENV version=6.10.1
RUN apt-get update && DEBIAN_FRONTEND="noninteractive" apt-get install -y libgflags-dev libsnappy-dev zlib1g-dev \
    libbz2-dev liblz4-dev libzstd-dev unzip cmake g++ wget curl && rm -rf /var/lib/apt/lists/*
RUN wget -O v${version}.tar.gz https://github.com/facebook/rocksdb/archive/v${version}.tar.gz && \
    tar -xf v${version}.tar.gz && \
    cd rocksdb-${version} && \
    USE_RTTI=1 DISABLE_JEMALLOC=1 make -j "$(nproc)" shared_lib && \
    make install-shared && \
    make clean && \
    ldconfig && \
    cd .. && rm v${version}.tar.gz && rm -rf rocksdb-${version}
