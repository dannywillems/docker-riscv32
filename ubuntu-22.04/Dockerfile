FROM ubuntu:22.04

LABEL maintainer="danny@o1labs.org"
LABEL version="0.1"
LABEL description="Docker image containing RISC-V 32bits toolchain"

# Disable Prompt During Packages Installation
ARG DEBIAN_FRONTEND=noninteractive

# Update Ubuntu Software repository
RUN apt update -y

RUN apt-get install -y autoconf automake autotools-dev curl python3 python3-pip \
    libmpc-dev libmpfr-dev libgmp-dev gawk build-essential bison flex texinfo \
    gperf libtool patchutils bc zlib1g-dev libexpat-dev ninja-build git cmake \
    libglib2.0-dev libslirp-dev

RUN git clone https://github.com/riscv-collab/riscv-gnu-toolchain
RUN cd riscv-gnu-toolchain && ./configure --with-arch=rv32gc --with-abi=ilp32d \
    --prefix=$(pwd)/riscv-toolchain && make -j 32
RUN cp riscv-gnu-toolchain/riscv-toolchain/bin/* /usr/local/bin
RUN rm -rf riscv-gnu-toolchain
