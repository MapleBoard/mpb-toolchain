This toolchain is for GD32 RISC-V Nano/Pico development board
The origin repositry is at: https://github.com/riscv-mcu/riscv-gnu-toolchain provided by nuclei.(updated: Autoconf error)

The RISC-V original toolchain source is at : https://github.com/riscv/riscv-gnu-toolchain provided by RISC-V foundation.  

This toolchain is for MapleBoard GD32 RISC-V Nano/Pico users, please visit https://github.com/MapleBoard/Mpb-toolchain-Example
to get the example of this toolchain. 


###  Getting the sources

This repository uses submodules, but submodules will fetch automatically on demand,
so `--recursive` or `git submodule update --init --recursive` is not needed.

    git clone https://github.com/MapleBoard/mpb-toolchain/

**Warning: git clone takes around 6.65 GB of disk and download size**

### Prerequisites

Several standard packages are needed to build the toolchain.  

On Debian, executing the following command should suffice:

    sudo apt-get install autoconf automake autotools-dev curl python3 libmpc-dev libmpfr-dev libgmp-dev gawk build-essential bison flex texinfo gperf libtool patchutils bc zlib1g-dev libexpat-dev

This process will start by downloading about 200 MiB of upstream sources, then
will patch, build, and install the toolchain.  If a local cache of the
upstream sources exists in $(DISTDIR), it will be used; the default location
is /var/cache/distfiles.  Your computer will need about 8 GiB of disk space to
complete the process.


### Installation (Linux)

To build the Linux cross-compiler, pick an install path.  If you choose,
say, `/opt/mpb-toolchain`, then add `/opt/mpb-toolchain/bin` to your `$PATH` now.
You can modity `~/.bashrc `file to do this thing.

Then, simply run the following command:

    cd mpb-toolchain
    ./configure --prefix=/opt/mpb-toolchain --with-arch=rv32imac --with-abi=ilp32
    sudo make -j8
    
* `--prefix` decide the toolchain installation location, if you install in user space, the `make` command should not add `sudo`.
* The `-j8` suffix means 8 threads, depending on your CPU core.

RISC-V ISA Base and Extension: rv32imac  

* rv32i – Base Integer Instruction Set, 32-bit.  

* m – Standard Extension for Integer Multiplication and Division.  

* a – Standard Extension for Atomic Instructions.  

* c – Standard Extension for Compressed Instructions. 

After installation complete, checkout the folder whhich you install, in this case`/opt/mpb-toolchain/bin`.
There should be alot shared library file such as ricv32-mapleboard-elf-ar, ricv32-mapleboard-elf-gcc, ricv32-mapleboard-elf-gdb.


If any question, please contact to jb@ces.com.tw

