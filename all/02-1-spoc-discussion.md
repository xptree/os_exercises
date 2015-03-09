#lec 3 SPOC Discussion

## 第三讲 启动、中断、异常和系统调用-思考题

## 3.1 BIOS
 1. 比较UEFI和BIOS的区别。
 1. 描述PXE的大致启动流程。

## 3.2 系统启动流程
 1. 了解NTLDR的启动流程。
 1. 了解GRUB的启动流程。
 1. 比较NTLDR和GRUB的功能有差异。
 1. 了解u-boot的功能。

## 3.3 中断、异常和系统调用比较
 1. 举例说明Linux中有哪些中断，哪些异常？
 1. Linux的系统调用有哪些？大致的功能分类有哪些？  (w2l1)

```
  + 采分点：说明了Linux的大致数量（上百个），说明了Linux系统调用的主要分类（文件操作，进程管理，内存管理等）
  - 答案没有涉及上述两个要点；（0分）
  - 答案对上述两个要点中的某一个要点进行了正确阐述（1分）
  - 答案对上述两个要点进行了正确阐述（2分）
  - 答案除了对上述两个要点都进行了正确阐述外，还进行了扩展和更丰富的说明（3分）
 ```

* 进程控制：
```
fork    创建一个新进程
clone   按指定条件创建子进程
execve  运行可执行文件
exit    中止进程
_exit   立即中止当前进程
getdtablesize   进程所能打开的最大文件数
getpgid 获取指定进程组标识号
setpgid 设置指定进程组标志号
getpgrp 获取当前进程组标识号
setpgrp 设置当前进程组标志号
getpid  获取进程标识号
getppid 获取父进程标识号
getpriority 获取调度优先级
setpriority 设置调度优先级
modify_ldt  读写进程的本地描述表
nanosleep   使进程睡眠指定的时间
nice    改变分时进程的优先级
pause   挂起进程，等待信号
personality 设置进程运行域
prctl   对进程进行特定操作
ptrace  进程跟踪
sched_get_priority_max  取得静态优先级的上限
sched_get_priority_min  取得静态优先级的下限
sched_getparam  取得进程的调度参数
sched_getscheduler  取得指定进程的调度策略
sched_rr_get_interval   取得按RR算法调度的实时进程的时间片长度
sched_setparam  设置进程的调度参数
sched_setscheduler  设置指定进程的调度策略和参数
sched_yield 进程主动让出处理器,并将自己等候调度队列队尾
vfork   创建一个子进程，以供执行新程序，常与execve等同时使用
wait    等待子进程终止
wait3   参见wait
waitpid 等待指定子进程终止
wait4   参见waitpid
capget  获取进程权限
capset  设置进程权限
getsid  获取会晤标识号
setsid  设置会晤标识号
```

* 文件系统控制

1. 文件读写操作
```
fcntl   文件控制
open    打开文件
creat   创建新文件
close   关闭文件描述字
read    读文件
write   写文件
readv   从文件读入数据到缓冲数组中
writev  将缓冲数组里的数据写入文件
pread   对文件随机读
pwrite  对文件随机写
lseek   移动文件指针
_llseek 在64位地址空间里移动文件指针
dup 复制已打开的文件描述字
dup2    按指定条件复制文件描述字
flock   文件加/解锁
poll    I/O多路转换
truncate    截断文件
ftruncate   参见truncate
umask   设置文件权限掩码
fsync   把文件在内存中的部分写回磁盘
```

2. 文件系统操作
```
access  确定文件的可存取性
chdir   改变当前工作目录
fchdir  参见chdir
chmod   改变文件方式
fchmod  参见chmod
chown   改变文件的属主或用户组
fchown  参见chown
lchown  参见chown
chroot  改变根目录
stat    取文件状态信息
lstat   参见stat
fstat   参见stat
statfs  取文件系统信息
fstatfs 参见statfs
readdir 读取目录项
getdents    读取目录项
mkdir   创建目录
mknod   创建索引节点
rmdir   删除目录
rename  文件改名
link    创建链接
symlink 创建符号链接
unlink  删除链接
readlink    读符号链接的值
mount   安装文件系统
umount  卸下文件系统
ustat   取文件系统信息
utime   改变文件的访问修改时间
utimes  参见utime
quotactl    控制磁盘配额
```

* 系统控制
```
ioctl   I/O总控制函数
_sysctl 读/写系统参数
acct    启用守护进程进行控制
vm86    进入模拟8086模式
create_module   创建可装载的模块项
delete_module   删除可装载的模块项
init_module 初始化模块
query_module    查询模块信息
*get_kernel_syms    取得核心符号,已被query_module代替
```

