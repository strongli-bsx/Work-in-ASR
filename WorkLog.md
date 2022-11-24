for server :

```html
https://sh2-cis01.asrmicro.com/guacamole/#/client/MjUAYwBwb3N0Z3Jlc3Fs
https://sh2-cis01.asrmicro.com/jenkins/view/gerrit/
```

[jenkins](https://sh2-cis01.asrmicro.com/jenkins/view/gerrit)  

[server](https://sh2-cis01.asrmicro.com/guacamole)

7.20

> 1. About Burn : Use  Aboot, click Release, choose correspond file, click download.  
> 2. How to know burn successsful? Add flag in log.  
> 3. Map network dirve. Click network, find ip in service.

---

 7.21

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
   cd --
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

 7.22

1. STAR PROCESSOR  
   
   - LSR : logical shift right
   
   - ASR : arithmetic shift right
   
   - ROR : rotote right
     
     > Note : the difference between LSR and RSR is the sign bit. ASR  sign bit is contant, while LSR donot have sign bit, and its highest bit is 0.

2. Saturating Instruction. This instruction is to prevent the calculation results overflow.

3. Contiki-NG OS.

---

 7.25

1. Learn concepts and advs. about Contiki OS, and details log in notebook.
2. Create hello-world project. The initial OS has example folder, but also has hello-world.c file. Just follow the tutorial.

---

 7.26

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

 7.27

Today did one thing: write a bug.

---

 7.28

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

7.29

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

 8.2

1. Read ARM-R/M cortex about startup and details write in future.
2. Modify test_process.c file
   - printf should not addr of *p at the same as printf content of *p.
   - 32bit OS, 0xAA, 0x00, 0x00, 0x00.
3. eMMC file write() and read() means write data to eMMC nor flash and read to assigned addr.

---

 8.3

1. Do task same as yesterday.
2. > Note:
   > - probe is init in project.  
   > - make cmd: add cmd as `USEMODULE += FLASH` and `CFLAG += -DUSE` in makefile. 
3. >  Aboot:
   > - when burn in ③, press RST at the same time press DWL **all the time**.
   > - when burn in ②, press DWL **all the time** at the same time press RST.

---

 8.4(Thu.)

1. Complete the work that was not done yesterday--test_process in boot2 successful.
2. There are many problems. But details is the key to accomplish work.
3. ```c
   if(cnt++)//cnt++ --> cnt += 1 This is a equation, that means is judged to be true.  
   ```

---

 8.5(Fri.)

1. do nothing because of acid reflux.

---

 8.8(Mon.)

1. ```c
   _attribute_((weak))//weak func.,means declare a func. If user define the func, compile user, or compile weak.
   ```
   
   void *p // no point type, means do not use the various
   void data //means do not use 
   
   char *p = 0 // means a null pointer
   char *p, p = 0

2. extern : use for declare static or global various, convenient for calling of other partition.

3. uintptr_t : unsigned int, alignment

---

 8.9(Tue.)

1. ```c
   __attribute__(noinline)//no inline function
   ```

---

8.10(Wed.)

1. Read some summaries and write down.

---

 8.11(Thu.)

1. New Targets: Replace cm4 in cpu/arch/jacana with RISC-V.

---

 8.12(Fri.)

1. Read some material about RISC-V.

---

 8.15(Mon.)

1. Learn the book named RISC-V Reader.   

---

 8.16(Tue.)

1. Read book about RISC-V.
2. Write relevant content down.

---

 8.17(Wed.)

1. Read book about asm.
2. Write relevant content down.

---

 8.18(Thu.)

1. Install RISC-V compile environment.

---

 8.19(Fri.)

1. Install RISC-V compile environment totally.
2. Run a test program in RVE.

---

 8.22(Mon.)

1. Try to figure out the problem that raised in meeting yesterday.

---

 8.23(Tue.)

1. Go on.(The task were not accomplished yesterday).

---

 8.24(Wed**.)**

1. Go on.
2. Read RISC-V ISA.

---

 8.25**(**Thu**.)**

1. Nothing.

---

 8.26(Fri.)~9.1(Thu.)

1. Log in note book.

---

---

---

9.16

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

 10.24(Mon.)

    Read makefile in arm, cortex-m, cm4. 

---

10.25(Tue.)

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

8. export VARITOU: 表示将改变量传给下层

​	unexport VARIOUS: 表示不将变量传给下层

9. `-`表示忽略执行过程中的错误

---

10.26(Wed.)

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
   #函数“ shell”所实现的功能和shell中的引用（``）相同，实现对命令的扩展
   
   $(info information)
   #在Makefile中实时输出信息
   
   $(abspath NAME)
   #将NAME中的各路径转换成绝对路径，并返回
   
   $(patsubst PATTERN,REPLACEMENT,TEXT)
   #将TEXT中所有符合PATTERN的单词替换成REPLACEMENT
   ```
   
   
   
3. Try to make clear helloWord in contiki-os

---

 10.27(Thus.)

1. Understand the helloworld in example how to work

2. The "contiki-conf.h" 在platform中native文件夹目录下

3. 代码规范：`.`(表示当下目录)最后单写一行，不然阅读时候很容易漏掉

---

10.28(Fri.)

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

10.31(Mon.)

1. `CONTIKI_TARGET_DIRS = .`先理解成已经将当前目录下的文件都添加进去了（还未得到验证，但由现象倒推的话，是这样的）
2. 原项目中是如何包含头文件的？答：是通过一层层嵌套，包含在arm项目下，或者其他文件中。
3. Makefile中gcc参数的含义：

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
     - -Werror：要求GCC将所有的警告当成错误进行处理
     - -x：设定文件所使用的语言, 使后缀名无效, 对以后的多个有效, 如 -x c 
     - 


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

---

11.3(Thu.)

1. GCC中arm参数(-m有关的)：

   ```shell
   -mabi= name 				    # 为指定的ABI生成代码 
   -mapcs-frame				    # 为所有功能生成符合ARM过程调用标准的堆栈框架 
   -mthumb-interwork				# 生成支持ARM和Thumb之间调用的代码 
   -mno-sched-prolog				# 防止对函数重新排序
   -mfloat-abi= name				# 浮点ABI
   
   -mlittle-endian       			 # 小端格式
   -mbig-endian					# 大端格式
   -mwords-little-endian
   -mcpu= name						# 指定处理器
   -mtune= name					# 指定ARM处理器可以优化
   -march= name					# ARM体系结构名称
   
   ```

2. GCC中riscv参数(-m有关的):

   ```shell
   -mbranch-cost=n  			
   # 将分支的成本设置为大约 n 条指令。
   
   -mplt					    
   -mno-plt
   # 允许或不允许使用PLT。默认是-mplt.
   
   -mabi=name
   # 指定整数和浮点调用约定。
   # 如 ‘-march = rv64ifd -mabi = lp64d’
   # 如，“-march = rv32if -mabi = ilp32d’
   
   -mfdiv
   -mno-fdiv
   # 是否使用硬件浮点除法和平方根指令
   
   -mdiv
   -mno-div
   # 是否使用硬件指令进行整数除法。
   
   -march=name
   # 包括“rv64i’，‘rv32g’，'rv32e’和’rv32imaf’
   # When-march=没有指定,则使用来自-mcpu.
   
   -mcpu=processor-name		
   # ‘sifive-e20’，‘sifive-e21’，‘sifive-e24’，‘sifive-e31’，‘sifive-e34’，‘sifive-e76’，‘sifive-s21’，‘sifive-s51’，‘sifive-s54’，‘sifive-s76’，'sifive-u54’和’sifive-u74’.
   
   
   -mtune=processor-name		
   # ‘rocket’，‘sifive-3-series’，‘sifive-5-series’，
   # ‘sifive-7-series’，‘size’，以及所有有效选项-mcpu=.
   # When-mtune=没有指定,则使用来自-mcpu, 默认为 ‘rocket’ 如果两者都没有指定。
   
   -mpreferred-stack-boundary=num
   # 尝试使堆栈边界与2对齐，以提高到 num 字节边界。
   # 如果-mpreferred-stack-boundary未指定,默认为4(16字节或128位)。
   
   -msmall-data-limit=n
   # 将小于 n 个字节的全局和静态数据放入一个特殊部分（在某些目标上）。
   
   -msave-restore
   -mno-save-restore
   # 是否使用较小但较慢的使用库函数调用的序言和结尾代码
   
   -mshorten-memrefs
   -mno-shorten-memrefs
   # 目前仅针对 32 位整数加载/存储。
   
   -mstrict-align
   -mno-strict-align
   # 不产生或不产生不对齐的内存访问。
   
   -mcmodel=medlow
   # 生成中低码模型的代码。
   
   -mcmodel=medany
   # 生成中任何代码模型的代码。
   
   -mexplicit-relocs
   -mno-exlicit-relocs
   # 使用或不使用汇编器重定位操作符
   
   -mrelax
   -mno-relax
   # 利用链接器松弛来减少实现符号地址所需的指令数量。
   
   -memit-attribute
   -mno-emit-attribute
   # 额外信息记录到ELF对象中。需要 binutils 2.32。
   
   -malign-data=type
   # 控制GCC如何对齐数组，持的 type 值为“xlen’使用x寄存器宽度作为对齐值，
   
   -mbig-endian
   # 生成大端代码。
   
   -mlittle-endian
   # 生成小端代码。
   
   -mstack-protector-guard=guard
   -mstack-protector-guard-reg=reg
   -mstack-protector-guard-offset=offset
   # 使用canary at guard 生成堆栈保护代码
   
   ```

3. lds文件的相关知识：

   - 装载地址(load memory addr.)：运行之前各段的地址；
   - 运行地址(virtual memory addr.)：运行时各段的地址
   - AT(ldadr)：定义本段存储（加载）的地址，如果不使用这个选项，则加载地址等于运行地址，通过这个选项可以控制各段分别保存于输出文件中不同的位置。
   - `-T`选项用以指定自己的链接脚本, 它将代替默认的连接脚本

   ```
   连接器有个默认的内置连接脚本, 可用`ld --verbose`查看。 连接选项`-r`和`-N`可以影响默认的连接脚本。
   你也可以使用<暗含的连接脚本>以增加自定义的链接命令
   
   链接器把一个或多个输入文件合成一个输出文件
   输入文件: 目标文件或链接脚本文件
   输出文件: 目标文件或可执行文件
   目标文件(包括可执行文件)具有固定的格式, 在UNIX或GNU/Linux平台下, 一般为ELF格式
   
   目标文件的每个section至少包含两个信息: 名字和大小
   一个section可被标记为“loadable(可加载的)”或“allocatable(可分配的)”
   loadable section: 在输出文件运行时, 相应的section内容将被载入进程地址空间中
   allocatable section: 内容为空的section可被标记为“可分配的”
   在输出文件运行时, 在进程地址空间中空出大小同section指定大小的部分
   某些情况下, 这块内存必须被置零
   如果一个section不是“可加载的”或“可分配的”, 那么该section通常包含了调试信息. 
   可用objdump -h命令查看相关信息
   
   在目标文件中, loadable或allocatable的输出section有两种地址: 
   VMA(virtual Memory Address)和LMA(Load Memory Address). 
   VMA是执行输出文件时section所在的地址, 而LMA是加载输出文件时section所在的地址
   在嵌入式系统中, 经常存在加载地址和执行地址不同的情况: 
   比如将输出文件加载到开发板的flash中(由LMA指定), 
   而在运行时将位于flash中的输出文件复制到SDRAM中(由VMA指定)
   
   可这样来理解VMA和LMA, 假设:
   data section对应的VMA地址是0x08050000, 该section内包含了3个32位全局变量, i、j和k, 分别为1,2,3，text section内包含由`printf( "j=%d ", j );`程序片段产生的代码
   连接时指定.data section的VMA为0x08050000, 产生的printf指令是将地址为0x08050004处的4字节内容作为一个整数打印出来.
   如果.data section的LMA为0x08050000，显然结果是j=2
   如果.data section的LMA为0x08050004，显然结果是j=1
   ---------------------------------------------------------------------------
   OUTPUT_FORMAT("elf32-littlearm", "elf32-littlearm", "elf32-littlearm")  
   					   #指定输出可执行文件是elf 格式,32位ARM 指令,小端(正常)
   OUTPUT_ARCH(arm) 		#指定输出可执行文件的平台为ARM
   ENTRY(_start)            #指定入口地址为_start标号所在的位置   
   
   SECTIONS
   {
       . = 0x00000000 ; 	#定位器定位到从0x0位置
       . = ALIGN(4)   ; 	#代码以4字节对齐
       .text: {
           start.o (.text)
           *(.text)
       }
       . = ALIGN(4)
       .rodata : { *(.rodata) }
       . = ALIGN(4);
       .data   : { *(.data) }
       . = ALIGN(4);
       .bss : {
           __bss_start = .;
           *(.bss)
           __bss_end = .;
       };
       . = ALIGN(4);
       _end = .;
   }
   
   ```

4. **RISC-V架构默认小端格式**，虽然也支持大端格式，但还不清晰。所以不需要特别指定

---

11.4(Fri.)

1. ```
   #push代码
   git push origin HEAD:refs/for/master
   ```

2. 在gnu中，除了o开头的（多个字母）参数往外，’--‘与’-‘效果相同，如下：

   ```shell
   --specs=nano.specs --specs=nosys.specs
   -specs=nano.specs -specs=nosys.specs
   #上述在表达效果上相同
   
   -omagic    #输出文件名设置为'magic'
   --omagic   #设置 NMAGIC 标志在输出上
   #以小写“o”开头的多个字母选项只能用两个破折号
   
   ```


---

11.7(Mon.)

1. `#ifndef..., define ...,` 可以防止头文件重复包含

2. ```c
   int *p = (int *) 0x100; // 指针p指向0x100地址处
   ```

3. `_buildtin_clz`“：返回前面引导位 0 的个数，例 0->31, 2->30

4. ```c
   void *p; // 无类型指针，可指向任意类型的数据
   (void) data; // 表示下面未使用该变量
   ```

5. `extern`用于显示声明某个全局变量或者静态变量，方便函数调用

6. lds文件中参数的含义：

   ```
   -R: only read
   -W: write/read
   -A: allocate
   -L: initial partiment
   ```

7. makefile 中的makefile.include，在计算目录的时候都是从make(动作发起)的地方算起的，不是从.included 的目录算起

8. GCC在编译时可以使用 `-ffunction-sections` 和 `-fdata-sections` 将每个函数或符号创建为一个sections，其中每个sections名与function或data名保持一致。而在链接阶段， `-Wl,–gc-sections` 指示链接器去掉不用的section（其中`-wl`, 表示后面的参数 `-gc-sections` 传递给链接器）

---

11.8(Tue.)

1. stack frame（栈帧）是用来追踪代码的调用过程和调用时的参数，通过读取stack frame信息可以知道到执行到当前位置的函数调用链表（call stack)

   

   Stack frame的本质是每次函数调用都在stack里记录一个frame，每一次函数调用叫做一个frame。ARM里的fp寄存器实现此功能，fp总是指向当前函数堆栈的frame

   

   Stack frame的产生方法：gcc在生成可执行代码时，在每个函数入口的地方“放置”一个stack frame，如下

   ```shell
   -fomit-frame-point 		#让gcc不产生stack frame
   -fno-omit-frame-pointer  	#让gcc产生stack frame
   ```

2. 内置函数分为两类：
   
    一类与标准c库函数对应，例如strcpy()有对应的builtin_strcpy()内建函数；
    
    另一类是对库函数的拓展
    
    **内置函数名称：**通常以builtin_作为函数名前缀，老的版本还可能以__sync作为前缀。

   ```shell
   -fbuiltin     #这是默认选项，用于通过名字来识别内建函数
    
   -fno-builtin  #除非利用前缀 __builtin_ 进行引用，否则不识别所有内建 函数
   #例如，为了获得内建版本，应该调用 __builtin_strcpy() 而不是名为 strcpy() 的函数
   
   -fno-builtin-xxx  #-fno-builtin-fgets，想使用除fgets() 之外的所有内建函数 
   ```

3. 当变量定义但未使用时，使用**void**关键字来屏蔽警告，如下：

   ```c
   int a;
   (void) a;  //编译器不会提示warning或error(当时用Werror的时候)
   ```
---

11.9(Wed.)

1. 使用gcc的-E -P选项展开源代码中的宏

2. crt0.o: 'C' runtime library. 

3. 工具链中配置as为gcc，所以在编译的时候需要添加一系列的参数，同gcc一样

   ```shell
   ASFLAGS += $(CFLAGS)
   ASFLAGS += -c
   ```

   

---

11.10(Thu.)

1. `-Wunused-const-variable` 打开未使用const 变量类型的警告 

    `-Wno-unused-const-variable` 关闭未使用const 变量类型的警告
    
2. 在其他项目中，并没有添加`CFLAGS += -specs=...`，可能是原工程项目是arm有关，现项目下需要添加`CFLAGS += -specc=picolibc.specs`，才可

---

11.11(Fri.)

1. .S和.s这两种文件都是汇编代码，其区别在于：.s 格式的汇编文件中， **只能包含纯粹的汇编代码** ，汇编器只对其进行汇编操作，没有预处理操作；.S 格式的汇编文件中， 还可以使用预处理命令 ，汇编器会先进行预处理，然后再进行汇编
2. 汇编中的函数，在预编译，编译，都会将代码处理成汇编代码；所以汇编中调用的函数，相当于是在汇编中找标签，不用特别包含引用

---

11.14(Mon.)

1. “.option push”伪操作暂时将当前的选项设置保存起来，从而允许之后使用.option伪操作指定新的选项；而“.option pop”伪操作将最近保存的选项设置恢复出来重新生效。

   通过“.option push”和“.option pop”的组合，便可以在汇编程序中在不影响全局选项设置的情况下，为其中嵌入的某一段代码特别地设置不同的选项

2. GNU中attribute分为函数、结构体，变量属性

   - 常用函数属性：

     - noreturn: 无返回值

     - always_inline: 总是内联
     - noinline: 无内联
     - flatten: 每个函数调用作内联
     - pure: 只有返回值
     - const: 不读全局变量
     - sentinel: NUll作为最后一个参数
     - format: 按printf. scanf检查
     - section("name")
     - unused: 未使用，但不警告
     - used: 避免未使用优化掉参数

   - 常用结构体属性：

     - aligned: 对齐，若超过，则选最大
     - packed: 让指定结构体按字节对齐

   - 常用变量属性：

     - aligned: 对齐
     - section("name")
     - at(0x0010): 按绝对地址写入

3. **在软件设计中不要总使用为真作为判断依据**

---

11.15(Tue.)

---

11.16(Wed.)

1. `#undef MACRO`: 取消前面的宏定义符号

---

11.17(Thu.)

1. 如果没有形成新功能的话，使用`git --amend`进行提交

---

11.18(Fri.)

---

11.21(Mon.)

1. RV约定的寄存器分配

   | 寄存器  | 汇编名称 | 功能描述                                               |
   | ------- | -------- | ------------------------------------------------------ |
   | x0      | zero     | 零寄存器                                               |
   | x1      | ra       | 返回地址                                               |
   | x2      | sp       | 栈指针                                                 |
   | x3      | gp       | 全局指针                                               |
   | x4      | tp       | 线程指针                                               |
   | x5      | t0       | 临时寄存器，或者用作替代链接寄存器                     |
   | x6      | t1       | 临时寄存器                                             |
   | x7      | t2       | 临时寄存器                                             |
   | x8      | s0/fp    | 该寄存器需要被调函数予以保存，或也可用作调用栈的帧指针 |
   | x9      | s1       | 该寄存器需要被调函数予以保存                           |
   | x10~x11 | a0~ a1   | 函数参数或返回值                                       |
   | x12~x17 | a2~a7    | 函数参数                                               |
   | x18~x27 | s2~s11   | 该寄存器需要被调函数予以保存                           |
   | x28~x31 | t3~t6    | 临时寄存器                                             |

2. bool类型，返回值用TRUE跟FALSE，不用0和1

3. CLINT: 处理器核局部中断控制器，Core Local Interrupts Controller，CLINT 是一个存储器地址映射的模块。**注意**：CLINT 的寄存器只支持`Size 32` 位的读写访问，主要用于产生计时器中断和软件中断

   PLIC: 平台级别中断控制器，Platform Level Interrupt Controller， PLIC将多个外部中断源仲裁为一个单比特的中断信号，送入处理器核作为机器模式外部中断

4. 外部中断、计时器中断和软件中断都会反映在CSR的mip中，通过对CSR寄存器mie进行配置，以屏蔽相应类型的中断

5. RISC-V标准CSR

   - misa(ISA): 1->RV32, 2->RV64, 3->RV128
   - mscratch: 用于机器模式下的程序临时保存某些数据, 退出异常时恢复至REG
   - mcause: 最高 1 位为中断位，低 31 位为异常
   - mtvec: 用于配置异常的入口地址 
   - mepc: 用于记录异常之前的PC值
   - mie: 用于控制不同中断类型的局部屏蔽  
   - mstatus: 状态寄存器

---

11.2(Tue.)

1. PLIC将每个中断目标都做了编号，不同Hart的不同模式，作为一个编号

2. PLIC将每个中断目标都设置优先级阈值，当阈值高于目前的目标时，则转去执行高阈值的目标。优先级的数字越大，则表示优先级越高，优先级 0 意味着“不可能中断”，相当于将此中断源屏蔽；若多个中断源具有相同的优先级，仲裁时选择 ID 数目最小的中断源  

3. PLIC为每个中断源分配了不同的ID，ID为 0 表示中断源不存在，ID从 1 开始有效

4. RV32C——16位压缩格式，压缩格式中立即数位数更少，能使用的寄存器也比较少，有些指令只能用常用8个整数寄存器（x8-x15）或者(f8-f15)。16 位指令只对汇编器和链接器可见，并且是否以短指令取代对应的宽指令由它们决定，RV32C 中没有字节或半字指令  

5. 内联汇编：

   ```java
   _asm__ __violate__ ("movl %1,%0" : "=r" (result) : "m" (input));
   ```

   `movl %1,%0`是指令模板；`%0`和`%1`代表指令的操作数，称为占位符。内嵌汇编靠它们将 C 语言表达式与指令操作数相对应。指令模板后面用小括号括起来的是C语言表达式，本例中只有两个：`result`和`input`，他们按照出现的顺序分别与指令操作数`%0`，`%1`对应；注意对应顺序：第一个C表达式对应`%0`；第二个表达式对应`%1`，依次类推。操作数至多有10 个，分别用`%0`,`%1`….`%9`表示。在每个操作数前面有一个用引号括起来的字符串，字符串的内容是对该操作数的限制或者说要求。 `result`前面的限制字符串是`=r`，其中`=`表示`result`是输出操作数，`r` 表示需要将`result`与某个通用寄存器相关联，先将操作数的值读入寄存器，然后在指令中使用相应寄存器，而不是`result`本身，当然指令执行完后需要将寄存器中的值存入变量`result`，从表面上看好像是指令直接对`result`进行操作，实际上GCC做了隐式处理，这样我们可以少写一 些指令。`input`前面的`m`表示该表达式需要先放入某个寄存器，然后在指令中使用该寄存器参加运算。

   - a,b,c,d,S,D 分别代表 eax,ebx,ecx,edx,esi,edi 寄存器
   - r 上面的寄存器的任意一个（谁闲着就用谁）
   - m 内存
   - i 立即数（常量，只用于输入操作数）
   - g 寄存器、内存、立即数 都行（gcc你看着办）

6. ```c
   typedef  oldName  newName;
   ```

7. 位域：

   ```c
   struct Date 
   {
      unsigned nWeekDay  : 3;    // 1..7   (3 bits)
      unsigned nMonthDay : 6;    // 1..31  (6 bits)
      unsigned           : 0;    // Force alignment to next boundary.
      unsigned nMonth    : 5;    // 1..12  (5 bits)
      unsigned nYear     : 8;    // 1..100 (8 bits)
   };
   //分配内存是按照既定好的位数
   //先忽略占位为0的代码
   //short类型为16位，则3+6+5+8>16, 超过16位则最后8占位不能连续存储，需从新的开始
   ```

8. **#define**：

   - 使用#把宏参数变为一个字符串
   - 用##把两个宏参数贴合在一起
   - #@x，其实就是给x加上单引号，结果返回是一个const char

   **注意：**当宏定义中的参数是另一个宏，且该宏展开中有#符号，则该宏不会生效；解决办法是使用中间转换

---

11.23(Wed.)

1. 伪指令意味着它并不是一条真正的指令，而是对其他基本指令使用形式的一种别名
2. `#pragma`指令的作用是：用于指定计算机或操作系统特定的编译器功能
3. 以**单下划线**（_）表明是**标准库**的变量，而**双下划线**（__） 开头表明是**编译器**的变量
4. U: Unsigned int 的简写
5. 在s模式的系统中，medeleg和mideleg寄存器必须存在；当发生在s模式或u模式时，在medeleg或mideleg中设置一个位，将代理相应的trap，送给s模式trap程序处理。在没有s模式的系统中，medeleg和mideleg寄存器不应该存在

---

11.24(Thu.)

1. 
