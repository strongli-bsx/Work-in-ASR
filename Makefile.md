## Makefile：

### 1 基本语法

#### 1.1 Makefile 变量赋值

- **` 简单赋值(:=) 只对当前语句的变量有效,`**

  换句话说，前面你对这个变量怎么赋值的我不管，我在这里对它赋值，那它就等于我赋给它的值

- **`递归赋值(=)`**

  这么理解，每次调用变量时，变量的值都会被动态计算

- **`条件赋值 ( ?= )`**
  如果变量未定义，则使用符号中的值定义变量。如果该变量已经赋值，则该赋值语句无效

- **` 追加赋值 ( += )`**
  原变量用空格隔开的方式追加一个新值
  
- `CURDIR`是Makefile的内嵌变量，自动设置为当前目录
  
  `RIOTBASE = $(realpath $(CURDIR)../..)`



#### 1.2 Makefile 符号

这些符号是Makefile中的特殊变量，用于在规则中引用文件名和目标，

- `$^` 用于表示所有的依赖文件列表，多个文件以空格分隔。在规则中，它可以用来引用所有依赖文件的列表。例如：

```
target: dependency1 dependency2 dependency3
    command $^
```

在这个例子中，`$^` 将会展开为 `dependency1 dependency2 dependency3`。

- `$@` 用于表示目标文件的名称。在规则中，它可以用来引用目标文件的名称。例如：

```
target: dependency1 dependency2 dependency3
    command $@
```

在这个例子中，`$@` 将会展开为 `target`。

- `$<`用于表示规则中的第一个依赖文件。通常在单目标多源文件的情况下使用。例如：

```
target: dependency1 dependency2
    command $<
```

在这个例子中，`$<` 将会展开为 `dependency1`。

- `$? `用于表示所有比目标文件新的依赖文件列表。通常在需要重新生成目标文件的情况下使用。例如：

```
target: dependency1 dependency2
    command $?
```

在这个例子中，如果 `dependency1` 比 `dependency2` 新，则 `$?` 将会展开为 `dependency1`；如果 `dependency2` 比 `dependency1` 新，则 `$?` 将会展开为 `dependency2`；如果两者都是相同的时间戳，则 `$?` 将为空。

- `$* `用于表示规则中目标文件的文件名部分（不包括扩展名）。通常在需要将目标文件名作为参数传递给命令时使用。例如：

```
%.o: %.c
    gcc -c $< -o $@
    ./process $*
```

在这个例子中，如果目标文件是 `example.o`，则 `$*` 将会展开为 `example`。

- % 和 * 的区别

  *是应用在系统中的，%是应用在这个Makefile文件中的

#### 1.3 变量替换

​	`$(var:a=b)`: 将 var 中的 a 替换为 b

模式替换:

```shell
targets: target-pattern : prereq-pattern
#target-pattern 从 target 中匹配子目标；再通过 prereq-pattern 从子目标生成依赖； 进而构成完整的规则

OBJS := func.o main.o
$(OBJS) : %.o : %.c
	gcc -o $@ -c $^

func.o : func.c
	gcc -o $@ -c $^
	
main.o : main.c
	gcc -o $@ -c $^
	
#for example
CC := g++							# 变量的简单赋值
TARGET := hello-makefile.out
OBJS := func.o main.o const.o

$(TARGET) : $(OBJS)
	$(CC) -o $@ $^

$(OBJS) : %.o : %.c					# 采用规则中的模式替换
	$(CC) -o $@ -c $^

.PHONY : rebuild clean all			# 声明伪目标

rebuild : clean all

all : $(TARGET)

clean :
	$(RM) *.o $(TARGET)    			# $(RM)：用于删除文件的命令

```





---

### 2 相关函数

```shell
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

$(foreach <var>, <list>, <text>)
#(1) var：临时变量；
#(2) list：以空格隔开的文件列表，每一次取一个文件名单词赋值为变量 var；
#(3) text：对 var 变量进行操作（一般使用 var 变量，不然没意义），每次操作结果都会以空格隔开，最后返回空格隔开的列表。
#函数解释：把参数 <list> 中的单词逐一取出放到参数 <var> 所指定的变量中，然后再执行 <text> 所包含的表达式。
#每一次 <text> 会返回一个字符串，循环过程中，<text> 表达式所返回的每个字符串会以空格分隔。
#最后当整个循环结束时，<text> 所返回的每个字符串所组成的整个字符串（以空格分隔）将会是 foreach 函数的返回值。
#所以，<var> 最好是一个变量名，<list> 可以是一个表达式，而 <text> 中一般会使用 <var> 这个参数来依次枚举 <list> 中的单词。

```



### 3 使用总结

- 在Makefile中的include要记得看路径是否正确

