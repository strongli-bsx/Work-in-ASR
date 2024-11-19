## Bat/Cmd

1. echo

​	echo on/off 打开回显或关闭回显功能

​	echo off 表示在此语句后所有运行的命令都不显示命令行本身；默认是on

​	echo [message]



2. @ 

​	不显示@后面的命令，(在入侵过程中自然不能让对方看到你使用的命令啦)

​	@ 与 echo off 相象，但它是加在每个命令行的最前面，表示运行时不显示这一行的命令行(只能影响当前行)。

```bash
 @echo off (此语句常用于开头，表示不显示所有的命令行信息，包括此句)

@echo please wait a minite...
```

3. goto label

​	label标签的名字后，**必须加个冒号“:”来表示这**个字母是标签。

4. rem <==> ::

​	注释

5. pause

​	暂停

6. call

​	call another.bat

```bash
code-style.bat arch/cpu/jacana-riscv/cpu.h #arch/cpu/jacana-riscv/cpu.h 为 call test.bat 参数1 的内容

@Rem code-style.bat
cd C:\Users\leeli\Desktop\contiki-ng\contiki-ng-develop\tools\code-style\
set dir=..\..
call test.bat %dir%\%1 	# %1 需要传入的参数，%dir%\%1 为test.cmd需要传入的参数
pause

@Rem test.cmd
uncrustify.exe --no-backup --replace -c uncrustify.cfg  %1

#shell 里面用 $ <=> %
```

7. if

```bash
 if "%1" == "a" echo a
 if not "%1" == "b" goto noparms
 
 if 1 == 0 ( echo comment1 ) else if 1==0 ( echo comment2 ) else (echo comment3 )

#注：如果 else 的语句需要换行，if 执行的行尾需用“^”连接，并且 if 执行的动作需用(括起来)，否则报错

 if 1 == 0 ( echo comment1 ) else if 1==0 ( echo comment2 ) ^
 else (echo comment3 )
```

8. set

```shell
set num=123
if "%num%" == "123" echo yes

set str=strong
if "%num%" == "strong" echo yes
```

9. timeout

```shell
timeout /t 5 # 等待5s
```





 

------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

------------------------------------------------------------------------------------------------------------------------------

## shell

1. sh 里面用 $ <=> % 来占位，可以`$1 来占位`

2. name=$(date "+%Y-%m-%d-%H-%M-%S")

3. ```shell
   read -p "The num is represent the different repos.                                                                                                        	1. bootorm                                                                                   											2. booloader																													Please input num of repo: " num
   
   case "$num" in 
   	[1-2]) 
   	git push origin HEAD:refs/for/master
   	;;
   	*)
   	echo "input num is valid!"
   	exit
   	;;
   esac
   
   
   # bat 使用如下
   @echo off
   echo.
   echo =====================================================
   echo The num represent bootrom mode:
   echo 	1.download
   echo 	2.normal 
   echo 	3.firmware(only rename) 		
   echo ======================================================
   set /p num=Please input mode(num): 
   
   if %num%==1 goto :do1
   if %num%==2 goto :do2
   if %num%==3 goto :do3
   
   :do1
   set name=arom-jacana-download
   ::echo SetPc 0x1E0000 >> .\a.txt
   goto :end
   
   :do2
   set name=arom-jacana-normal
   goto :end
   
   :do3
   set name=firmware-base-0x100000
   copy .\%name%.bin .\arom-jacana.bin
   echo next to modify setpc and load add
   timeout /t 6
   exit
   
   :end
   copy .\%name%.bin .\arom-jacana.bin
   timeout /t 2
   call run_riscv.bat
   
   
   ```

4. shell 中的符号

   ```shell
   
   1、$#：表示执行脚本传入参数的个数
   
   2、$*：表示执行脚本传入参数的列表（不包括$0）
   
   3、$$：表示进程的id；Shell本身的PID（ProcessID，即脚本运行的当前 进程ID号）
   
   4、$!：Shell最后运行的后台Process的PID(后台运行的最后一个进程的 进程ID号)
   
   5、$@：表示获取执行脚本传入的所有参数
   
   6、$0：表示执行的脚本名称
   
   7、$1：表示第一个参数
   
   8、$2：表示第二个参数
   
   9、$?：表示脚本执行的状态，0表示正常，其他表示错误
   
   
   ```

5. 

