# BDA: Binary Dependence Analysis

#### Practical Dependence Analysis for Binary Executables by Unbiased Whole-program Path Sampling and Per-path Abstract Interpretation

## TL;DR

Please install [radare2](https://github.com/radare/radare2) on your machine first. Note that we do not support the newest version radare2 (*we will support it in upcoming source code*), due to its fast development. Thus, please use following commands to install radare2.

```bash
git clone https://github.com/radare/radare2.git
cd radare2/
git checkout 5d698c76ae8a94226532b67711983e38221f21d2 .
sys/user.sh
echo "PATH=\$PATH:\$HOME/bin" >> ~/.bashrc
```

After that, all the executable could run directly on Ubuntu 16.04.

## Description

+ `rexe`: Sampling-based abstract interpreter

+ `rgdb`: GDB for sampling-based abstract interpretr

+ `rdep`: Sampling-based posterior analyzer

+ `rinfo`: Binary basic information dumper


## Basic Usage

```bash
./rexe -t <sample.time> <binary>
./rdep -d <refer.dep> <binary>
```

You can also set log level for more information.

```bash
RUST_LOG=info ./rexe -t <sample.time> <binary>
RUST_LOG=info ./rdep -d <refer.dep> <binary>
```

### 181.mcf Demo

In the following demo, we sampled `181.mcf` for 300 times. At last, we got *2 Missing Dependence* and *141 More Dependence*, compared with *2050 Refer Dependence*.

[![asciicast](https://asciinema.org/a/239700.svg)](https://asciinema.org/a/239700)

## Auxiliary Tool

Additionally, `rgdb` could help you dig into more internal data of abstract interpreter.

```bash
./rgdb <binary>
```

### 181.mcf Demo

[![asciicast](https://asciinema.org/a/239633.svg)](https://asciinema.org/a/239633)
