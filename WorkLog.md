The Internet for server :
```html
https://sh2-cis01.asrmicro.com/guacamole/#/client/MjUAYwBwb3N0Z3Jlc3Fs
https://sh2-cis01.asrmicro.com/jenkins/view/gerrit/
```
[jenkins](https://sh2-cis01.asrmicro.com/jenkins/view/gerrit)  
[server](https://sh2-cis01.asrmicro.com/guacamole)

### 7.20

> 1. About Burn：Use  Aboot, click Release, choose correspond file, click download.  
> 2. How to know burn successsful? Add flag in log.  
> 3. Map network dirve. Click network, find ip in service.

---
### 7.21
1. burn craneG:
   -  Use the compiled code in gerrrit, for the code in ubuntu cannot download in PC.
   -  Run sscom.exe and press RESET buttton, then you can see the version.Replace the old file with the new file in version folder.  
   -  Run Aboot.exe and click Release dashboard, choose the correspond chip, click Release button. After release finished, click the Download button. Specially, press the RESET button and the DOWNLOAD button in DKB and the chip will enter burn program mode.
   -  Note: You can read the log output of sscom to check the code.  
   
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
### 7.22
1. STAR PROCESSOR  
   - LSR : logical shift right
   - ASR : arithmetic shift right
   - ROR : rotote right
   > Note : the difference between LSR and RSR is the sign bit. ASR  sign bit is contant, while LSR donot have sign bit, and its highest bit is 0.

2. Saturating Instruction. This instruction is to prevent the calculation results overflow.
3. Contiki-NG OS.
   
---
### 7.25
1. Learn concepts and advs. about Contiki OS, and details log in notebook.
2. Create hello-world project. The initial OS has example folder, but also has hello-world.c file. Just follow the tutorial.

<<<<<<< HEAD
-----
=======
---
### 7.26
1. Complie project in Ubuntu, generate .out file and run the file.
2. Learn difference between and gcc and make. The first, gun, used only for compling, but make inclues gcc command in makefile.
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
         struct Count *p_Count;  //struct Count donot emit.
      }*pC;  //define struct Count point *pC
      ```

6. Function Pointer
      ```c
      int (*p)(int, int ) //The later brackets are parameters. The * is return value.
      ```
                     

>>>>>>> b2094c0a84d8c168394c80b31d8710b06232ae99

### 7.26

Today did one thing: write a bug.