* 内存管理
```
brk 改变数据段空间的分配
sbrk    参见brk
mlock   内存页面加锁
munlock 内存页面解锁
mlockall    调用进程所有内存页面加锁
munlockall  调用进程所有内存页面解锁
mmap    映射虚拟内存页
munmap  去除内存页映射
mremap  重新映射虚拟内存地址
msync   将映射内存中的数据写回磁盘
mprotect    设置内存映像保护
getpagesize 获取页面大小
sync    将内存缓冲区数据写回硬盘
cacheflush  将指定缓冲区中的内容写回磁盘
```

* 网络管理
```
getdomainname   取域名
setdomainname   设置域名
gethostid   获取主机标识号
sethostid   设置主机标识号
gethostname 获取本主机名称
sethostname 设置主机名称
```

* socket控制
```
soc识号
setegid 设置有效组标识号
geteuid 获取有效用户标识号
seteuid 设置有效用户标识号
setregid    分别设置真实和有效的的组标识号
setreuid    分别设置真实和有效的用户标识号
getresgid   分别获取真实的,有效的和保存过的组标识号
setresgid   分别设置真实的,有效的和保存过的组标识号
getresuid   分别获取真实的,有效的和保存过的用户标识号
setresuid   分别设置真实的,有效的和保存过的用户标识号
setfsgid    设置文件系统检查时使用的组标识号
setfsuid    设置文件系统检查时使用的用户标识号
getgroups   获取后补组标志清单
setgroups   设置后补组标志清单
```

* 进程间通信
```
ipc 进程间通信总控制调用
```

1. 信号
```
sigaction   设置对指定信号的处理方法
sigprocmask 根据参数对信号集中的信号执行阻塞/解除阻塞等操作
sigpending  为指定的被阻塞信号设置队列
sigsuspend  挂起进程等待特定信号
signal  参见signa
```

2. 消息
```
msgctl  消息控制操作
msgget  获取消息队列
msgsnd  发消息
msgrcv  取消息
```

3. 管道
```
pipe    创建管道
```

4. 信号量
```
semctl  信号量控制
semget  获取一组信号量
semop   信号量操作
```

5. 共享内存
```
shmctl  控制共享内存
shmget  获取共享内存
shmat   连接共享内存
shmdt   拆卸共享内存
```

 1. 以ucore lab8的answer为例，uCore的系统调用有哪些？大致的功能分类有哪些？(w2l1)
 
 ```
  + 采分点：说明了ucore的大致数量（二十几个），说明了ucore系统调用的主要分类（文件操作，进程管理，内存管理等）
  - 答案没有涉及上述两个要点；（0分）
  - 答案对上述两个要点中的某一个要点进行了正确阐述（1分）
  - 答案对上述两个要点进行了正确阐述（2分）
  - 答案除了对上述两个要点都进行了正确阐述外，还进行了扩展和更丰富的说明（3分）
 ```
 
## 3.4 linux系统调用分析
 1. 通过分析[lab1_ex0](https://github.com/chyyuu/ucore_lab/blob/master/related_info/lab1/lab1-ex0.md)了解Linux应用的系统调用编写和含义。(w2l1)
 

 ```
  + 采分点：说明了objdump，nm，file的大致用途，说明了系统调用的具体含义
  - 答案没有涉及上述两个要点；（0分）
  - 答案对上述两个要点中的某一个要点进行了正确阐述（1分）
  - 答案对上述两个要点进行了正确阐述（2分）
  - 答案除了对上述两个要点都进行了正确阐述外，还进行了扩展和更丰富的说明（3分）
 
 ```
 
 1. 通过调试[lab1_ex1](https://github.com/chyyuu/ucore_lab/blob/master/related_info/lab1/lab1-ex1.md)了解Linux应用的系统调用执行过程。(w2l1)
 

 ```
  + 采分点：说明了strace的大致用途，说明了系统调用的具体执行过程（包括应用，CPU硬件，操作系统的执行过程）
  - 答案没有涉及上述两个要点；（0分）
  - 答案对上述两个要点中的某一个要点进行了正确阐述（1分）
  - 答案对上述两个要点进行了正确阐述（2分）
  - 答案除了对上述两个要点都进行了正确阐述外，还进行了扩展和更丰富的说明（3分）
 ```
 
## 3.5 ucore系统调用分析
 1. ucore的系统调用中参数传递代码分析。
 1. ucore的系统调用中返回结果的传递代码分析。
 1. 以ucore lab8的answer为例，分析ucore 应用的系统调用编写和含义。
 1. 以ucore lab8的answer为例，尝试修改并运行ucore OS kernel代码，使其具有类似Linux应用工具`strace`的功能，即能够显示出应用程序发出的系统调用，从而可以分析ucore应用的系统调用执行过程。
 
## 3.6 请分析函数调用和系统调用的区别
 1. 请从代码编写和执行过程来说明。
   1. 说明`int`、`iret`、`call`和`ret`的指令准确功能
 
