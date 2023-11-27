# OverTheWire_Bandit练习

>SSH Information
>Host: bandit.labs.overthewire.org
>Port: 2220
>
>ssh bandit@bandit.labs.overthewire.org -p 2220

## 关于OverTheWire-Bandit

>Welcome to OverTheWire!      
>
>If you find any problems, please report them to the #wargames channel on                                                                    
>
>discord or IRC.                                                                                                                                                                                                                                                                   
>
>--[ Playing the games ]--                                                                                                                                                                                                                                                        
>
>  This machine might hold several wargames.                                                                                                 
>
>  If you are playing "somegame", then:                                                                                                                                                                                                                                            
>
>​    \* USERNAMES are somegame0, somegame1, ...                                                                                               
>
>​    \* Most LEVELS are stored in /somegame/.                                                                                                 
>
>​    \* PASSWORDS for each level are stored in /etc/somegame_pass/.         
>
>  **大多数级别存储在/somegame/中**。
>
>  **每个级别的密码存储在/etc/somegame_pass/中**。                                                                                                                                                                                                      
>
>  Write-access to homedirectories is disabled. It is advised to create a                                                                    
>
>  working directory with a hard-to-guess name in /tmp/.  You can use the                                                                    
>
>  command "mktemp -d" in order to generate a random and hard to guess                                                                       
>
>  directory in /tmp/.  Read-access to both /tmp/ is disabled and to /proc                                                                   
>
>  restricted so that users cannot snoop on eachother. Files and directories                                                                 
>
>  with easily guessable or short names will be periodically deleted! The /tmp                                                               
>
>  directory is regularly wiped.                                                                                                             
>
>  Please play nice:                                                                                                                                                                                                                                                              
>
>​    \* don't leave orphan processes running                                                                                                  
>
>​    \* don't leave exploit-files laying around                                                                                               
>
>​    \* don't annoy other players                                                                                                             
>
>​    \* don't post passwords or spoilers                                                                                                      
>
>​    \* again, DONT POST SPOILERS!                                                                                                            
>
>​      This includes writeups of your solution on your blog or website!                                                                                                                                                                                                         
>
>--[ Tips ]--                                                                                                                                                                                                                                                           
>
>  This machine has a 64bit processor and many security-features enabled                                                                     
>
>  by default, although ASLR has been switched off.  The following                                                                           
>
>  compiler flags might be interesting:                                                                                                                                                                                                                                    
>
>​    -m32                    compile for 32bit                                                                                               
>
>​    -fno-stack-protector    disable ProPolice                                                                                               
>
>​    -Wl,-z,norelro          disable relro                                                                                                                                                                                                                              
>
>  In addition, the execstack tool can be used to flag the stack as                                                                          
>
>  executable on ELF binaries.                                                                                                                                                                                                                                         
>
>  Finally, network-access is limited for most levels by a local                                                                             
>
>  firewall.                                                                                                                                                                                                                                                                     
>
>--[ Tools ]--                                                                                                                                                                                                                                                              
>
> For your convenience we have installed a few useful tools which you can find                                                               
>
> in the following locations:                                                                                                                                                                                                                                                    
>
>​    \* gef (https://github.com/hugsy/gef) in /opt/gef/                                                                                       
>
>​    \* pwndbg (https://github.com/pwndbg/pwndbg) in /opt/pwndbg/                                                                             
>
>​    \* peda (https://github.com/longld/peda.git) in /opt/peda/                                                                               
>
>​    \* gdbinit (https://github.com/gdbinit/Gdbinit) in /opt/gdbinit/                                                                         
>
>​    \* pwntools (https://github.com/Gallopsled/pwntools)                                                                                     
>
>​    \* radare2 (http://www.radare.org/)                                                                                                                                                                                                                                      
>
>--[ More information ]--                                                                                                                                                                                                                                                   
>
>  For more information regarding individual wargames, visit                                                                                 
>
>  http://www.overthewire.org/wargames/                                                                                                                                                                                                                            
>
>  For support, questions or comments, contact us on discord or IRC.                                                                                                                                                                                                           
>
>  Enjoy your stay!                                                                                                                                                                                                                                                           

# Bandit Level 0

## SSH

> ## Level Goal
>
> The goal of this level is for you to log into the game using SSH. The host to which you need to connect is`bandit.labs.overthewire.org`, on port 2220. The username is **`bandit0`** and the password is **`bandit0`**. Once logged in, go to the [Level 1](https://overthewire.org/wargames/bandit/bandit1.html) page to find out how to beat Level 1.
>
> [ssh](https://man7.org/linux/man-pages/man1/ssh.1.html)

- [Secure Shell (SSH) on Wikipedia](https://en.wikipedia.org/wiki/Secure_Shell)
- [How to use SSH on wikiHow](https://www.wikihow.com/Use-SSH)

![image-20231121145351802](https://gitee.com/zhengzhivon/images/raw/master/imgs/image-20231121145351802.png)

```shell
$ ssh <username>@<remote>
#将 <username> 替换为您在远程计算机上的用户名，并将 <remote> 替换为远程计算机或服务器的地址
#如果要指定端口，请添加-p 0000, （将 0000 替换为所需的端口号）。

ssh bandit0@bandit.labs.overthewire.org -p 2220

#-p port	Port to connect to on the remote host.  This can be specified on a per-host basis in the configuration file.
```

![image-20231121145959867](https://gitee.com/zhengzhivon/images/raw/master/imgs/image-20231121145959867.png)



# Bandit Level 0 → Level 1

> ## Level Goal
>
> The password for the next level is stored in a file called **readme** located in the home directory. Use this password to log into bandit1 using SSH. Whenever you find a password for a level, use SSH (on port 2220) to log into that level and continue the game.
>
> [ls](https://man7.org/linux/man-pages/man1/ls.1.html) , [cd](https://man7.org/linux/man-pages/man1/cd.1p.html) , [cat](https://man7.org/linux/man-pages/man1/cat.1.html) , [file](https://man7.org/linux/man-pages/man1/file.1.html) , [du](https://man7.org/linux/man-pages/man1/du.1.html) , [find](https://man7.org/linux/man-pages/man1/find.1.html)

```shell
#已经登陆了bandit0用户，在登陆bandit1用户之前需要exit退出bandit0用户，然后重新使用ssh远程连接。
ssh -p 2220 bandit1@bandit.labs.overthewire.org
#关于切换用户su bandit1
bandit1@bandit:~$ su bandit0
Password: 
su: Authentication failure
#OverTheWire_Bandit可能禁用了切换用户权限

使用 su 命令切换用户时遇到 "Authentication failure" 错误：
#密码错误： 你输入的目标用户密码可能不正确。请确保输入的密码与目标用户的密码匹配。记住，在使用 su 命令时需要输入目标用户的密码，而不是当前用户的密码。
#用户权限限制： 可能当前用户没有权限切换到目标用户。某些系统设置可能禁止某些用户切换到特定的目标用户。在这种情况下，你可能需要使用其他的权限或者请求管理员权限。
#用户已被禁用： 目标用户的账户可能已被禁用或者被锁定，导致无法使用 su 命令切换到该账户。你可以检查一下目标用户账户是否处于锁定状态。
```

![image-20231121153751702](https://gitee.com/zhengzhivon/images/raw/master/imgs/image-20231121153751702.png)

## ls 命令

ls命令用于显示指定工作目录下之内容（列出指定目录所含之文件及子目录)，ls命令的输出信息可以进行彩色加亮显示，以区分不同类型的文件。

用法：ls [选项] [目录]

```shell
参数：
-a 显示所有文件及目录 (. 开头的隐藏文件也会列出)
-l 除文件名称外，也将文件型态、权限、拥有者、文件大小等资讯详细列出
-h 以容易理解的格式列出文件大小

ls -a
```

## cd 命令

`cd`命令用于切换当前工作目录。

```shell
#用法1：cd [目录]
cd user

#用法2：cd [绝对路径]
cd /root/file

#用法3： .代表当前目录，..代表上一级目录，cd ~用于切换至登录用户家目录。cd -用于回到上一个目录。
cd .
cd ..
cd ~
cd -
```

## cat 命令

`cat`命令用于打开文件查看文件内容。

```shell
#用法：cat [选项] [文件]
cat /etc/passwd

cat -v file #加入参数-v后再查看
-v：除了 LFD(换行) 和 TAB 之外所有控制符，用 ^ 和 M- 显示。

cat -n 可以显示行号
```

## du 命令

`du`命令可查看文件使用空间.

```shell
用法：
du [选项] [文件]
参数：
-h 以K，M，G为单位，提高信息的可读性。

du -h /etc/passwd
du -h ./-
```

![image-20231121155346930](https://gitee.com/zhengzhivon/images/raw/master/imgs/image-20231121155346930.png)

# Bandit Level 1 → Level 2

> ## Level Goal
>
> The password for the next level is stored in a file called **-** located in the home directory.
>
> [ls](https://man7.org/linux/man-pages/man1/ls.1.html) , [cd](https://man7.org/linux/man-pages/man1/cd.1p.html) , [cat](https://man7.org/linux/man-pages/man1/cat.1.html) , [file](https://man7.org/linux/man-pages/man1/file.1.html) , [du](https://man7.org/linux/man-pages/man1/du.1.html) , [find](https://man7.org/linux/man-pages/man1/find.1.html)

- [Google Search for “dashed filename”](https://www.google.com/search?q=dashed+filename)
- [Advanced Bash-scripting Guide - Chapter 3 - Special Characters](http://tldp.org/LDP/abs/html/special-chars.html)

```shell
#‘-’这个名字跟root目录名是一样的，所以必须使用相对路径来访问
cat ./-
```

![image-20231121162103620](https://gitee.com/zhengzhivon/images/raw/master/imgs/image-20231121162103620.png)

## 关于特殊字符-命名的访问

在 Linux 中，当文件名以连字符（减号）或其他特殊字符开头时，有时可能会导致一些命令误解文件名为选项或参数。为了读取以连字符开头的文件名的内容，可以使用以下方法之一：

1. **使用相对或绝对路径：** 如果文件位于当前目录，可以使用相对路径或绝对路径来读取文件内容。例如：

   ```shell
   cat ./-filename
   ```

   或者

   ```
   cat /path/to/directory/-filename
   ```

2. **使用 `--` 表示结束选项：** 在某些命令中，使用 `--` 可以表示选项结束，之后的内容将被视为参数。例如：

   ```shell
   cat -- -filename
   ```

   这种方法告诉 `cat` 命令 `-filename` 不是一个选项，而是文件名。

3. **使用相对路径和 `./`：** 有时在文件名前加上 `./` 可以帮助命令正确解析文件名。例如：

   ```shell
   cat ./-filename
   ```

4. 还可以使用 < 运算符将其**重定向到标准输入**。

   ```shell
   cat < -
   ```

## 其他特殊字符

1. **文件名以特殊字符开头：** 如果文件名以其他特殊字符开头，比如 `*`、`!`、`#` 等，这些字符在命令行中通常有特殊含义，需要用类似的方式处理。

   ```shell
   cat ./#filename
   ```

   或者

   ```shell
   cat -- #filename
   ```

2. **文件名包含空格或特殊字符：** 如果文件名包含空格或其他特殊字符，可以使用引号或转义字符来正确处理。例如：

   ```shell
   #双引号单引号都可以
   cat "file name.txt"
   cat ’file name.txt‘
   ```

   或者

   ```shell
   cat file\ name.txt
   ```

   ```shell
   #每一个空格之前需要添加转义字符\
   bandit2@bandit:~$ ls
   spaces in this filename
   bandit2@bandit:~$ cat spaces\ in\ this\ filename
   aBZ0W5EmUfAf7kHTQeOwd8bauFJ2lAiG
   ```

3. **文件名包含通配符：** 如果文件名包含通配符（比如 `*` 或 `?`），为了防止它们被扩展，也可以使用引号或转义字符来处理。例如：

   ```shell
   cat "*.txt"
   ```

   或者

   ```shell
   cat \*.txt
   ```

处理这些情况的方法通常是确保命令解释器正确解释文件名，而不会将其误认为是选项或特殊字符。可以使用引号、转义字符或 `--` 来帮助命令解释器正确识别文件名。

# Bandit Level 2 → Level 3

>## Level Goal
>
>The password for the next level is stored in a file called **spaces in this filename** located in the home directory.
>
>[ls](https://man7.org/linux/man-pages/man1/ls.1.html) , [cd](https://man7.org/linux/man-pages/man1/cd.1p.html) , [cat](https://man7.org/linux/man-pages/man1/cat.1.html) , [file](https://man7.org/linux/man-pages/man1/file.1.html) , [du](https://man7.org/linux/man-pages/man1/du.1.html) , [find](https://man7.org/linux/man-pages/man1/find.1.html)

- [Google Search for “spaces in filename”](https://www.google.com/search?q=spaces+in+filename)

```shell
# 如果文件名包含空格或其他特殊字符，可以使用引号或转义字符来处理
cat spaces\ in\ this\ filename
or
cat "spaces in this filename"
or
cat 'spaces in this filename'

#3 aBZ0W5EmUfAf7kHTQeOwd8bauFJ2lAiG
```

![image-20231121162837118](https://gitee.com/zhengzhivon/images/raw/master/imgs/image-20231121162837118.png)

# Bandit Level 3 → Level 4

> ## Level Goal
>
> The password for the next level is stored in a hidden file in the **inhere** directory.
>
> [ls](https://man7.org/linux/man-pages/man1/ls.1.html) , [cd](https://man7.org/linux/man-pages/man1/cd.1p.html) , [cat](https://man7.org/linux/man-pages/man1/cat.1.html) , [file](https://man7.org/linux/man-pages/man1/file.1.html) , [du](https://man7.org/linux/man-pages/man1/du.1.html) , [find](https://man7.org/linux/man-pages/man1/find.1.html)

```shell
ls -a	#-a 选项显示所有文件，包括隐藏文件，但不以长格式显示。
la -l	#-l 选项以长格式显示文件和目录的详细信息，包括文件的权限、所有者、所属组、文件大小、创建时间等。

la -al	#结合-a和-l

#4 2EW7BBsr6aMMoJ2HjW067dm8EgX26xNe
```

![image-20231122140726114](https://gitee.com/zhengzhivon/images/raw/master/imgs/image-20231122140726114.png)

# Bandit Level 4 → Level 5

>## Level Goal
>
>The password for the next level is stored in the only human-readable file in the **inhere** directory. Tip: if your terminal is messed up, try the “reset” command.
>
>[ls](https://man7.org/linux/man-pages/man1/ls.1.html) , [cd](https://man7.org/linux/man-pages/man1/cd.1p.html) , [cat](https://man7.org/linux/man-pages/man1/cat.1.html) , [file](https://man7.org/linux/man-pages/man1/file.1.html) , [du](https://man7.org/linux/man-pages/man1/du.1.html) , [find](https://man7.org/linux/man-pages/man1/find.1.html)

```shell
#显示当前目录中所有文件的类型信息。它会对当前目录下的每个文件执行 file 命令，并显示每个文件的类型信息。
file ./*
file ./-file07
```

![image-20231122142644288](https://gitee.com/zhengzhivon/images/raw/master/imgs/image-20231122142644288.png)

------

## file命令

> file命令是Linux中用于检测文件类型的命令，可以根据文件的二进制数据来确定其类型。特别是当你需要确定某个文件是文本文件还是二进制文件时。

```shell
 语法：file  (选项)  (参数)
```

![image-20231122142015619](https://gitee.com/zhengzhivon/images/raw/master/imgs/image-20231122142015619.png)

## 一些返回值类型

1. **ASCII text**：纯文本文件，其中包含 ASCII 字符。
2. **UTF-8 Unicode text**：使用 UTF-8 编码的 Unicode 文本文件。
3. **ELF xxx-bit xxx-endian**：可执行和链接格式（Executable and Linkable Format）的二进制文件，通常是可执行文件或共享库。
4. **JPEG image data**：JPEG 图像文件。
5. **PNG image data**：PNG 图像文件。
6. **PDF document**：PDF 文档。
7. **HTML document**：HTML 文档。
8. **gzip compressed data**：经过 gzip 压缩的文件。
9. **directory**：目录。
10. **symbolic link to xxx**：符号链接，指向另一个文件或目录。

# Bandit Level 5 → Level 6

> ## Level Goal
>
> The password for the next level is stored in a file somewhere under the **inhere** directory and has all of the following properties:
>
> - human-readable
> - 1033 bytes in size
> - not executable
>
> [ls](https://man7.org/linux/man-pages/man1/ls.1.html) , [cd](https://man7.org/linux/man-pages/man1/cd.1p.html) , [cat](https://man7.org/linux/man-pages/man1/cat.1.html) , [file](https://man7.org/linux/man-pages/man1/file.1.html) , [du](https://man7.org/linux/man-pages/man1/du.1.html) , [find](https://man7.org/linux/man-pages/man1/find.1.html)

[find命令-菜鸟教程](https://www.runoob.com/linux/linux-comm-find.html)

[find命令](https://blog.csdn.net/KW__jiaoq/article/details/121319527?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522170063496116800182197554%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fblog.%2522%257D&request_id=170063496116800182197554&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~blog~first_rank_ecpm_v1~rank_v31_ecpm-1-121319527-null-null.nonecase&utm_term=find&spm=1018.2226.3001.4450)

```shell
find . -type f -size 1033c
#文件类型 普通 大小1033c
#6 P4L4vucdmLnm8I7Vl7jG1ApGSfjYKqJU
```

![image-20231122144146348](https://gitee.com/zhengzhivon/images/raw/master/imgs/image-20231122144146348.png)

## find命令

```shell
find [path...] [expression]

#path 是要查找的目录路径，可以是一个目录或文件名，也可以是多个路径，多个路径之间用空格分隔，如果未指定路径，则默认为当前目录。
#expression 是可选参数，用于指定查找的条件，可以是文件名、文件类型、文件大小等等。
```

### 参数

![image-20231122144538632](https://gitee.com/zhengzhivon/images/raw/master/imgs/image-20231122144538632.png)

![image-20231122144615635](https://gitee.com/zhengzhivon/images/raw/master/imgs/image-20231122144615635.png)

![image-20231122144645188](https://gitee.com/zhengzhivon/images/raw/master/imgs/image-20231122144645188.png)

### 常用选项

- `-name`：根据文件名查找文件。

- `-type`：根据文件类型查找文件（如文件、目录、符号链接等）。
- `-size`：根据文件大小查找文件。
- `-exec`：对匹配的文件执行指定的命令。

### 示例：

1. **按名称查找文件**：

   ```shell
   find /path/to/search -name "filename.txt"
   ```

   查找 `/path/to/search` 目录及其子目录下名为 `filename.txt` 的文件。

2. **按类型查找文件**：

   ```shell
   find /path/to/search -type f
   ```

   查找 `/path/to/search` 目录及其子目录下的所有文件。

3. **按大小查找文件**：

   ```shell
   find /path/to/search -size +1M
   ```

   查找 `/path/to/search` 目录及其子目录中**大小超过 1MB** 的文件。

4. **组合条件查找文件**：

   ```shell
   find /path/to/search -type f -name "*.txt" -exec grep "keyword" {} \;
   ```

   在 `/path/to/search` 目录及其子目录中查找所有扩展名为 `.txt` 的文本文件，并在这些文件中搜索包含关键词 `keyword` 的内容。

5. **查找空文件或空目录**：

   ```shell
   find /path/to/search -empty
   ```

   查找 `/path/to/search` 目录及其子目录中的空文件或空目录。

6. **查找 /var/log 目录下在 7 天前修改过的文件**：

   ```shell
   find /var/log -mtime +7
   ```

7. **将当前目录及其子目录下所有最近 20 天前更新过的文件列出，不多不少正好 20 天前的**:

   ```shell
   find . -ctime  20
   ```

8. **将当前目录及其子目录下所有 20 天前及更早更新过的文件列出**:

   ```shell
   find . -ctime  +20
   ```

9. **将当前目录及其子目录下所有最近 20 天内更新过的文件列出**:

   ```shell
   find . -ctime  20
   ```

10. **查找 /var/log 目录中更改时间在 7 日以前的普通文件，并在删除之前询问它们**：

   ```shell
find /var/log -type f -mtime +7 -ok rm {} \;
   ```

11. **查找当前目录中文件属主具有读、写权限，并且文件所属组的用户和其他用户具有读权限的文件**：

   ```shell
find . -type f -perm 644 -exec ls -l {} \;
   ```

12. **查找系统中所有文件长度为 0 的普通文件，并列出它们的完整路径**：

   ```shell
find / -type f -size 0 -exec ls -l {} \;
   ```

# Bandit Level 6 → Level 7

> ## Level Goal
>
> The password for the next level is stored **somewhere on the server** and has all of the following properties:
>
> - owned by user bandit7
> - owned by group bandit6
> - 33 bytes in size
>
> [ls](https://man7.org/linux/man-pages/man1/ls.1.html) , [cd](https://man7.org/linux/man-pages/man1/cd.1p.html) , [cat](https://man7.org/linux/man-pages/man1/cat.1.html) , [file](https://man7.org/linux/man-pages/man1/file.1.html) , [du](https://man7.org/linux/man-pages/man1/du.1.html) , [find](https://man7.org/linux/man-pages/man1/find.1.html) , [grep](https://man7.org/linux/man-pages/man1/grep.1.html)

```shell
#bandit7的密码文件有3个属性：被用户bandit7所有，被用户组bandit6所有，并且拥有33字节.
find / -user bandit7 -group bandit6 -size 33c

#7 z7WtoNQU2XfjmMtWA8u5rN4vzqu4v99S
```

![image-20231122150449236](https://gitee.com/zhengzhivon/images/raw/master/imgs/image-20231122150449236.png)

# Bandit Level 7 → Level 8

> ## Level Goal
>
> The password for the next level is stored in the file **data.txt** next to the word **millionth**
>
> [man](https://man7.org/linux/man-pages/man1/man.1.html), grep, sort, uniq, strings, base64, tr, tar, gzip, bzip2, xxd

[grep-菜鸟教程](https://www.runoob.com/linux/linux-comm-grep.html)

```shell
#下一个级别的密码存储在文件data.txt中，紧挨着单词"millionth"后边。
cat data.txt |grep millionth

#8 TESKZC0XvTetK0S9xNwm25STk5iWrBvP
```

![image-20231122153045246](C:\Users\VoN\AppData\Roaming\Typora\typora-user-images\image-20231122153045246.png)

## |管道

> `|` 符号代表管道（pipe），用于将一个命令的输出传递给另一个命令进行处理。这允许你通过将多个命令串联起来来实现更复杂的操作。

```shell
command1 | command2
#上一条命令的输出，作为下一条命令参数。Linux所提供的管道符“|”将两个命令隔开，管道符左边命令的输出就会作为管道符右边命令的输入。连续使用管道意味着第一个命令的输出会作为 第二个命令的输入，第二个命令的输出又会作为第三个命令的输入，依此类推

cat /etc/passwd | grep /bin/bash | wc -l
#这条命令使用了两个管道，利用第一个管道将cat命令（显示passwd文件的内容）的输出送给grep命令，grep命令找出含有“/bin /bash”的所有行；第二个管道将grep的输出送给wc命令，wc命令统计出输入中的行数。这个命令的功能在于找出系统中有多少个用户使用bash
```

![image-20231122153526180](https://gitee.com/zhengzhivon/images/raw/master/imgs/image-20231122153526180.png)

### 一些示例

1. **筛选数据**：

   ```shell
   ls -l | grep ".txt"
   ```

   这个命令首先列出当前目录中的文件，然后将 `ls -l` 命令的输出通过管道 `|` 传递给 `grep` 命令。`grep ".txt"` 将会筛选包含 `.txt` 的行，并仅显示这些行，过滤出文件名中包含 `.txt` 的文件。

2. **查找特定进程**：

   ```shell
   ps aux | grep "nginx"
   ```

   这个命令通过 `ps aux` 显示当前系统中所有的进程，并将这些输出通过管道传递给 `grep "nginx"` 命令。`grep "nginx"` 会在输出中搜索包含 "nginx" 字符串的行，筛选出关于 nginx 进程的信息。

3. **计算文件行数**：

   ```shell
   cat filename.txt | wc -l
   ```

   这个命令将 `filename.txt` 文件的内容通过 `cat` 命令读取，并将其输出通过管道传递给 `wc -l` 命令，`wc -l` 用于统计输入的行数。因此，这个命令将显示 `filename.txt` 文件中的行数。

4. **统计文件中某个词出现的次数**：

   ```shell
   cat filename.txt | grep "word" | wc -l
   ```

   这个命令首先读取 `filename.txt` 文件的内容，然后将其中包含 "word" 的行筛选出来，最后通过 `wc -l` 统计包含 "word" 的行数，从而得到 "word" 在文件中出现的次数。

## grep命令

> **grep** (global regular expression) 命令用于查找文件里符合条件的字符串或正则表达式。

grep 指令用于查找内容包含指定的范本样式的文件，如果发现某文件的内容符合所指定的范本样式，预设 grep 指令会把含有范本样式的那一列显示出来。若不指定任何文件名称，或是所给予的文件名为 **-**，则 grep 指令会从标准输入设备读取数据。

语法：

```shell
grep [options] pattern [files]
或
grep [-abcEFGhHilLnqrsvVwxy][-A<显示行数>][-B<显示列数>][-C<显示列数>][-d<进行动作>][-e<范本样式>][-f<范本文件>][--help][范本样式][文件或目录...]

#pattern - 表示要查找的字符串或正则表达式。
#files - 表示要查找的文件名，可以同时查找多个文件，如果省略 files 参数，则默认从标准输入中读取数据。
```

### 用法参数

1. **命令格式**：

   ```
   grep [options] pattern [file...]
   ```

2. **常用选项**：

   - `-i`：忽略大小写进行匹配。
   - `-v`：反向查找，只打印不匹配的行。
   - `-n`：显示匹配行的行号。
   - `-r`：递归查找子目录中的文件。
   - `-l`：只打印匹配的文件名。
   - `-c`：只打印匹配的行数。

   ![image-20231122171837843](https://gitee.com/zhengzhivon/images/raw/master/imgs/image-20231122171837843.png)

### 示例：

1. **搜索单个文件**：

   ```shell
   grep "pattern" filename.txt
   ```

   在 `filename.txt` 文件中搜索匹配 `pattern` 的行。

2. **忽略大小写进行搜索**：

   ```shell
   grep -i "pattern" filename.txt
   ```

   在 `filename.txt` 文件中忽略大小写地搜索匹配 `pattern` 的行。

3. **递归搜索目录**：

   ```shell
   grep -r "pattern" /path/to/directory
   ```

   递归搜索 `/path/to/directory` 及其子目录中匹配 `pattern` 的行。

4. **显示匹配行的行号**：

   ```shell
   grep -n "pattern" filename.txt
   ```

   在 `filename.txt` 文件中搜索匹配 `pattern` 的行，并显示行号。

5. **反转匹配**：

   ```shell
   grep -v "pattern" filename.txt
   ```

   在 `filename.txt` 文件中查找未匹配 `pattern` 的行。

6. **使用正则表达式**：

   ```shell
   grep -E "pattern1|pattern2" filename.txt
   ```

   在 `filename.txt` 文件中使用正则表达式搜索匹配 `pattern1` 或 `pattern2` 的行。

7. **查找匹配内容所在的文件名**：

   ```shell
   grep -l "pattern" /path/to/directory/*.txt
   ```

   在 `/path/to/directory` 目录下的 `.txt` 文件中查找匹配 `pattern` 的内容，并显示匹配内容所在的文件名。

`grep` 命令提供了灵活的文本搜索功能，可以根据需要使用不同的选项来满足特定的搜索需求。它也支持正则表达式，允许更复杂的模式匹配和搜索。