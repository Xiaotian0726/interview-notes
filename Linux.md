- [0、Linux 中 Ctrl+c 和 Ctrl+z 的区别](#0linux-中-ctrlc-和-ctrlz-的区别)
  - [Ctrl+c (kill foreground process)](#ctrlc-kill-foreground-process)
  - [Ctrl+z (suspend foreground process)](#ctrlz-suspend-foreground-process)
- [1、Linux 文件权限](#1linux-文件权限)
  - [chmod 命令](#chmod-命令)
# 0、Linux 中 Ctrl+c 和 Ctrl+z 的区别
## Ctrl+c (kill foreground process)
发送 `SIGINT` 信号给前台进程组中的所有进程，强制终止进程的执行
## Ctrl+z (suspend foreground process)
发送 `SIGTSTP` 信号给前台进程组中的所有进程，常用于挂起一个进程，而并非结束进程。

# 1、Linux 文件权限
Linux 文件采用 10 个标志位来表示文件权限：
```
-rw-r--r--  1 skyline  staff    20B  1 27 10:34 1.txt
drwxr-xr-x   5 skyline  staff   170B 12 23 19:01 ABTableViewCell
```
第一个字符一般用来区分文件和目录：
* d：目录。在 ext2fs 中，目录是一个特殊的文件
* -：普通文件
* l：符号链接文件，实际上指向另一个文件
* b、c：分别表示区块设备和其他的外围设备，是特殊类型的文件
* s、p：关系到系统的数据结构和管道，通常很少见到

第 2 ~ 10 个字符每 3 个为一组，左边 3 个字符表示所有者权限，中间 3 个字符表示与所有者同一组的用户的权限，右边 3 个字符是其他用户的权限.一共 9 个字符，含义如下:
* r：对文件而言，具有读取文件内容的权限；对目录而言，具有浏览目录的权限
* w：对文件而言，具有新增、修改文件内容的权限；对目录来说，具有删除、移动目录内文件的权限
* x：对文件而言，具有执行文件的权限；对目录来说该用户具有进入目录的权限

## chmod 命令
chmod 命令非常重要，用于改变文件或目录的访问权限，用户可以用它控制文件和目录的访问权限
```
chmod [who] [+|-|=] [mode] <文件名>
```
[who]
* "u"：用户，即文件或目录的所有者
* "g"：同组用户，即与文件属主有相同组 ID 的用户
* "o"：其他用户
* "a"：所有用户（默认值）

[+|-|=]
* "+"：添加某个权限
* "-"：取消某个权限
* "="：赋予给定权限并取消其他所有权限（如果有的话）