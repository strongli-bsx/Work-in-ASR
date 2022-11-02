The Internet for server :

```html
https://sh2-cis01.asrmicro.com/guacamole/#/client/MjUAYwBwb3N0Z3Jlc3Fs
https://sh2-cis01.asrmicro.com/jenkins/view/gerrit/
```

[jenkins](https://sh2-cis01.asrmicro.com/jenkins/view/gerrit)  

[server](https://sh2-cis01.asrmicro.com/guacamole)

**7.20**

> 1. About Burn : Use  Aboot, click Release, choose correspond file, click download.  
> 2. How to know burn successsful? Add flag in log.  
> 3. Map network dirve. Click network, find ip in service.

---

 **7.21**

1. burn craneG:
   
   - Use the compiled code in gerrrit, for the code in ubuntu cannot download in PC.
   - Run sscom.exe and press RESET buttton, then you can see the version.Replace the old file with the new file in version folder.  
   - Run Aboot.exe and click Release dashboard, choose the correspond chip, click Release button. After release finished, click the Download button. Specially, press the RESET button and the DOWNLOAD button in DKB and the chip will enter burn program mode.
   - Note: You can read the log output of sscom to check the code.  

2. git command:
   
   ```git
   git checkout . : back file to workspace
   git status -s  : view the file information  
   ```

3. cd command:  
   
   ```linux
   cd /        : root 
   cd ~        : home
   cd -        : return to before dir when enter this dir.
   cd ..       : return to the previous dir.
   cd ../..    : return to the dir before previous dir.
   ```

4. vim complier:
   
   - commamd mode : use i, a, o etc to enter input mode. ues '': ' to enter the last line mode.
   - input mode : edit
   - the last line mode : use q, w etc to quit the vim. **Note** the ESC can quit this mode anytime.

---

 **7.22**

1. STAR PROCESSOR  
   
   - LSR : logical shift right
   
   - ASR : arithmetic shift right
   
   - ROR : rotote right
     
     > Note : the difference between LSR and RSR is the sign bit. ASR  sign bit is contant, while LSR donot have sign bit, and its highest bit is 0.

2. Saturating Instruction. This instruction is to prevent the calculation results overflow.

3. Contiki-NG OS.

---

 **7.25**

1. Learn concepts and advs. about Contiki OS, and details log in notebook.
2. Create hello-world project. The initial OS has example folder, but also has hello-world.c file. Just follow the tutorial.

---

 **7.26**

1. Complie project in Ubuntu, generate .out file and run the file.

2. Learn difference between and gcc and make. The first, gnu, used only for compling, but make inclues gcc command in makefile.

3. Git command. 
   
   - rm filename : delete filename in local PC.
   - git status -s : show file status in short.

4. PROCESS_THREAD used list type to design.

5. C
   
   - typedef : 
     
     ```c
     typedef unsigned int UINT; //replace UINT to int, the later replace the former
     
     typedef struct Count{
        int x;
        int y;
        int c;
     }NUM;    //NUM replace Count various.
     
     typedef struct Count{
        struct Count *p_Count;  //struct Count donot omit.
     }*pC;  //define struct Count point *pC  
     ```

6. Function Pointer
   
   ```c
   int (*p)(int, int ) //The later brackets are parameters.
   // The * is return value.
   ```

---

 **7.27**

Today did one thing: write a bug.

---

 **7.28**

1. Do not use numbers in code; use the macro replace it. The numbers is called devil numbers.

2. "_A" : use in library function 
   
   ```c
   _func_ : const char type array, storage the current function name.
   _FILE_ : string type, storage file name.
   _TIME_ : string type, storage compile time.
   _LINE_ : int type, storage line number.
   _DATE_ : string type, storage complie data.
   ```

3. extern C : compile in C style.

4. ifdef : 
   
   ```c
   #ifndef _LOG_H_ //if it do not include __LOG__H__, then define ....
   #define _LOG_H_
   #endif
   ```

5. macro:
   
   ```c
   ... // args list
   _VA_ARGS_ ;//various macro
   ```

6. LOG : use output info via comport. Note: rank different log, then when accomplished can omit low-level log.

7. how to make pointer point address: int* p = (int *) 0x100;

> **Note：** Log detailed after today. 

---

**7.29**

1. Learn how to output log in flasher mode.

2. Read the revelant code in emmc, understand read codes and write codes.

3. Read macro code in project.
   
   8.1

4. Make test code successful.

5. Be familiar with PROCESS, and make clear the PROCESS how to run.

6. The last task: test access 0xd1f00000 via DMA in eMMC.   
   **Note:** the most important part is accessing the memory via DMA, by means of read().  

7. TASK:
   
   > - ARM->RISC-V.

8. Details:
   
   - static various : just global variable, meaning the init of various. It's `changeable`.
   - macro : the replace various in code, it's unchangeable.

---

 **8.2**

1. Read ARM-R/M cortex about startup and details write in future.
2. Modify test_process.c file
   - printf should not addr of *p at the same as printf content of *p.
   - 32bit OS, 0xAA, 0x00, 0x00, 0x00.
3. eMMC file write() and read() means write data to eMMC nor flash and read to assigned addr.

---

 **8.3**

1. Do task same as yesterday.
2. > Note:
   > - probe is init in project.  
   > - make cmd: add cmd as `USEMODULE += FLASH` and `CFLAG += -DUSE` in makefile. 
3. >  Aboot:
   > - when burn in ③, press RST at the same time press DWL **all the time**.
   > - when burn in ②, press DWL **all the time** at the same time press RST.

---

 **8.4(Thu.)**

1. Complete the work that was not done yesterday--test_process in boot2 successful.
2. There are many problems. But details is the key to accomplish work.
3. ```c
   if(cnt++)//cnt++ --> cnt += 1 This is a equation, that means is judged to be true.  
   ```

---

 **8.5(Fri.)**

1. do nothing because of acid reflux.

---

 **8.8(Mon.)**

1. ```c
   _attribute_((weak))//weak func.,means declare a func. If user define the func, compile user, or compile weak.
   ```
   
   void *p // no point type, means do not use the various
   void data //means do not use 
   
   char *p = 0 // means a null pointer
   char *p, p = 0

2. extern : use for declare static or global various, convenient for calling of other partition.

3. uintptr_t : unsigned int, alignment

4. typeof: receive the return value of the function.

---

 **8.9(Tue.)**

1. ```c
   __attribute__(noinline)//no inline function
   ```

---

** 8.10(Wed.)**

1. Read some summaries and write down.

---

 **8.11(Thu.)**

1. New Targets: Replace cm4 in cpu/arch/jacana with RISC-V.

---

 **8.12(Fri.)**

1. Read some material about RISC-V.

---

 8.15(Mon.)

1. Learn the book named RISC-V Reader.   

---

 **8.16(Tue.)**

1. Read book about RISC-V.
2. Write relevant content down.

---

 **8.17(Wed.)**

1. Read book about asm.
2. Write relevant content down.

---

 **8.18(Thu.)**

1. Install RISC-V compile environment.

---

 **8.19(Fri.)**

1. Install RISC-V compile environment totally.
2. Run a test program in RVE.

---

 **8.22(Mon.)**

1. Try to figure out the problem that raised in meeting yesterday.

---

 **8.23(Tue.)**

1. Go on.(The task were not accomplished yesterday).

---

 **8.24(Wed.)**

1. Go on.
2. Read RISC-V ISA.

---

 **8.25(Thu.)**

1. Nothing.

---

 **8.26(Fri.)~9.1(Thu.)**

1. Log in note book.

---

---

---

**9.16**

1. 用uart输出函数示例

```c
ssize_t _write(int fd, const void *ptr, size_t len)
{
    const uint8_t *current = (const char *)ptr;
    if (isatty(fd)) {
        for (size_t jj = 0; jj < len; jj++)  {
            while (UART0_REG(UART_REG_TXFIFO) & 0x80000000); //等待UART的TXFIFO有空
            //向 UART 的 TXFIFO 寄存器写入字符，从而使字符通过 UART 输出
            UART0_REG(UART_REG_TXFIFO) = current[jj];
            if (current[jj] == '\n') {
                while (UART0_REG(UART_REG_TXFIFO) & 0x80000000);
                UART0_REG(UART_REG_TXFIFO) = '\r';
            }
        }
        return len;
    }
    return _stub(EBADF);
}
```

---

2. RISCV 启动代码草稿

```assembly
.section    .init,"ax",@progbits    // 定义.init 段
    .global    _start
    .align    1
_start:
    j    handle_reset                    //跳转至handle_reset入口处
    # .word expression 表示从当前位置分配若干个字空间，用expression填充
    .word 0x00000013                    //内核设计需要
    .word 0x00000013
    .word 0x00000013
    .word 0x00000013
    .word 0x00000013
    .word 0x00000013
    .word 0x00000013
    .word 0x00000013
    .word 0x00000013
    .word 0x00000013
    .word 0x00000013
    .word 0x00000013
    .word 0x00100073


    .section    .vector,"ax",@progbits  //定义中断向量表部分,progbits表明这个section储存在磁盘映像中，而不是在加载时分配和初始化。
    .align  1
_vector_base:                           //中断向量表部分
    .option norvc;                      //接下来的汇编程序不可以被汇编生成16位宽的压缩指令
        j   _start
    .word   0
        j   NMI_Handler                 /* NMI Handler */
        j   HardFault_Handler           /* Hard Fault Handler */
    .word   0
    .word   0
    .word   0
    .word   0
    .word   0
    .word   0
    .word   0
    .word   0
        j   SysTick_Handler            /* SysTick Handler */
    .word   0
        j   SW_handler                 /* SW Handler */
    .word   0
    /* External Interrupts */


    .option rvc;

    # 中断处理程序
    .section    .text.vector_handler, "ax", @progbits
    .weak   NMI_Handler
    .weak   HardFault_Handler
    .weak   SysTick_Handler


NMI_Handler:  1:  j 1b
HardFault_Handler:  1:  j 1b
SysTick_Handler:  1:  j 1b
SW_handler:  1:  j 1b


# handle_reset 的初始位置
    .section    .text.handle_reset,"ax",@progbits
    .weak    handle_reset
    .align    1
handle_reset:
.option push 
.option    norelax 
    la gp, __global_pointer$
.option    pop 
1:
    la sp, _eusrstack 
2:
    /* Load data section from flash to RAM */
    //flash中存放, RAM中运行

    la a0, _data_lma
    la a1, _data_vma    # lma 在 vma 之后
    la a2, _edata       # edata 在 vma 之后, 即vma < lma < edata
    bgeu a1, a2, 2f     # 大于等于
1:
    //加载操作
    //将a0的数据搬移到a1
    lw t0, (a0)
    sw t0, (a1)
    addi a0, a0, 4
    addi a1, a1, 4
    bltu a1, a2, 1b     # 小于(应该是相等)
2:
    /* clear bss section */
    la a0, _sbss
    la a1, _ebss
    bgeu a0, a1, 2f     # a0 < a1 
1:
    sw zero, (a0)       # 将 zero 寄存器写入到 (a0) REG
    addi a0, a0, 4
    bltu a0, a1, 1b 
2:
    /* enable all interrupt */
  li t0, 0x88
  csrs mstatus, t0     /* 机器模式状态寄存器mstatus赋值为0x88，打开所有中断，设置MPP值为00 */
    la t0, _vector_base
  ori t0, t0, 1        # or  immediate
    csrw mtvec, t0    /* 将中断向量表的首地址赋值给mtvec寄存器（中断发生时PC的地址） */     

  jal  SystemInit
    la t0, main      //call main
    csrw mepc, t0
    mret
```

---



 **10.24(Mon.)**

    Read makefile in arm, cortex-m, cm4.                                          

---

**10.25(Tue.)**

**书写Makefile总结：**

1. Makefile中PROJECT名称要跟该项目下的.c文件相同

2. 在Makefile中的include要记得看路径是否正确

3. Makefile中管道符-->`|`

   有时，需要定义一个这样的规则，在更新目标（ 目标文件已经存在）时只需要根据依赖文件中的部分来决定目标是否需要被重建，而不是在依赖文件的任何一个被修改后都重建目标。为了实现这一目的，相应的就需要对规则的依赖进行分类，一类是在这些依赖文件被更新后，需要更新规则的目标；另一类是更新这些依赖的，可不需要更新规则的目标。我们把第二类称为：“ order-only”依赖。书写规则时，“ order-only”依赖使用管道符号“ |”开始，作为目标的一个依赖文件。规则依赖列表中管道符号“ |”左边的是常规依赖，管道符号右边的就是“ order-only”依赖。这样的规则书写格式如下：  
   TARGETS : NORMAL-PREREQUISITES | ORDER-ONLY-PREREQUISITES

   - $(Q) 变量的本质就是 Makefile中的命令显示与否

   - |grep就是指把上个命令运行的结果通过管道命令带入到grep的参数里执行，
     所以单纯的grep没什么意义，一般使用都是通过管道符来使用grep

   - -*v* 表示反向选择 "*^\s*#*" 表示匹配以S开头的字符串

   - (\s*)表示连续空格的字符串

4. 在Makefile中的include要记得看路径是否正确，为了方便都是使用宏来代替的，记得要查看宏的定义，每个人定义方式不同

5. make命令可以显式定义DEFINES，为c预处理设定任意的变量：**make TARGET=esb DEFINES=MYTRACE,MYVALUE=4711**

   还可以保存默认的DEFINES到**Makefile.$(TARGET).DEFINES**中：**make TARGET=esb DEFINES=MYTRACE,MYVALUE=4711 savedefines**

6. 通过变量“ VPATH”可以指定依赖文件的搜索路径

7. 在Makefile中输出信息：`$(info information)`

---

**10.26(Wed.)**

1. 出现问题的地方可能与make的隐含规则或者默认规则有关

2. ```makefile
   $(strip <string> )
   #去掉<string>字串中开头和结尾的空字符,包括 空格, tab 等不可显示的字符
   #并将中间的多个连续空字符(如果有的话)合并为一个空字符
   
   $(wildcard PATTERN...)
   #展开为已经存在的、使用空格分开的、匹配此模式的所有文件列表
   #如果不存在任何符合此模式的文件，函数会忽略模式字符并返回空
   
   $(words TEXT)
   #计算字符串“ TEXT”中单词的数目
   #返回“ TEXT”字串中的单词数
   
   $(filter PATTERN…,TEXT)
   #过滤函数— filter,过滤掉字串“ TEXT”中所有不符合模式“PATTERN”的单词
   #返回所有符合此模式的单词
   
   $(call FUNCTION)
    #call”函数可以实现对用户自己定义函数引用
   
   
   $(addprefix PREFIX,NAMES…)
   #加前缀函数— addprefix
   
   $(shell syntax)
   #函数“ shell”所实现的功能和shell中的引用（ ``）相同，实现对命令的扩展
   
   $(info information)
   #在Makefile中实时输出信息
   ```
   
   
   
3. Try to make clear helloWord in contiki-os

---

 **10.27(Thus.)**

1. Understand the helloworld in example how to work

2. The "contiki-conf.h" 在platform中native文件夹目录下

3. 代码规范：`.`(表示当下目录)最后单写一行，不然阅读时候很容易漏掉

---

**10.28(Fri.)**

**contiki-os的使用：**

1. 在app文件夹中建立自己的项目文件夹；

2. 文件夹中包含Makefile，Makefile.target,以及同项目名称的.c文件；如下：

   ![](WorkLog.asset/725698fdfe994d7a285d5f7a1d37bd78121cf0cc.jpg)

3. 上图中的Makefile中应该包含如下代码:

   ```makefile
   #默认代码如下：
   CONTIKI_PROJECT = arom-jacna-riscv #此处名称要与改目录下的.c文件一致
   all: $(CONTIKI_PROJECT)
   
   CONTIKI = ../..
   include $(CONTIKI)/Makefile.include
   # 公司添加了一些版本号代码等
   ```

4. Makefile.target中应该包含：

   ```makefile
   TARGET = jacana-riscv
   ```

---

5. 在arch（架构）下建立文件夹，名称同4.中的TARGET名称，如下：

   ![](WorkLog.asset/662e4712577ab921d48479c0157436e60f746eb1.jpg)

        其中，必须包含的有`.lds`、`Makefile.jacana-riscv`文件，其余的看情况添加

---

6. 在platform中同样建立同名文件夹，名称同4.中的TARGET名称，如下：

   ![](WorkLog.asset/43b8b0ef92c290ded31480908c3c06f6da6e2935.jpg)

        其中，两个文件都是要包含的，其余的文件看情况添加

---

7. 下面说一下各个文件是怎么内嵌的：
   
   - 首先，app（即3.）项目文件下的Makefile中添加了`Makefile.incule`，该文件是CONTIKI-OS自带的——`Makefile.include`中实现了添加自带的所有Makefile，其中最有关联的是`Makefile.dir-variables`与`Makefile.identify-target`；
   
   - `Makefile.identify-target`中实现了找TARGET的功能，如果找到了TARGET，则使用定义的Makefile；若没找到，则使用`TARGET = native`；所以4.中定义了`TARGET=jacana-riscv`
   
   - 接着`Makefile.include`中通过以下命令在`platform`文件夹中找TARGET同名文件下的Makefile，如下：![](WorkLog.asset/6a8cd266de2fc8e7486cf69d4cd043a6d6eed887.jpg)
     
     ```makefile
     target_makefile := $(wildcard $(CONTIKI_NG_RELOC_PLATFORM_DIR)/$(TARGET)/Makefile.$(TARGET) \
     $(foreach TDIR, $(TARGETDIRS), $(TDIR)/$(TARGET)/Makefile.$(TARGET)))
     ```
   
   - 在`platform`中的`Makefile.jacana-riscv`（见6.）里面最后要包含arch(5.)中的`Makefile.jacana-riscv`路径，如下：
   
     ![](WorkLog.asset/65d5394c1b0ca8db834568bae002441a9a420d99.jpg)
   
   - 在arch下的目标文件下Makefile(见5.)中要包含文件所用的架构（如arm、riscv等）的Makefile，如下：
   
     ![](WorkLog.asset/24bc4b2660f9bf4b6a70716f0ee0a0c31d5fcf8b.jpg)
   
   - 在`Makefile.riscv`中则定义了工具链，以及CFLGAS、LDFLAGS等编译参数
   
   - `Makefile.dir-variables`中则包含了`OS`中的所有路径文件，这对于编译项目很有用，项目中一定会用到`OS`的文件

---

**10.31(Mon.)**

1. `CONTIKI_TARGET_DIRS = .`先理解成已经将当前目录下的文件都添加进去了（还未得到验证，但由现象倒推的话，是这样的）
2. 原项目中是如何包含头文件的？答：是通过一层层嵌套，包含在arm项目下，或者其他文件中。
3. Makefile中参数的含义：

     - -g：可执行程序包含调试信息，-加个-g 是为了gdb 用，不然gdb用不到

     - -o：指定输出文件名

     - -c ：只编译不链接，产生.o文件，就是obj文件，不产生执行文件

     - -D：添加宏定义，如`-D DEFINES=CONDITION`；宏定义使用前缀-D，在编译过程中可以把宏定义追加到CFLAG中，如`-D DEFINES`

     - -w：关闭编译时的警告，也就是编译后不显示任何warning

     - -W：类似-Wall，会显示警告，但是只显示编译器认为会出现错误的警告。

     - -Wall：编译后显示所有警告

     - -O3：开启编译优化，等级为三
     - -l：用来指定程序要链接的库，-l参数紧接着就是库名
     - -L：-L参数跟着的是库文件所在的目录名
     - -Wl：紧跟的参数是传递给链接器ld的
     - "-f"/"-file"：指定特定的Makefile，如`make -f Make.Linux`
     - -I：可以看作是include的首字母大写，主要是包含对应的头文件路径


4. ```makefile
   $@	# 表示目标
   $^	# 表示所有的依赖
   $<	# 表示第一个依赖
   ```

   


---

11.1(Tue.)

1. Read Makefile.include totally.

2. c中变量出处：

   ```
   uint16_t		-->  包含在<stdint.h>
   size_t/ssize_t	 -->  包含在<stddef.h>
   ```

3. c中不必指定函数返回值类型，这样它默认是int类型，如下：

   ```c
   unsigned ringbuffer_add(ringbuffer_t rb, ...){
   	if(...)   return 0;
       size_t total = MIN(...);
   	return total; 
   }
   ```

4. "conflicting type":查看声明的参数与定义参数是否一致

---

11.2(Wed.)

1. `arm-none-eabi-gcc`：是 GNU 推出的的ARM交叉编译工具。可用于交叉编译ARM MCU（32位）芯片，如ARM7、ARM9、Cortex-M/R芯片程序； `riscv64-unknown-elk`表示是64位的编译，区别在于：32位的编译链中size_t为4个字节，而64位编译链中size_t为8个字节
1. 64位的工具链能编译32位的项目，但是区别在于上面64位的size_t跟32位中不一样
1. `riscv64-unknown-elf-gcc -mabi=ilp32 -march=rv32i`用64位编译工具编译32位工程，在`CFLAGS`中添加上述参数也可编译通过
1. 

---



