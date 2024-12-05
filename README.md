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

The resulting binaries are after that copied in /usr/local/bin so you can use it
as you want.
The available binaries are:
```
riscv32-unknown-elf-addr2line
riscv32-unknown-elf-ar
riscv32-unknown-elf-as
riscv32-unknown-elf-c++
riscv32-unknown-elf-c++filt
riscv32-unknown-elf-cpp
riscv32-unknown-elf-elfedit
riscv32-unknown-elf-g++
riscv32-unknown-elf-gcc
riscv32-unknown-elf-gcc-14.2.0
riscv32-unknown-elf-gcc-ar
riscv32-unknown-elf-gcc-nm
riscv32-unknown-elf-gcc-ranlib
riscv32-unknown-elf-gcov
riscv32-unknown-elf-gcov-dump
riscv32-unknown-elf-gcov-tool
riscv32-unknown-elf-gdb
riscv32-unknown-elf-gdb-add-index
riscv32-unknown-elf-gprof
riscv32-unknown-elf-ld
riscv32-unknown-elf-ld.bfd
riscv32-unknown-elf-lto-dump
riscv32-unknown-elf-nm
riscv32-unknown-elf-objcopy
riscv32-unknown-elf-objdump
riscv32-unknown-elf-ranlib
riscv32-unknown-elf-readelf
riscv32-unknown-elf-run
riscv32-unknown-elf-size
riscv32-unknown-elf-strings
riscv32-unknown-elf-strip
```

## Build the images

```shell
docker build -t riscv32-toolchain .
```
