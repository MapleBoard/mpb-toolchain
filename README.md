This toolchain is for GD32 RISC-V Nano/Pico development board
The origin repositry is at: https://github.com/riscv-mcu/riscv-gnu-toolchain provided by nuclei.(updated: Autoconf error)

The RISC-V original toolchain source is at : https://github.com/riscv/riscv-gnu-toolchain provided by RISC-V foundation.  

This toolchain is for MapleBoard GD32 RISC-V Nano/Pico users, please visit https://github.com/MapleBoard/Mpb-toolchain-Example
to get the example of this toolchain. 


###  Getting the sources

This repository uses submodules, but submodules will fetch automatically on demand,
so `--recursive` or `git submodule update --init --recursive` is not needed.

    $ git clone https://github.com/MapleBoard/mpb-toolchain/

**Warning: git clone takes around 6.65 GB of disk and download size**

### Prerequisites

Several standard packages are needed to build the toolchain.  

On Debian, executing the following command should suffice:

    $ sudo apt-get install autoconf automake autotools-dev curl python3 libmpc-dev libmpfr-dev libgmp-dev gawk build-essential bison flex texinfo gperf libtool patchutils bc zlib1g-dev libexpat-dev

This process will start by downloading about 200 MiB of upstream sources, then
will patch, build, and install the toolchain.  If a local cache of the
upstream sources exists in $(DISTDIR), it will be used; the default location
is /var/cache/distfiles.  Your computer will need about 8 GiB of disk space to
complete the process.


### Installation (Linux)

To build the Linux cross-compiler, pick an install path.  If you choose,
say, `/opt/riscv`, then add `/opt/riscv/bin` to your `PATH` now.  Then, simply
run the following command:

    ./configure --prefix=/opt/mpb-toolchain --with-arch=rv32imac --with-abi=ilp32
    make -j8
    
* The -j8 means 8 threads, you can type more threads if your PC has more powerful CPU

RISC-V ISA Base and Extension: rv32imac  

* rv32i – Base Integer Instruction Set, 32-bit.  

* m – Standard Extension for Integer Multiplication and Division.  

* a – Standard Extension for Atomic Instructions.  

* c – Standard Extension for Compressed Instructions. 


The build defaults to targetting RV64GC (64-bit), even on a 32-bit build
environment.  To build the 32-bit RV32GC toolchain, use:

    ./configure --prefix=/opt/riscv --with-arch=rv32gc --with-abi=ilp32d
    make linux

Supported architectures are rv32i or rv64i plus standard extensions (a)tomics,
(m)ultiplication and division, (f)loat, (d)ouble, or (g)eneral for MAFD.

Supported ABIs are ilp32 (32-bit soft-float), ilp32d (32-bit hard-float),
ilp32f (32-bit with single-precision in registers and double in memory, niche
use only), lp64 lp64f lp64d (same but with 64-bit long and pointers).

If any question, please contact to jb@ces.com.tw

