### RISC-V Environment

主要参考https://blog.csdn.net/weixin_43283275/article/details/125365614博文，期间有问题，又分别参考了其他博文。总之在一些非人类操作之后，弄出来了。

> 1. 先clone必要的工具包；
>    
>    ```shell
>    sudo apt-get install autoconf 
>    sudo apt-get install automake 
>    sudo apt-get install autotools-dev 
>    sudo apt-get install curl 
>    sudo apt-get install python3 
>    sudo apt-get install libmpc-dev 
>    sudo apt-get install libmpfr-dev 
>    sudo apt-get install libgmp-dev 
>    sudo apt-get install gawk 
>    sudo apt-get install build-essential 
>    sudo apt-get install bison 
>    sudo apt-get install flex 
>    sudo apt-get install texinfo 
>    sudo apt-get install gperf 
>    sudo apt-get install libtool 
>    sudo apt-get install patchutils 
>    sudo apt-get install bc 
>    sudo apt-get install zlib1g-dev 
>    sudo apt-get install libexpat-dev
>    sudo apt-get install libnewlib-dev
>    sudo apt-get install device-tree-compiler
>    ```
> 
> 2. clone RISC-V-GUN-TOOLCHAIN.
>    
>    **Note:** GitHub上clone的很慢，经常会失败。所以这里可以选择国内的Gitee上，这个比较快。但是晚上在GitHub上下载速度还可以，我第二次就在GitHub上成功了。
>    
>    ```shell
>    #GitHub 
>    git clone https://github.com/riscv/riscv-gnu-toolchain
>    cd riscv-gnu-toolchain
>    git submodule update --init   #递归下载子模块
>    ```
> 
> ```shell
> #Gitee
> git clone https://gitee.com/mirrors/riscv-gnu-toolchain.git
> #下载子模块
> git clone --recursive https://gitee.com/mirrors/riscv-newlib.git 
> 
> #子模块，GitHub中也一样，如果子模块下载失败了，可以用下面的地址重新下载
> git clone --recursive https://gitee.com/mirrors/riscv-dejagnu.git
> git clone --recursive https://gitee.com/mirrors/riscv-gcc.git
> git clone --recursive https://gitee.com/mirrors/riscv-glibc.git glibc
> git clone --recursive https://gitee.com/mirrors/riscv-newlib.git newlib
> # riscv-binutils与riscv-gdb来自于同一个仓库，且与本地要求的文件夹名称不同，需用命令指定本地名
> git clone --recursive -b fsf-gdb-10.1-with-sim https://gitee.com/mirrors/riscv-binutils-gdb.git riscv-gdb
> git clone --recursive -b riscv-binutils-2.38 https://gitee.com/mirrors/riscv-binutils-gdb.git riscv-binutils
> ```

