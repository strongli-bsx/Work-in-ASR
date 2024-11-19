通常Linux会有以下目录

- arch 子目录包括所有和体系结构相关的核心代码。它还有更深的子目录，每一个代表一种支持的体系结构
- include 子目录包括编译核心所需要的大部分 include 文件。它也有更深的子目录，每一个支持的体系结构一个。 include/asm 是这个体系结构所需要的真实的 include 目录的软链接，例如 include/asm-i386 。为了改变体系结构，你需要编辑核心的 makefile ，重新运行 Linux 的核心配置程序 
- init 这个目录包含核心的初始化代码，这时研究核心如何工作的一个非常好的起点
- mm 这个目录包括所有的内存管理代码。和体系结构相关的内存管理代码位于 arch/*/mm/
- drivers 系统所有的设备驱动程序在这个目录。它们被划分成设备驱动程序类
- ipc 这个目录包含核心的进程间通讯的代码
- modules 这只是一个用来存放建立好的模块的目录
- fs 所有的文件系统代码。被划分成子目录，每一个支持的文件系统一个
- kernel 主要的核心代码。同样，和体系相关的核心代码放在 arch/*/kernel
- net 核心的网络代码
- lib 这个目录放置核心的库代码。和体系结构相关的库代码在 arch/*/lib/
- scripts 这个目录包含脚本（例如 awk 和 tk 脚本），用于配置核心



Linux 核心源代码的大部分代码行在它的设备驱动程序中。 Linux 所有的设备驱动程序源代码都在 drivers 中，但是它们被进一步分类： 

- /block 块设备驱动程序比如 ide （ ide.c ）。如果你希望查看所有可能包含文件系统的设备是如何初始化的，你可以看 drivers/block/genhd.c 中的 device_setup() 。它不仅初始化硬盘，也初始化网络，因为你安装 nfs 文件系统的时候需要网络。块设备包括基于 IDE 和 SCSI 设备。 
- /char 这里可以查看基于字符的设备比如 tty ，串行口等。 
- /cdrom Linux 所有的 CDROM 代码。在这里可以找到特殊的 CDROM 设备（比如 Soundblaster CDROM ）。注意 ide CD 驱动程序是 drivers/block 中的 ide-cd.c ，而 SCSI CD 驱动程序在 drivers/scsi/scsi.c 中 
- /pci PCI 伪驱动程序。这是一个观察 PCI 子系统如何被映射和初始化的好地方。 Alpha AXP PCI 整理代码也值得在 arch/alpha/kernel/bios32.c 中查看 
- /scsi 在这里不但可以找到所有的 Linux 支持的 scsi 设备的驱动程序，也可以找到所有的 SCSI 代码 
- /net 在这里可以找到网络设备驱动程序比如 DEC Chip 21040 PCI 以太网驱动程序在 tulip.c 中 
- /sound 所有的声卡驱动程序的位置 