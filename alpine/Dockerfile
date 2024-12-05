ARG ALPINE_VERSION=latest

FROM alpine:${ALPINE_VERSION}

LABEL maintainer="danny@o1labs.org"
LABEL version="0.1"
LABEL description="Docker image containing RISC-V 32bits toolchain"

RUN apk add --no-cache \
  autoconf \
  automake \
  curl \
  python3 \
  py3-pip \
  gmp-dev \
  mpfr-dev \
  mpc1-dev \
  gawk \
  build-base \
  bison \
  flex \
  texinfo \
  gperf \
  libtool \
  patch \
  bc \
  zlib-dev \
  expat-dev \
  samurai \
  git \
  cmake \
  glib-dev \
  libslirp-dev

RUN git clone https://github.com/riscv-collab/riscv-gnu-toolchain && \
cd riscv-gnu-toolchain && \
  ./configure --with-arch=rv32gc --with-abi=ilp32d --prefix=$(pwd)/riscv-toolchain && \
  make -j $(nproc) && \
  cp riscv-toolchain/bin/* /usr/local/bin && \
cd .. && \
  rm -rf riscv-gnu-toolchain