> ```
> 3. 我用的是GitHub下的，所以会有这个log，不知道Gitee有无。
> 
> ```shell
> 子模组路径 'glibc'：检出 '9826b03b747b841f5fc6de2054bf1ef3f5c4bdf3'
> 子模组路径 'musl'：检出 '85e0e3519655220688e757b9d5bfd314923548bd'
> 子模组路径 'newlib'：检出 '415fdd4279b85eeec9d54775ce13c5c412451e08'
> 子模组路径 'pk'：检出 '2efabd3e6604b8a9e8f70baf52f57696680c7855'
> 子模组路径 'qemu'：检出 '823a3f11fb8f04c3c3cc0f95f968fef1bfc6534f'
> 子模组路径 'riscv-binutils'：检出 '20756b0fbe065a84710aa38f2457563b57546440'
> 子模组路径 'riscv-dejagnu'：检出 '4ea498a8e1fafeb568530d84db1880066478c86b'
> 子模组路径 'riscv-gcc'：检出 '5964b5cd72721186ea2195a7be8d40cfe6554023'
> 子模组路径 'riscv-gdb'：检出 '5da071ef0965b8054310d8dde9975037b0467311'
> 子模组路径 'spike'：检出 'a0298a33e7b2091ba8d9f3a20838d96dc1164cac'
> ```
> 
> 4. 创建安装目录以及设置环境变量
>    
>    ```shell
>    sudo mkdir -p /opt/RISCV/riscv64
>    sudo chmod -R 777 /opt/RISCV/riscv64     
>    sudo vim ~/.bashrc
>    export RISCV="/opt/RISCV/riscv64"        #工具链的安装链接路径
>    export PATH=$PATH:$RISCV/bin 
>    source ~/.bashrc             #使此设置永久有效，不然每次打开终端都需要重新设置
>    ```
>    
>    **Note:**这里`export RISCV="地址"`一定要写对，我在安装时，因为后面出错去参考其他博文，忘记这个地方要一致了，每篇博文安装的目录不一致，不能直接复制用，导致一直不对。
> 
> 5. 编译安装RISCV-GNU-TOOLCHAIN
>    
>    ```shell
>    cd riscv-gnu-toolchain
>    mkdir build
>    cd build
>    ../configure --prefix=/opt/RISCV/riscv64 --with-arch=rv64imc --with-abi=xxx
>    sudo make -jN  # N 代表使用job数量，我选用的是4个   同一时刻可允许同时执行命令的数目
>    ```
>    
>    **Note:**这里在编译的时候重复出错了，很浪费时间。首先第一个是4步骤中的/opt，一开会时执行的时候没有就加参数，导致一直不成功。印象里/opt是家目录下文件夹，但是不是很确定。所以我自己建了一个/opt进行安装，这里反反复复出错。其次就是make -j，用这个命令一直死机，编译很久后就宕机了。每次都是编译到大半，过了很多时间，突然卡住，死机。另外，../configure 命令中的/opt后面的参数地址一定要写对。
> 
> 6. 检查编译链
>    
>    ```shell
>    riscv64-unknown-linux-gnu-gcc -v
>    #log
>    Using built-in specs.
>    COLLECT_GCC=riscv64-unknown-linux-gnu-gcc
>    COLLECT_LTO_WRAPPER=/opt/RISCV/riscv64/libexec/gcc/riscv64-unknown-linux-gnu/11.1.0/lto-wrapper
>    Target: riscv64-unknown-linux-gnu
>    Configured with: /home/lihua/riscv-gnu-toolchain/build/../riscv-gcc/configure --target=riscv64-unknown-linux-gnu --prefix=/opt/RISCV/riscv64 --with-sysroot=/opt/RISCV/riscv64/sysroot --with-pkgversion=g --with-system-zlib --enable-shared --enable-tls --enable-languages=c,c++,fortran --disable-libmudflap --disable-libssp --disable-libquadmath --disable-libsanitizer --disable-nls --disable-bootstrap --src=../../riscv-gcc --disable-multilib --with-abi=lp64d --with-arch=rv64imafd --with-tune=rocket --with-isa-spec=2.2 'CFLAGS_FOR_TARGET=-O2   -mcmodel=medlow' 'CXXFLAGS_FOR_TARGET=-O2   -mcmodel=medlow'
>    Thread model: posix
>    Supported LTO compression algorithms: zlib
>    gcc version 11.1.0 (g) 
>    ```
>    
>    **Note:**这里前面提到的4中地址写对，就会有这个命令。相当于声明了环境变量是可以直接使用的。如果前面没有对应，则会找不到这个变量。4中，记得source ~/.bashrc
> 
> 7. 编译安装RISC-TOOLS
>    
>    ```shell
>    #编译spike
>    cd spike 
>    mkdir build 
>    cd build 
>    ../configure --prefix=$RISCV
>    make
>    sudo make install     
>    
>    #编译pk
>    cd pk
>    mkdir build
>    cd build
>    ../configure --prefix=$RISCV --host=riscv64-unknown-linux-gnu
>    make 
>    make install
>    ```
>    
>    **Note:**同样，前面4如果设置不对，则这里也是无法安装的。环境变量设置成功了，则这一步没有问题。
> 
> 8. 测试
>    
>    ```c
>    #include<stdio.h>
>    void main(){
>        printf("hello world!\n");
>    }
>    ```
>    
>    编译使用：
>    
>    ```shell
>    riscv64-unknown-linux-gnu-gcc -o hello hello.c -static
>    ```
>    
>    执行：
>    
>    ```shell
>    spike pk hello
>    #但是会出现以下log
>    terminate called after throwing an instance of 'std::runtime_error'
>      what():  could not open pk (did you misspell it? If VCS, did you forget +permissive/+permissive-off?)
>    #解决办法是找到pk的绝对路径
>    spike /opt/riscv/riscv64-unknown-linux-gnu/bin/pk test_hello  #我的路径是这个
>    
>    #此时终端显示helloworld，即算安装成功了。
>    ```