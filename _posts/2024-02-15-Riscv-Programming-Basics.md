---
layout: post
title: Riscv Programming Basics
date: 2024-02-15
categories: ["Technology", "RISCV", "Programming"]
tags: ["RISCV", "Technology"]
---

Having to study microprocessor architecture and organization, the open source and modular aspect of RISC-V interested me much. Risc-V is a Open Source ISA which anyone can use and modify.

First we have to setup the riscv-toolchain 

# RISC-V Toolchain Setup
======================

This is the RISC-V C and C++ cross-compiler. It supports two build modes:
a generic ELF/Newlib toolchain and a more sophisticated Linux-ELF/glibc
toolchain.

###  Getting the sources
```
 git clone https://github.com/riscv/riscv-gnu-toolchain
```
**Warning: git clone takes around 6.65 GB of disk and download size**

### Prerequisites

Several standard packages are needed to build the toolchain.  

On Ubuntu, executing the following command should suffice:
```
sudo apt-get install autoconf automake autotools-dev curl python3 python3-pip libmpc-dev libmpfr-dev libgmp-dev gawk build-essential bison flex texinfo gperf libtool patchutils bc zlib1g-dev libexpat-dev ninja-build git cmake libglib2.0-dev libslirp-dev
```
On Fedora/CentOS/RHEL OS, executing the following command should suffice:
```
sudo yum install autoconf automake python3 libmpc-devel mpfr-devel gmp-devel gawk  bison flex texinfo patchutils gcc gcc-c++ zlib-devel expat-devel libslirp-devel
```
### Installation (Newlib)

To build the Newlib cross-compiler, pick an install path (that is writeable).
If you choose, say, `/opt/riscv`, then add `/opt/riscv/bin` to your `PATH`.
Then, simply run the following command:
```
./configure --prefix=/opt/riscv --with-cmodel=medany
make
```
> --prefix={folder_path} should be a path that must be writeable. You can add a specific path in the prefix flag

###### FOR ARCH AND ABI SELECTION:
```sh
./configure --prefix={folder_path} --with-arch=rv32gc --with-abi=ilp32d --with-cmodel=medany
make
```
Below Mentioned are some of the combinations that can be used with arch and abi:
```sh
rv32i/ilp32,
rv32ic/ilp32,
rv32iac/ilp32,
rv32im/ilp32,
rv32imc/ilp32,
rv32imafc/ilp32f,
rv32imafdc/ilp32,
rv32imafdc/ilp32f,
rv32imafdc/ilp32d,
rv32gc,ilp32d,
rv32ima/ilp32,
rv32imaf/ilp32,
rv32imafd/ilp32d,
rv64ima/lp64,
rv64imac/lp64,
rv64imaf/lp64,
rv64imafc/lp64,
rv64imafd/lp64,
rv64imafd/lp64d,
rv64imafdc/lp64
```
You should now be able to use riscv64-unknown-elf-gcc and its cousins.

### Installation (Linux)

To build the Linux cross-compiler, pick an install path (that should be writeable).
If you choose, say, `/opt/riscv`, then add `/opt/riscv/bin` to your `PATH` or you can add your own specific install path.
Then, simply run the following command:
```sh
./configure --prefix=/opt/riscv --with-cmodel=medany
make linux
```
> --prefix={folder_path} should be a path that must be writeable. You can add a specific path in the prefix flag

The build defaults to targeting RV64GC (64-bit) with glibc, even on a 32-bit
build environment. To build the 32-bit RV32GC toolchain, use:
```sh
./configure --prefix={folder_path} --with-arch=rv32gc --with-abi=ilp32d --with-cmodel=medany
make linux
```
Supported architectures are rv32i or rv64i plus standard extensions (a)tomics,
(m)ultiplication and division, (f)loat, (d)ouble, or (g)eneral for MAFD.

Supported ABIs are ilp32 (32-bit soft-float), ilp32d (32-bit hard-float),
ilp32f (32-bit with single-precision in registers and double in memory, niche
use only), lp64 lp64f lp64d (same but with 64-bit long and pointers).

### Installation For Most Combinations that I know
```sh
./configure --prefix={folder_path} --with-multilib-generator="rv32i-ilp32--;rv32ic-ilp32--;rv32iac-ilp32--;rv32im-ilp32--;rv32imc-ilp32--;rv32imafc-ilp32f--;rv32imafdc-ilp32f--;rv32ima-ilp32--;rv32imaf-ilp32--;rv32imafd-ilp32d--;rv32imafdc-ilp32--;rv32imafd-ilp32d--;rv32imafdc-ilp32d--;rv64ima-lp64--;rv64imac-lp64--;rv64imaf-lp64--;rv64imafc-lp64--;rv64imafd-lp64--;rv64imafdc-lp64--;rv64imafd-lp64d--;rv64imafdc-lp64d--;" --with-cmodel=medany
make
```
Only the elf toolchain can be built using the setup above. Therefore, you may use the multilib configure indicated below to create the Linux toolchain by using 
```sh
./configure --prefix={folder_path} --enable-multilib --with-cmodel=medany
make linux
```

