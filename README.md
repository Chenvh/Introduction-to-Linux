---
title: Linux入门（更新中）
date: 2021-05-03 14:40:18
description: Linux快速入门
categories: Linux
tags:  
		- Linux
top_img: /img/linux_1.jpg
cover: /img/linux_1.jpg
---

[更新到](#用户身份的切换)

# Linux概述

## 前言
这篇文章目的是帮你快速入门使用Linux，不可能面面俱到，很多内容都是省略的。我们要对Linux操作系统建立起一个整体框架，了解最基础的知识点和掌握最常用的命令，然后在使用Linux中学习，给自己建立出来的框架添加 *亿点* 细节。文章的内容，是根据我在日常使用Linux中，总结出来的最常用的操作，或者是最基础的知识点。可能其他熟悉Linux的人会觉得还需要加其他的内容。（文章还在更新中）

## Linux简介

一般我们说的Linux系统，指的是**Linux内核**，最初的的Linux内核是由林纳斯·托瓦丝（Linus Torvalds）编写出来的，是一个开源的免费的类Unix操作系统，意思就是可以白嫖的操作系统，目前(2021.7.14)最新的Linux内核版本为5.13.1。

* Linux 吉祥物
![](https://ae01.alicdn.com/kf/U9b7a7764e972436dbe5c779a60b50cafs.jpg)

### 什么是Linux发行版
* Linux发行版是由Linux内核、GNU工具、软件包管理器等等组成的操作系统。简单来说就是：Linux内核　+　应用软件组成的操作系统。
* Linux发行版数量无数，但是目前都是基于Debain、Slackware、RedHat、Fedora、Enoch、Arch以及Android。
* 下面是简单的Linux各大系 ![](https://ae01.alicdn.com/kf/U12b33021018848bab63925da0e65c082P.jpg)
* 具体有哪些发行版的可以去这里*https://github.com/FabioLolix/LinuxTimeline/tags*了解
### Linux一些特点
* 开源：Linux内核是开源的，你可以下载源码学习，或者自己修改
* 命令行使用方便
* 应用领域：服务器操作系统
* Linux一切皆为文件

## 安装Linux操作系统
* 可以根据自己的喜好选择Linux发行版、也可以根据特定的需求选择Linux发行版，下载镜像文件
* 选择再虚拟机上安装还是实体机安装，实体机安装要制作启动盘，安装过程虚拟机和实体机差不多。
* 安装过程可以根据需要选择自己分盘，也可以整盘安装，安装程序自动分配。
* 具体网上随便搜就有

## 一些关于Linux的网站

### Linux学习
* 菜鸟教程：*www.runoob.com/linux/linux-tutorial.html*
* 鸟哥的私房菜：*www.linux.vbird.org/linux_basic/*
* Linux内核：*www.kernel.org*
### 工具网站
* 命令行搜索：*https://wangchujiang.com/linux-command/*

----------------------------

# Linux的灵魂：命令行


## 命令的一般格式

* **`command -[选项] [参数] `**
* **`command [参数]`**
* 一些命令选项可以多个，参数也可以多个
* 例如：
    * 单列显示当前目录所有文件和文件夹  **`ls -al`** 
        * 选项 **-a** 是显示全部
        * 选项 **-l**  是单列输出
        * **ls**  的选项不只这些可以通过 -h 选项快速查询，也可以 通过 man 查询
    * 删除当前目录下的文件夹 **`rm -r [目标文件夹]`**
        * -r 或 -R  递归处理，将指定目录下的所有文件与子目录一并处理

## 命令的补全 Tab 键

补全是个好东西，有一些命令比较长，懒得敲完或者是忘了全拼，只记得开头几个字母，可以通过 *TAB* 键补全。也可以补全路径，路径最好用补全，既方便又不会出错。值得注意的是，补全功能，并不是所有的黑乎乎的命令行界面都有的功能，具体后面讲到 **shell** 的时候会解释。

**可补全的：**

* 可以补全命令、选项、和参数
* 补全有多个匹配值时，双击TAB可以查看可补全的命令、选项或者参数
* 善于利用补全可以提高工作效率

## 命令的别名

在 bash（后面解释） 中可以用 alias 来给指令创建别的名字，可以加上参数。
* **`alias ll='ls -al'`**
* 但是这个别名只在当前的bash 中有效，所以可以把这条语句写进当前用户的 bash 配置文件中，使别名永久有效

## 常用的指令
| 指令  |              指令的作用              |
| :---: | :----------------------------------: |
|  ls   |    显示当前文件夹中的文件、文件夹    |
|  cp   |               拷贝文件               |
|  mv   |          移动文件或者文件夹          |
|  rm   |       用于删除给定的文件和目录       |
|  cd   |         切换用户当前工作目录         |
|  su   |  用于切换当前用户身份到其他用户身份  |
| sudo  |   以其他身份来执行命令，预设为root   |
| echo  |       输出指定的字符串或者变量       |
| grep  | 强大的文本搜索工具，常与管道配合使用 |
| wget  |        Linux系统下载文件工具         |
|  man  |        查看Linux中的指令帮助         |
| mkdir |            创建文件夹命令            |

## 如何学习、记忆命令
我们没必要记住所有的命令以及指令的选项，只需要记住常用的指令。基本上用多了就记住了，所以学习Linux就是多动手，多实践。忘了指令或者指令选项可以用man来快速查看指令的选项，或者搜索。

----------------------

# 认识和学习Shell
## Vim编辑器

学Shell之前先介绍一下Linux命令行下的文本编辑软件。Linux下的编辑器有很多，比如Nano、Emacs、Pico等。完全可以根据自己的喜好学习，喜欢用哪个就用哪个，**Vim** 是现在大多数Linux发行版自带的一个文本编辑。

### vi/vim的操作模式（重点）
* 一般命令模式，默认的模式，可以进行很多操作，比如，行复制、多行删除、跳转、查找、撤销和重做等等。

* 编辑模式，顾名思义就是直接编辑文本文件，按 a、i、o 键进入，按ESC退出到一般命令模式，**在命令模式下输入`：`（英文冒号），再输入指令**

  **指令：**

* **保存退出：`:wq`**

* **放弃更改退出：`:q!`**

* **未更改退出：`:q`**
### vim的使用
直接用：`vim [文件名]`进行编辑。

## 认识和学习bash
### 什么是Shell
首先 shell 翻译成中文是”壳“；它是相对于Linux内核来说的，因为shell建立在Linux内核的基础上，面向用户的命令接口。意思就是我们可以通过Shell跟Linux内核打交道，你通过shell告诉内核做什么，它给你反馈运行信息。所以shell只是一个统称，不具指某一个东西。

### 认识bash
bash就是shell的一种，绝大部分Linux发行版默认用的都是bash。
**Bash Shell 的功能：**

* 历史命令（history）
    * 记录你使用过的命令，记录的条数可以自己设置，默认是1000个。
* 命令和文件的补全功能
* 命令别名的设置
* 任务管理、前台、后台任务控制
* 程序化脚本：也就是Shell脚本，可以做很多事情，可以直观理解成，一次执行多条命令，但不仅限于此
* 通配符
### shell的变量
#### 简单说明
学过C 或者其他编程语言都知道变量这个东西，shell可以使用变量，一般在shell 脚本中使用的比较多。可以在学Shell脚本的时候在学习。

#### 环境变量
* PATH 变量：这个变量里包含很多路径，这些路径一般是某些软件的可执行文件的路径，后面在讲解。
* 还有各种环境变量

### bash的环境配置

就像对bash进行设置一样，根据自己的习惯定制自己的bash，提高工作效率。**设置**自己的bash就要改bash的配置文件。

#### 配置文件
* /etc/profile 这是全部用户的配置文件，不熟悉的情况下最好不要改这个，改v
* bash  的配置文件是家目录下的 `.bashrc` 和 `.profile`，改哪个都可以，但是一般只改 **.bashrc**
#### 可以配置什么
* 命令别名
* 环境变量，如PATH
* 配置文件的修改，会在使用中慢慢熟悉

### bash 的一些快捷键

**善用快捷键，提高工作效率**，下面的都是最常用的快捷键

#### 控制
* **Ctrl + l**：清屏（与clear命令效果相同）
* **Ctrl + c**：终止当前正在执行的命令
* **Ctrl + z**：挂起命令，把当前进程转到后台运行，使用fg命令恢复
* Ctrl + s：阻止屏幕输出(当前正在执行的命令不在打印信息)
* Ctrl + q：允许屏幕输出(使用Ctrl+s命令后，可以用Ctrl+q恢复)
* Ctrl + d : 退出当前 Shell ^S、^Q、^C、^Z 是由终端设备处理的，可用 stty 命令设置。


####  编辑命令

##### 光标移动
* Ctrl + a ：移到命令行首
* Ctrl + e ：移到命令行尾
* Alt + f ：前移（向右移动）一个单词
* Alt + b ：后退（向左移动）一个单词

##### 命令修改
* Ctrl + u ：从光标处删除至命令行首
* Ctrl + k ：从光标处删除至命令行尾
* Ctrl + w ：从光标处删除至字首
* Alt + d ：从光标处删除至字尾
* Ctrl + d ：删除光标处（或光标后）的字符（如果光标前后都没有字符，即命令行为空的时候，则会退出shell）

#### 重新执行命令
* 上下键选择执行过的命令



### 数据流重定向
#### 什么是数据流重定向
最直观的数据流：bash执行命令过程中输出到屏幕上的信息，数据流重定向就是，把命令运行输出信息，重新定向到指定的地方。

#### 具体操作
* 标准输入（stdin）：< 或  <<
* 标准输出（stdout）：> 或  >>
* 标准错误输出（stderr）：2> 或 2>>（程序运行可能回输出报错信息，这个会把报错的信息重新定向）
* 例如：将 `ls -al / ` 的输出重定向到某个文件，`ls -al / >> ./test`

### 多命令执行（指令的分隔方式；、&&、||）

为什么需要多命令执行？因为有时候你想执行完 *指令1* 然后 再执行 *指令2* 但是 *指令1* 有输出，而且可能命令执行时间比较长，需要等待，所以就会一次输入多个指令，分隔方式的不同，多条命令执行的情况也会不同。多命令执行在工作中经常用到。

##### 分隔方式

- **;（分号）**：`cmd1;  cmd2`  不虑命令相关性执行，也就是不管cmd1执行是否成功，都会执行cmd2

- **&&** ：`cmd1 && cmd2` 当cmd1 成功执行，才会执行cmd2

- **||** ：`cmd1 || cmd2 `  当cmd1成功执行，则不执行cmd2，假如cmd1执行不成功，那就执行cmd2

### 管道命令
#### 为什么要用管道命令
有一些命令执行的输出数据密密麻麻，堆满整个屏幕，很难筛选出有效的或者是自己需要的信息。这时候就要 **”管道加塞子“** 来筛选出自己想要的信息。

#### 直观理解管道
* 命令其实也可以算是数据重定向的一种，可以理解为将数据流重定向到管道中。而**管道命令**就相当于“筛子”、“过滤器”。最后通过管道出来的信息就是自己想要的信息。
* 管道命令使用【|】定界符号，就像一根管道，配合管道命令使用。
#### 选取命令：cut、grep
* cut 可以将一段信息的某一个部分切出来，以行为单位，也可以用awk命令
* grep 字符查找，也可以说是字符匹配，可以将信息中匹配的字符或者字符串筛选出来
    * 用法 cmd1 | grep "要匹配的字符(串)" ，也可以用单引号 '，单个匹配字符串可以不用引号
* 例子 查找当前目录下所有带 a 字母的文件或者文件夹 **`ls -l | grep a`**



#### 排序命令
* sort
* wc
* uniq

#### shell 脚本

**什么是shell脚本：**

最简单的理解，就是把一堆命令写在脚本文件里，执行脚本文件就等于执行这一堆命令，但是shell脚本不仅限于只写一条条命令，它像其他编程语言一样，有变量，有循环、条件等语句。 shell脚本可以作为独立分支去学习，严格来说是一种编程语言。**shell脚本文件名后缀一般是`.sh`，如果要执行当前目录下的脚本文件，要加上 `./` （既：./脚本文件名.sh）才能执行。**（`./`是当前目录的意思，后面讲到，*[传送门](#绝对路径和相对路径)*）

### 命令的本质
**一般来说，shell命令分为两种，一种是内置的命令，一种是外部命令。**

* 内置命令
    shell自带的命令叫做shell的内置命令，在内部是通过函数来实现的。当启动shell之后，这些命令所对应的函数代码就会被加载到内存中，因为这些命令是被直接加载到内存中，所以shell的内置命令在运行的时候是非常快的。比如说 `ls` 命令就是内置命令。
* 外部命令
    执行外部命令就是执行相应的程序。一般在Linux中，执行外部命令的时候，不会去所有的目录一个一个的查找是否有对应的应用程序，而只会在**PATH环境变量**的路径下查找是否有相应的应用程序，如果有的话就运行，没有的话就返回错误的信息给用户。比如说我们使用 **vim编辑器**编辑文本文件，`vim`就是外部命令

（[原文链接](https://blog.csdn.net/bendanfly/article/details/100256826)）

-------------

# 文件目录

## Linux的用户与用户组
* 这里只是简单的介绍Linux的用户与用户组，为了方便讲Linux的文件和目录，因为Linux操作系统对权限的管理特别的严格，每个文件都有自己的拥有者，你没有一个文件的权限，你就不能对这个文件操作。而且管理非常简单，并不会像 windows 那样非常的混乱。

* **用户：**就是在Linux主机上创建的用户，这不难理解。

* **用户组：**其实就是把一群用户扎堆放，一个用户可以在多个用户组中

* **其他人的概念（抽象）：**用图解释

![](https://ftp.bmp.ovh/imgs/2021/07/85c5d1f7236ff082.jpg)

## 用户的家目录
每个用户都可以有一个家目录，对应的shell环境变量是  **＄HOME**，家目录在 `/home` 下，一般以用户的形势命名。一般工作都是在自己的家目录下进行的，但是并不是每个用户都有家目录，一是因为新增用户的时候可能没有创建家目录，二是因为有时候新增的用户不需要家目录，只是需要用来实现某种工作而新增的用户。

## Linux文件权限的概念

### Linux的文件属性

一定要弄清文件的属性，这是我们和Linux操作系统打交道最最最多的地方，因为**”Linux下一切皆为文件“**，我们一定要搞懂文件的属性。

![](https://ae01.alicdn.com/kf/U358c063b313145b190d249b9881db23aF.jpg)

#### 第一栏
第一 栏代表这个文件的**类型**与**权限( permission )**

**类型：**
- 第一个字符代表这个文件是目录、文件或链接文件等
- 当为 `[d]` 则是目录，例如上表文件名为`anconda`的那 行（重点）
- 当为 `[-]` 则是文件， 例如上表文件名为`bashrc`那一行（重点）
- 若是 `[1]` 则表示为链接文件( link file )
- 若是 `[b]` 则表示为设备文件里面的可供存储的周边设备（可按块随机读写的设备）
- 若是 `[c]` 则表示为设 备文件里面的串行端口设备，例如键盘、鼠标(一次性读取设备)

**权限( permission )：**
接下来的字符中，以三个为一组，且均为`{r,w,x}`的三个参数的组合比如[rwx]、[rw-]。(重重重点)
- `[r]`代表可读 **( read ) **
- `[w]`代表可写 **( write )**
- `[x]`代表可执行 **( execute )**
- 要注意的是这三个权限的**位置不会改变**，如果没有权限，就会出现减号`[-]`而已
- 第一组为**文件拥有者**可具备的权限，以`[db.py]`这个文件为例，该文件的拥 有者可以读写，但不可执行;
- 第二组为加入此**用户组**之账号的权限
- 第三组为非本人 且没有加入本用户组的**其他用户**的权限

#### 二到七栏
- 第二栏表示有多少文件连结到此节点
- 第三栏表示这个文件(或目录)的**『拥有者帐号』**
- 第四栏表示这个文件的**所属群组**
- 第五栏为这个文件的容量大小，预设单位为bytes
- 第六栏为这个文件的建档日期或者是最近的修改日期
- 第七栏为这个文件的文件名
(PS：这部分内容由鸟哥的描述改编）
#### 扫盲
Linux的文件和Windows有非常大的区别，一定要区分清楚。Linux操作系统下，一个文件能不能**读和写**也就是，并不由这个 **文件本身的属性** 决定，而是由文件的**读写权限**决定，也就是说：一个文本文件，能不能**读取、修改**，还要看它有没有**读和写**的权限，而不是它是个文本文件就能读和写。同理，一个 **可执行文件** 能不能执行，还要看它有没有 **执行** 权限。文件夹也是一样的，文件夹能不能**读**（用`ls`列出文件夹内的文件或文件夹），看 `r` 权限，能不能进入到这个文件夹（cd） 要看 `x` 权限，能不能在文件夹内 修改文件、创建文件、创建文件夹等，要看 `w` 权限。 
## 如何修改文件的属性和权限
* `chgrp：`**修改文件所属的用户组**
* `chown：`**修改文件拥有者**
* `chmod：`**修改文件的权限，SUID、SGID、SBIT 等的特性**

### 修改所属用户组：chgrp
* 命令： chgrp   [-R]   gropName  dirname/filename 
* 解释：-R 选项是更改这个目录以及目录下的所有文件

### 修改所属用户：chown
* 命令： chom   [-R]  UserName(username:group)  dirname/filename 
* 解释：-R 选项是更改这个目录以及目录下的所有文件,如果要修改的目标是 `文件`，可以不用这个选项

### 修改权限：chmod

#### 整体修改
* Linux文件权限字母有对应的数字，也可以叫数字权限
* 读、写、执行的数字权限对照（重点）
    * **r：4**
    * **w：2**
    * **x：1**

* 每一种身份的权限都是这三个权限累加起来的，所以我们可以用数字权限的累加作为一种用户的权限，比如：
    * 某个文件的权限为 `-rw-rwxr--`，对应的数字权限就是674

* 命令：chmod  [-R]   guo  dirName/fileName 
    * 解释：-R 选项是更改这个目录以及目录下的所有文件
    * guo ：g 用户组数字权限，u 用户数字权限，o 其他人数字权限

#### 单个修改
我们也可以针对某一权限组进行修改，比如文件用户组权限的修改，文件用户权限的修改。

* 更改权限符号
    * +（加入）
    * -（除去）
    * = （设置）
* 权限组
    * u（user）：用户权限组
    * g（group）：用户组权限组
    * o（other）：其他权限组
    * a（all）：所有组

* 用法：
    * 比如说我们修改用户的权限，给用户的权限加上可执行权限：chmod u+x fileName

## 文件的种类与扩展名

### Linux系统文件种类
#### 简述
其实Linux下文件的种类不像Windows下的那么多，那么复杂，常见的文件类型也就几种。

####  文件种类
* 常规文件
    * 存文本文件：最常见的就是我们敲的代码，不管是C/C++ 还是Python
    * 二进制文件：里面就0和1
    * 数据文件：一般是某种程序执行时读取的文件

* 目录
* 链接文件
- 设备与设备文件
    - 区块设备文件
    - 字符设备文件

- 数据接口文件（socket）
- 数据传送文件（FIFO，pipe）

### 文件的扩展名
#### 概述
Linux文件名的后缀，并不决定这个文件的文件类型，它只起到辅助作用，告诉你这个是什么类型的文件。比如说一个shell 脚本文件，文件名一般为：filename.sh ，但是不管有没有 `.sh` 它都是一个脚本文件，把`.sh` 删掉都可以，只不过如果没有这个后缀，你可能不知道它是个脚本文件。同样的，**一个可执行文件能不能被执行，看的不是扩展名，看的是有没有执行权限，跟文件扩展名一点关系都没有，有没有都可以** 

#### 扩展名的用处
文件的扩展名不能决定文件是否能执行，那Linux还要扩展名干啥？其实最简单的一个原因就是，容易区分是什么文件，或者说容易区分是哪种文件，这个文件是个什么东西。

#### 常见的文件扩展名
* .py、.c、.cpp 这一类的文件名
* .sh：Linux下常见的，shell脚本的扩展名
* .Z、.tart、.tart.gz：压缩包

### 文件内容的查看和修改
* 查看：文本文件都可以用 **cat** 命令来查看，大部分文件都能用 cat ，只不过可能 显示出来的是一堆乱码。
* 修改：用文本编辑器修改，如：vim
* touch 命令：用来创建一个文件



## Linux目录配置
Linux根目录下有很多个文件夹，这些文件夹都有一定的自己用处

### Linux常见的目录

|  目录  |                             作用                             |
| :----: | :----------------------------------------------------------: |
|   /    |                      这个叫根(root)目录                      |
| /boot  |                   主要放系统启动相关的文件                   |
|  /dev  |    Linux所有的设备与接口设备，以文件的形式放在这个目录中     |
|  /etc  |     配置文件的目录，系统的配置文件，和一些软件的配置文件     |
|  /var  |                        和系统运行有关                        |
|  /usr  | 一般用来存放系统软件资源的，比如说/usr/bin下存放我们大部分用户能执行的命令 |
| /media |             一般用来挂载媒体文件，比如说挂载U盘              |
| /home  |                   家目录都在这个home目录下                   |

Ps：usr==> 是Unix software resource的缩写，而 不是 user 缩写

### Linux目录树
![](https://ae01.alicdn.com/kf/Uce111d8c51ed4d45a411435d85dc835eI.jpg)

(图片来自：[Linux 目录详解](https://cloud.tencent.com/developer/article/1678497?from=information.detail.linux目录树介绍))

### 打印当前目录指令
* pwd 可以打印当前工作目录

### 绝对路径和相对路径
* **绝对路径：**就是详细的路径，就比如说你家在 xxx省xxx市xxx街道xxx路xxx小区xxx栋xxx号。在Linux就是，从根目录（`/`）开始，一直到你的目标目录，比如说**用户abc**的家目录绝对路径：`/home/abc`
* **相对路径：**路径的相对位置，以当前目录为基准的路径，比如说我家旁边的哪哪哪。
* Linux**每个**目录下都会有两个特殊的目录
    * `./`：表示的是当前目录
    * `../`：表示上一级目录

### 文件、目录的默认权限和隐藏权限

这部分如果没兴趣，可以不用了解，只需要知道Linux下文件权限有这一部分的内容，具体内容，可以去查查资料，比如说鸟哥私房菜。

#### 文件默认权限：umask

#### 文件的特殊权限：SUID、SGID、SBIT

## Linux的文件系统和磁盘

### Linux的文件系统

#### 什么是文件系系统

这部分涉及到了计算机组成和操作系统的知识，任何的操作系统，都建立在自己的文件按系统上，Linux和Windows使用的文件系统不同。windows使用的文件系统是ntfs，但是并不是windows只能识别ntfs文件系统，还可以支持其他文件系统，比如说U盘常用的：FAT32、eFat。但是，windows不能支持Linux的文件系统（ext3、ext4），而Linux支持ntfs。比如说你在自己的电脑上安装了Windows+Linux双操作系统，但是windows不能访问Linux的文件，Linux能访问Windows的文件。

#### Linux的文件系统
* 现在常用的是：ext4（以前是ext3）
* 支持U盘的文件系统、和ntfs等

### 磁盘分区
#### 磁盘分区查看
* gdisk 设备名
* fdisk

#### 磁盘格式化

#### 内存交换分区
##### 什么是内存交换分区（swap）
内存交换分区是用来扩展内存的，当内存不够时使用。

### 什么是挂载点
**重点：**挂载点一定是目录，这个目录是进入文件系统的入口，并不是所有文件系统都能使用，只有挂载到目录树的某个目录后，才能使用该文件系统。

### 如何挂载和解挂文件系统
**命令：mount 和 umount**
* mount  设备名 挂载点
    * 设备名一般在/dev下
    * 挂载点：目录
* umount 设备名

## 文件的压缩

### 常见的压缩文件

| 文件后缀 |              压缩文件种类              |
| :------: | :------------------------------------: |
|    .Z    |         compress程序压缩的文件         |
|   .zip   |           zip程序压缩的文件            |
|   .gz    |           gzip程序压缩的文件           |
|   .bz2   |          bzip2程序压缩的文件           |
|   .XZ    |            XZ程序压缩的文件            |
|  . tar   |    tar程序打包的文件，并没有压缩过     |
| .tar.gz  | tar程序打包的文件，并且经过gzip的压缩  |
| .tar.bz2 | tar程序打包的文件，并且经过bzip2的压缩 |



### 压缩、打包命令
gzip、bzip2、xz

#### 打包指令： tar
为什么要打包指令？gzip, bzip2, xz也能够针对目录来进行压缩，不过，这两个指令对目录的压缩指的是『将目录内的所有档案"分别"进行压缩』，而不是像windows下面的那样直接对目录就可以进行压缩。所以要想对文件夹压缩，首先要打包，再最打包好的单个打包文件进行压缩。

#### 打包常用指令
* 压缩：tar -j c v -f filename.tar.bz2 要被压缩的文件或目录名
* 查询：tar -j t v -f filename.tar.bz2
* 解压缩：tar -j x v -f filename.tar.bz2 -C 欲解压缩的目录

------

# Linux 使用者管理

## 用户账号与用户组
Linux的管理工作中，最重要部分之一就是管理账号，因为Linux是一个可多用户使用的操作系统，每个登入的使用者至少都会取得两个ID ，一个是使用者ID (User ID ，简称UID)、一个是群组ID (Group ID ，简称GID)。有的Linux发行版，添加新用户时不回自动创建家目录，而且默认的shell不是bash，所以在添加新用户的时候要注意。

### 用户账号的标识：UIG、GID
我们登入系统输入的是账号，但其实Linux并不认识你的账号名，只认识你的ID，ID和账号的对应在`/etc/passwd`中
* UID
![](https://ae01.alicdn.com/kf/Uc3cb780f03cd4647a2c69fc6ebe985e8i.jpg)
(图片来源：[鸟哥的网站](http://linux.vbird.org/linux_basic/0410accountmanager.php#account_id))
* GID：这个与/etc/group有关，只是他是用来规范群组名称与GID的对应而已


### 账号管理

#### 新增用户与删除用户：useradd

因为不同的Linux发行版新增用户的默认设置不一样，所以最好每次都要指定家目录和默认的shell。当然你还可以指定UID和GID（意思就是指定用户组），这个命令需要root权限，所以在非root登入既普通用户登入情况下，想新建有家目录的用户就用：

`sudo useradd -m userName  -s /bin/bash`

**部分其他参数说明：**

* -g 群组：指定用户所属的群组； 
* -G 群组：指定用户所属的附加群组； 
* -M：不要自动建立用户的登入目录；
* -n：取消建立以用户名称为名的群组；
* -u <uid>：指定用户id。

**用useradd 创建用户，系统会自动做部分工作：**

* etc/passwd 里面建立一行与帐号相关的资料，包括建立UID/GID/家目录等
* 在/etc/shadow 里面将此帐号的密码相关参数填入，但是尚未有密码
* 在/etc/group 里面加入一个与帐号名称一模一样的群组名称
* 在/home 底下建立一个与帐号同名的目录作为使用者家目录，且权限为700

#### 更改用户设置
**usermod [-cdegGlsuLU] username**
选项与参数：

* -g ：后面接初始群组，修改/etc/passwd 的第四个栏位，亦即是GID 的栏位
* -G ：后面接次要群组，修改这个使用者能够支援的群组，修改的是/etc/group
* -l ：后面接帐号名称。亦即是修改帐号名称， /etc/passwd 的第一栏！
* -s ：后面接Shell 的绝对路径，例如/bin/bash 或/bin/csh 等等。
* -u ：后面接UID ，即/etc/passwd 第三栏的资料；


#### 删除用户
**userdel [-r] username**

**选项**

* -r ：连同使用者的家目录也一起删除

#### 更改用户的密码

* 使用 `passwd username` 可以更改用户的密码
* root 账户可以改任何账户的密码，当然包括root账户本身的密码

## 用户身份的切换
Linux中经常切换用户，比如切换到root用户或者其他账户，又或者某些指令需要更高级的权限才能完成执行，也需要**暂时**的切换用户。**正常情况下尽量使用普通账户，不要随便使用root账户进行操作**，Linux中不建议经常使用**root**操作，最好都是在普通用户下操作。

### su 切换用户
su 是最简单的用户切换命令
*   su [-lm] [-c指令] [username]
    选项与参数：
    \- ：单纯使用- 如『 su - 』代表使用login-shell 的变数档案读取方式来登入系统， 若使用者名称没有加上去，则代表切换为root 的身份。
    -l ：与- 类似，但后面需要加欲切换的使用者帐号！也是login-shell 的方式。
    -m ：-m 与-p 是一样的，表示『使用目前的环境设定，而不读取新使用者的设定档』
    -c ：仅进行一次指令，所以-c 后面可以加上指令
*   接下来会输入密码，输入密码时不会显示任何字符，比如我们熟悉的 *    
### sudo
* sudo可以让你以其他用户的身份执行指令(通常是使用root的身份来执行指令)，和su不同的是sudo的执行则仅需要自己的密码
* sudo [-b] [-u新使用者帐号]
	* 选项与参数：
	* -b ：将后续的指令放到背景中让系统自行执行，而不与目前的shell 产生影响
	* -u ：后面可以接欲切换的使用者，若无此项则代表切换身份为root 。
* 一般我们使用的就是 sudo [cmd]：sudo 后面接命令，可以使用root的权限执行该命令。
* 我们这主要是讲sudo 最常用的用法。**sudo没有那么简单，能否使用sudo必须要看/etc/sudoers的设定值，而可使用sudo者是透过输入使用者自己的密码来执行后续的指令**，可自行了解。
* 你可以修改相应的配置文件，自定义sudo。

# 系统管理简单讲解
## 认识系统服务（service）
简单的说，就是系统为了某些功能必须要提供的一些服务，就像Windows那样，打开任务管理器就会看到很多系统服务。

## 通过systemctl管理服务
systemctl就是system加ctl，这样是不是很好记住这个命令，system（系统）+ ctl（control：控制）

### 查看系统所有的服务
* 列出系统上面有启动的unit ：直接systemctl

### 管理服务
* stemctl [command] [unit] 
    - command主要有：
    - start ：立刻启动后面接的unit
    - restart ：立刻关闭后启动后面接的unit，亦即执行stop 再start 的意思
    - reload ：不关闭后面接的unit 的情况下，重新载入设定档，让设定生效
    - enable ：设定下次开机时，后面接的unit 会被启动
    - disable ：设定下次开机时，后面接的unit 不会被启动
    - status ：目前后面接的这个unit 的状态，会列出有没有正在执行、开机预设执行否、登录等资讯等！
    - is-active ：目前有没有正在运作中
    - is-enabled：开机时有没有预设要启用这个unit

- 比如 查看某个服务的状态：systemctl status [unit]

## 任务、进程管理

### 什么是进程
在Linux系统当中：触发任何一个事件时，系统都会将他定义成为一个程序，并且给予这个程序一个ID ，称为PID，同时依据启发这个程序的使用者与相关属性关系，给予这个PID一组有效的权限设定。看不懂没关系，以后会学，就记住在系统跑的程序，都会有一个PID。

### Linux的多人多任务环境
* 多人环境：同时多人在线使用同一个Linux操作系统，每个人都有自己的权限，和自己配置文件，root账号的权限是最高的
* 多任务操作环境：意思就是多人可以同时开同一款软件。

### 多重登入环境的七个基本终端界面
在Linux 当中，预设提供了六个文字界面登入视窗，以及一个图形界面，你可以使用[Alt]+[F1].....[F7] 来切换不同的终端机界面，而且每个终端机界面的登入者还可以不同人

### 任务管理

#### 什么是任务管理
**进行工作管理的行为中，其实每个工作都是目前bash的子程序，亦即彼此之间是有相关性的。我们无法以job control的方式由tty1的环境去管理tty2的bash **，这里不能理解没关系，记住**每个工作都是目前bash的子程序**就行了。

#### 注意
* 这些工作所触发的程序必须来自于你shell 的子程序(只管理自己的bash)；
* 前景：你可以控制与下达指令的这个环境称为前景的工作(foreground)；
* 背景：可以自行运作的工作，你无法使用[ctrl]+c 终止他，可使用bg/fg 呼叫该工作；
* 背景中『执行』的程序不能等待terminal/shell 的输入(input)

#### 管理
* 直接将指令丢到后台中执行的& ：在命令后面加一个 & 就可以
* 将目前的任务丢到后台中暂停：[ctrl]-z
* 观察目前后台任务的状态： jobs
    * 使用 `jobs -l`，可以看到后台的任务号（jobnumber）
* 将后台任务拿到前台来处理：fg
* 让任务在后台下的状态变成运作中： bg

#### kill命令
* 命令：kill [选项] %jubnumber
* 或者：kill [选项] PID
    * 选项与参数：
        - -l ：这个是L 的小写，列出目前kill 能够使用的讯号(signal) 有哪些？
        - signal ：代表给予后面接的那个工作什么样的指示啰！用man 7 signal 可知：
        - -1 ：重新读取一次参数的设定档(类似reload)；
        - -2 ：代表与由键盘输入[ctrl]-c 同样的动作；
        - -9 ：立刻强制删除一个工作；
        - -15：以正常的程序方式终止一项工作。与-9 是不一样的。
- **-9 ** 这个选项通常是用在『强制删除一个不正常的工作』时所使用的， **-15**则是以正常步骤结束一项工作(15也是**默认值**)，所以不要随便乱 **kill -9**

### 计划任务
可以把任务添加到计划任务中，由触发条件触发计划任务。例如，自己写了一个py的爬虫脚本，每天早上8点自动运行。

# 软件管理

## 简介
这里我重点讲 apt（yum）管理软件，简单介绍官网下载安装包或者源代码编译安装。

### Linux 界的两大主流: RPM 与DPKG
|  代表   | 软件管理机制 |   使用命令    | 线上升级命令 |
| :-----: | :----------: | :-----------: | :----------: |
| Debian  |     dpkg     |   dpkg-deb    |   apt-get    |
| Red Hat |     rpm      | rpm, rpmbuild |     yum      |

这里我主要讲的是**dpkg**

### apt-get 操作
**一般使用root权限才能操作**，apt-get的源配置，在 /etc/apt/source.list 中，一般我们改为国内的源，比如阿里源，清华源等等。

* 命令：apt-get [选项] 软件包
    > 选项：
    > apt  install 安装新包
    > apt  remove 卸载已安装的包（保留配置文件）
    > apt  purge 卸载已安装的包（删除配置文件）
    > apt  update 更新软件包列表
    > apt  upgrade 更新所有已安装的包
    > apt  autoremove 卸载已不需要的包依赖
    > apt  dist-upgrade 自动处理依赖包升级
    > apt  autoclean 将已经删除了的软件包的.deb安装文件从硬盘中删除掉
    > apt  clean 删除软件包的安装包，不影响软件的使用


* ~~命令：apt-get [选项] 软件包~~
    > 选项：
    > apt-get install 安装新包
    > apt-get remove 卸载已安装的包（保留配置文件）
    > apt-get purge 卸载已安装的包（删除配置文件）
    > apt-get update 更新软件包列表
    > apt-get upgrade 更新所有已安装的包
    > apt-get autoremove 卸载已不需要的包依赖
    > apt-get dist-upgrade 自动处理依赖包升级
    > apt-get autoclean 将已经删除了的软件包的.deb安装文件从硬盘中删除掉
    > apt-get clean 删除软件包的安装包，不影响软件的使用

**现在用apt会好一点，apt包含了apt-get，而且命令还短**

* 安装已有软件包时，假如目前使用的源有更新版本则更新到最新版本。
* 升级操作，先 `apt-get update` 再 `apt-get upgrade`

# Linux的图形界面

## 简介
目前主流的桌面环境是KDE和GNOME，Linux不像Windows和MacOS那样主要使用桌面环境，Linux的桌面环境也是一个软件，而且会占用比较多的系统资源。服务器的Linux操作系统一般不会装桌面环境。

[环境变量]: 