- Makefile中管道符-->`|`：有时，需要定义一个这样的规则，在更新目标（ 目标文件已经存在）时只需要根据依赖文件中的部分来决定目标是否需要被重建，而不是在依赖文件的任何一个被修改后都重建目标。为了实现这一目的，相应的就需要对规则的依赖进行分类，一类是在这些依赖文件被更新后，需要更新规则的目标；另一类是更新这些依赖的，可不需要更新规则的目标。我们把第二类称为：“ order-only”依赖。书写规则时，“ order-only”依赖使用管道符号“ |”开始，作为目标的一个依赖文件。规则依赖列表中管道符号“ |”左边的是常规依赖，管道符号右边的就是“ order-only”依赖。这样的规则书写格式如下：  
  TARGETS : NORMAL-PREREQUISITES | ORDER-ONLY-PREREQUISITES
  - $(Q) 变量的本质就是 Makefile中的命令显示与否，Makefile.include 中 有定义


  - |grep就是指把上个命令运行的结果通过管道命令带入到grep的参数里执行，
    所以单纯的grep没什么意义，一般使用都是通过管道符来使用grep


  - -*v* 表示 select no-macthing lines，相当于把不符号的 case 都罗列出来


  - (\s*)表示连续空格的字符串


- make命令可以显式定义DEFINES，为c预处理设定任意的变量：**make TARGET=esb DEFINES=MYTRACE,MYVALUE=4711**

​	还可以保存默认的DEFINES到**Makefile.$(TARGET).DEFINES**中：**make TARGET=esb DEFINES=MYTRACE,MYVALUE=4711 savedefines**

- 通过变量“VPATH”可以指定依赖文件的搜索路径

- 在Makefile中输出信息：`$(info information)`，`$(error storng)`，`$(waring wning~)`

- export VARITOU: 表示将改变量传给下层

​	unexport VARIOUS: 表示不将变量传给下层

- `-`表示忽略执行过程中的错误

- 在Makefile中所有出现的宏，有且只能有一次定义为 `.`，也就相当于固定了基准地址

- Makefile 包含目录时要包含到具体文件所在的分级目录

- 代码规范：`.`(表示当下目录)最好单写一行，不然阅读时候很容易漏掉



### 4 mk中gcc参数：

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



在gnu中，除了o开头的（多个字母）参数外，’--‘与’-‘效果相同，如下：

```shell
--specs=nano.specs --specs=nosys.specs
-specs=nano.specs -specs=nosys.specs
#上述在表达效果上相同

-omagic    #输出文件名设置为'magic'
--omagic   #设置 NMAGIC 标志在输出上
#以小写“o”开头的多个字母选项只能用两个破折号

```


---

#### 4.1 attribute

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
  - naked: 裸函数，编译器不会生成入口代码和退出代码，只有编译器生成的 prolog 和 epilog 序列的性质受到 naked 属性的影响
  - constructor: 在执行 main 函数之前执行此函数
  - destructor: 在 main 函数后调用
- 常用结构体属性：

  - aligned: 字节对齐，若超过，则选最大
  - packed: 取消结构体在编译过程中的优化对齐，按照实际占用字节数进行对齐
- 常用变量属性：

  - aligned: 对齐
  - section("name")
  - at(0x0010): 按绝对地址写入

---

- Q: USEMODULE 是如何将全部的 c 文件添加进去的？

- A: `SRC += $(patsubst $(BASE_MODULE)_%,%.C,$(filter $(BASE_MODULE)_%, $(USEMODULE)`

---

#### 4.2 ((naked))

prolog 和 epilog 

```c
首部代码
push        ebp                    ; Save ebp
sub         esp, localbytes        ; Allocate space for locals
mov         ebp, esp               ; Set stack frame pointer
push        <registers>      ; Save registers

    
尾部代码
pop            ; Restore registers
pop         ebp           ; Restore ebp
mov         esp, ebp      ; Restore stack pointer
ret                       ; Return from function

```

---

### 5 linux

- Linux系统预留可三个文件描述符：0、1和2，他们的意义如下所示：

  0——标准输入（[stdin](https://so.csdn.net/so/search?q=stdin&spm=1001.2101.3001.7020)）

  1——标准输出（stdout）

  2——标准错误（stderr）

  ```shell
  touch 123.txt
  ls 123.txt 1> stdout.txt
  cat stdout.txt # 123.txt
  
  ls abc.txt 2> stderr.txt
  cat stderr.txt # no such file or directory
  
  # /dev/null 是一个特殊设备，会丢弃所有写入的信息，也被称为黑洞或位桶
  #2>/dev/null 的意思就是将标准错误stderr删掉
  2>/dev/null
  ```

-  which unzip 2>&1 > /dev/null：这段代码的作用是检查系统中是否安装了unzip命令，并打印当前Shell脚本的进程ID

       which unzip 2>&1 > /dev/null：这是一个命令，它使用which命令来查找系统中unzip命令的路径。2>&1表示将标准错误（stderr）重定向到标准输出（stdout），> /dev/null表示将标准输出（stdout）重定向到空设备文件，即丢弃输出。因此，这个命令的目的是检查系统中是否安装了unzip命令，但会将输出结果丢弃。
       
       echo $$：这是一个echo命令，用于打印特殊变量$$的值。在Shell中，$$表示当前正在运行的进程的进程ID（PID）。因此，这个命令的目的是打印当前Shell脚本的进程ID。

-  sed 's/^ //'

   ```
   sed 是正则表达式中的替换命令
   s/ 代表替换
   
   ```

   