### Installation (Newlib/Linux multilib)

To build either cross-compiler with support for both 32-bit and
64-bit, run the following command:
```sh
./configure --prefix={folder_path} --enable-multilib --with-cmodel=medany
```

And then either `make`, `make linux` or `make musl` for the Newlib, Linux
glibc-based or Linux musl libc-based cross-compiler, respectively.

The multilib compiler will have the prefix riscv64-unknown-elf- or
riscv64-unknown-linux-gnu- but will be able to target both 32-bit and 64-bit
systems.
It will support the most common `-march`/`-mabi` options, which can be seen by
using the `--print-multi-lib` flag on either cross-compiler.

The musl compiler (riscv64-unknown-linux-musl-) will only be able to target
64-bit systems due to limitations in the upstream musl architecture support.
The `--enable-multilib` flag therefore does not actually enable multilib support
for musl libc.

#### Build with customized multi-lib configure.

`--with-multilib-generator=` can specify what multilibs to build.  The argument
is a semicolon separated list of values, possibly consisting of a single value.
Currently only supported for riscv*-*-elf*.  The accepted values and meanings
are given below.

Every config is constructed with four components: architecture string, ABI,
reuse rule with architecture string and reuse rule with sub-extension.

Re-use part support expansion operator (*) to simplify the combination of
different sub-extensions, example 4 demonstrate how it uses and works.

Example 1: Add multi-lib support for rv32i with ilp32.
```sh
./configure --with-multilib-generator="rv32i-ilp32--" --with-cmodel=medany
```

Example 2: Add multi-lib support for rv32i with ilp32 and rv32imafd with ilp32.
```sh
./configure --with-multilib-generator="rv32i-ilp32--;rv32imafd-ilp32--" --with-cmodel=medany
```

Example 3: Add multi-lib support for rv32i with ilp32; rv32im with ilp32 and
rv32ic with ilp32 will reuse this multi-lib set.
```sh
./configure --with-multilib-generator="rv32i-ilp32-rv32im-c" --with-cmodel=medany
```

Example 4: Add multi-lib support for rv64ima with lp64; rv64imaf with lp64,
rv64imac with lp64 and rv64imafc with lp64 will reuse this multi-lib set.
```sh
./configure --with-multilib-generator="rv64ima-lp64--f*c" --with-cmodel=medany
```



## Installing Spike Simulator

#### PRE-REQUISITES
```sh
sudo apt-get install device-tree-compiler
```

Clone the RISC-V ISA Simulator (Spike) repository:
```sh
git clone https://github.com/riscv/riscv-isa-sim.git
cd riscv-isa-sim
```

Create a build directory and configure Spike:

```sh
mkdir build && cd build
../configure --prefix={folder_path} 
```
> --prefix={folder_path} has to be the path you provided for building the RISCV toolchain. 


Build and install Spike:
```
make
make install
```

### Running Spike Simulator

To run Spike simulator with custom configurations, use a command like this:
```sh
spike -l -m0x10000:0x20000 --isa=RV32IMA -d  bbl
```

Run spike with custom address not mentioned in the spike simulator
```sh
spike -l -m0x20000:0x20000,0x20041000:0x1000 --isa=RV64IMAFD -d  bbl
```
> here if the 20041000 is present in the bbl program and if it is not specified here, it may occur error during a spike operation. 


#### Troubleshooting Build Problems

Builds work best if installing into an empty directory.  If you build a
hard-float toolchain and then try to build a soft-float toolchain with
the same --prefix directory, then the build scripts may get confused
and exit with a linker error complaining that hard float code can't be
linked with soft float code.  Removing the existing toolchain first, or
using a different prefix for the second build, avoids the problem.  It
is OK to build one newlib and one linux toolchain with the same prefix.
But you should avoid building two newlib or two linux toolchains with
the same prefix.


#### Advanced Options

There are a number of additional options that may be passed to
configure.  See './configure --help' for more details.

Also you can define extra flags to pass to specific projects:
```sh
BINUTILS_NATIVE_FLAGS_EXTRA, BINUTILS_TARGET_FLAGS_EXTRA, GCC_EXTRA_CONFIGURE_FLAGS, GDB_NATIVE_FLAGS_EXTRA, GDB_TARGET_FLAGS_EXTRA, GLIBC_NATIVE_FLAGS_EXTRA, GLIBC_TARGET_FLAGS_EXTRA
```
Example: 
```sh
GCC_EXTRA_CONFIGURE_FLAGS=--with-gmp=/opt/gmp make linux 
```

_Note_ :
- _spike only support rv64* bare-metal/elf toolchain._
- _gdb simulator only support bare-metal/elf toolchain._