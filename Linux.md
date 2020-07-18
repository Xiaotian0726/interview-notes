- [0、Linux 中 Ctrl+c 和 Ctrl+z 的区别](#0linux-中-ctrlc-和-ctrlz-的区别)
  - [Ctrl+c (kill foreground process)](#ctrlc-kill-foreground-process)
  - [Ctrl+z (suspend foreground process)](#ctrlz-suspend-foreground-process)
# 0、Linux 中 Ctrl+c 和 Ctrl+z 的区别
## Ctrl+c (kill foreground process)
发送 `SIGINT` 信号给前台进程组中的所有进程，强制终止进程的执行
## Ctrl+z (suspend foreground process)
发送 `SIGTSTP` 信号给前台进程组中的所有进程，常用于挂起一个进程，而并非结束进程。