# RISC-V 32 bits toolchain

This docker image contains the toolchain to build, analyze and disassemble
RISC-V 32 bits compatible programs.

Mostly, the docker images contains the binaries resulting from the following commands:
```shell
sudo apt-get install -y autoconf \
  automake \
  autotools-dev \
  curl python3 python3-pip libmpc-dev libmpfr-dev libgmp-dev gawk build-essential bison flex texinfo gperf libtool patchutils bc zlib1g-dev libexpat-dev ninja-build git cmake libglib2.0-dev libslirp-dev

git clone https://github.com/riscv-collab/riscv-gnu-toolchain
cd riscv-gnu-toolchain
./configure --with-arch=rv32gc --with-abi=ilp32d --prefix=$(pwd)/riscv-toolchain
make -j 32
```

This docker image can be used in GitHub actions to cross-compile programs
written in a RISC-V 32 bits ISA variant (like riscv32i, riscv32im, etc).

## Build the images

```shell
docker build -t riscv32-toolchain .
```


