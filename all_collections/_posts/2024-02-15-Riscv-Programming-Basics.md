---
layout: post
title: Riscv Programming Basics
date: 2024-02-15
categories: ["Technology", "Riscv", "Programming"]
---

Having to study microprocessor architecture and organization, the open source and modular aspect of RISC-V interested me much. Risc-V is a Open Source ISA which anyone can use and modify.

First we have to get the riscv-toolchain from the [original source](https://github.com/riscv-collab/riscv-gnu-toolchain.git).
Clone the Toolchain from Github Source.

```git clone https://github.com/riscv-collab/riscv-gnu-toolchain.git ```

Then install the essential packages for Linux

```sudo apt-get install autoconf automake autotools-dev curl python3 python3-pip libmpc-dev libmpfr-dev libgmp-dev gawk build-essential bison flex texinfo gperf libtool patchutils bc zlib1g-dev libexpat-dev ninja-build git cmake libglib2.0-dev libslirp-dev```
