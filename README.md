# AmoveoMinerGpuCuda
Amoveo Cryptocurrency Miner for Gpu work to be used with [AmoveoPool2.com](http://AmoveoPool2.com).

[for the prop-pool-exploit version](propPoolExploit/README.md)

Tested Gpu Speeds:

* Tesla V100:  ??? Mh/s  - Suggested BlockSize: 1024, Numblocks: 64
* Tesla P100:  ??? Mh/s  - Suggested BlockSize: 192, Numblocks: 168
* GTX1080 TI:  2900 Mh/s  - Suggested BlockSize: 96, Numblocks: 168
* GTX1060 6GB: 1300 Mh/s  - Suggested BlockSize: 64
* GTX1050:    550 Mh/s  - Suggested BlockSize: 64
* Tesla K80:  451 Mh/s  - Suggested BlockSize: 128
* 750TI:      323 Mh/s  - Suggested BlockSize: 32

Default BlockSize is 64.
Default NumBlocks is 96.
Default SuffixMax is 65536.

* Try various BlockSize setting values. Optimal setting for BlockSize is very personal to your system. Try BlockSize values like 96, 64, 32, or 128. A higher BlockSize is almost always better, but too high will crash the miner.
* If you get too much OS lag, reduce the SuffixMax setting (at the cost of a some hash rate).
* If your Memory Controller Load is constantly at 100%, you may want to try lowering your NumBlocks.

Best Settings from My Tests:
* Gtx1060: BlockSize=64, NumBlocks=96
* Gtx1050: BlockSize=64, NumBlocks=90
* Tesla K80: BlockSize=128, NumBlocks=128
* 750Ti: BlockSize=32, NumBlocks=64



## Windows

### Run Dependencies
* Install Visual Studio 2015 (Community Edition is free.)
* Install Cuda 9.1

### Releases

   [Latest pre-built releases are here](https://github.com/Mandelhoff/AmoveoMinerGpuCuda/releases)


### Run

Example Usage:
```
AmoveoMinerGpuCuda.exe BPA3r0XDT1V8W4sB14YKyuu/PgC6ujjYooVVzq1q1s5b6CAKeu9oLfmxlplcPd+34kfZ1qx+Dwe3EeoPu0SpzcI=
```

Advanced Usage Template:
```
AmoveoMinerGpuCuda.exe <Base64AmoveoAddress> <CudaDeviceId> <BlockSize> <NumBlocks> <RandomSeed> <SuffixMax> <PoolUrl>
```
* CudaDeviceId is optional an defaults to 0.
* BlockSize is optional and defaults to 64.
* NumBlocks is optional and defaults to 96.
* RandomSeed is optional. Set this if you want multiple miners using the same address to avoid nonce collisions.
* SuffixMax optional and defaults to 65536. Do NOT use anything higher than 65536. Lower numbers reduce OS lag and will reduce hash rate by a few percent.
* PoolUrl is optional and defaults to http://amoveopool.com/work


### Build
The Windows releases are built with Visual Studio 2015 with Cuda, RestCPP, boost, and openSSL.


## Linux

### Install dependencies

```
sudo apt-get install libcpprest-dev libncurses5-dev libssl-dev unixodbc-dev g++ git
```

### Install CUDA9.1

```
wget http://developer.download.nvidia.com/compute/cuda/repos/ubuntu1604/x86_64/cuda-repo-ubuntu1604_9.1.85-1_amd64.deb
sudo apt-key adv —fetch-keys http://developer.download.nvidia.com/compute/cuda/repos/ubuntu1604/x86_64/7fa2af80.pub
sudo dpkg -i cuda-repo-ubuntu1604_9.1.85-1_amd64.deb
sudo apt update
sudo apt install cuda -y
```

Add these lines to the end of `~/.bashrc`

```
export CUDA_HOME=/usr/local/cuda
export PATH="/usr/local/cuda/bin:$PATH"
export LD_LIBRARY_PATH="/usr/local/cuda/lib64:$LD_LIBRARY_PATH"
```

### Build

```
git clone https://github.com/Mandelhoff/AmoveoMinerGpuCuda.git
cd ./AmoveoMinerGpuCuda
sh build.sh
```

Donations are welcome:
* Amoveo: BGH+3P768A9cSNR3GLSRXgsokSL/Jdbm+rOJogbgiPxq8M+J2R4nVxZ+Hj6WdI4rMsq6nPzkMh77WGBCMx89HUM=
