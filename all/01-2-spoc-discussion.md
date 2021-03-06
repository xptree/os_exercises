# 操作系统概述思考题

## 个人思考题

---

分析你所认识的操作系统（Windows、Linux、FreeBSD、Android、iOS）所具有的独特和共性的功能？
- [x]  

> 操作系统是一种软件，折中软件管理计算机硬件资源和软件资源，并且向上层计算机应用提供服务。
* Windows系统有友好的UI设计和丰富的上层应用，但其在权限控制、软件管理方面都做得不是很好
* Linux的特点就是自由啦，它对于操作系统的使用者非常透明；此外它相对Windows稳定许多，也不容易受电脑病毒的影响。 
* FreeBSD是一种自由的类Unix操作系统，它起源于AT&T Unix，是经过BSD、386BSD和4.4BSD发展而来的类Unix的一个重要分支。
* Android中文俗称安卓，是一个以Linux为基础的开放源代码移动设备操作系统，主要用于智能手机和平板电脑。它的特点是开放性和可移植性。
* IOS是由苹果公司为移动设备所开发的操作系统，不支持非苹果的硬件设备，且严格控制软件开发者。

请总结你认为操作系统应该具有的特征有什么？并对其特征进行简要阐述。
- [x]  

> 我认为操作系统需要有的特征有：
* 控制程序的执行过程，放置错误和计算机的不当使用
* 执行用户程序，给用户程序提供各种服务。
* 方便用户使用计算机。

请给出你觉得的更准确的操作系统的定义？
- [x]  

>  操作系统是管理计算机硬件与软件资源的计算机程序，同时也是计算机系统的内核与基石。
操作系统需要处理如管理与配置内存、决定系统资源供需的优先次序、控制输入与输出设备、操作网络与管理文件系统等基本事务。
操作系统也提供一个让用户与系统交互的操作界面。 


你希望从操作系统课学到什么知识？
- [x]  

>
* 了解操作系统的设计哲学和思想。
* 融会之前学习的计算机组成原理，数据结构，程序设计等课程。
* 了解一个全新的领域。

---

## 小组讨论题

---

目前的台式PC机标准配置和价格？
- [x]  

>
* 酷睿i5-4xxx四核处理器
* 频率3.2GHz
* GTX750独显
* 8GDDR3内存
* 1TSATA7200rpm硬盘
* 主机共四五千元
* 再配一个1000左右的24英寸显示器

你理解的命令行接口和GUI接口具有哪些共性和不同的特征？
- [x]  

> 
* 命令行和GUI都是用户界面的一种，都可以完成操作系统提供的一些功能。
* GUI对于用户更加友好，操作更加简洁
* 命令行更加节约计算机系统的资源，在熟练的情况下能够获得更快的操作速度。

为什么现在的操作系统基本上用C语言来实现？
- [x]  

> 
* 历史原因，在人们实现现代操作系统的时候，C语言是为数不多的高级语言之一。
* 客观原因，C语言比较底层，比如可以直接进行内存相关的操作；同时相对于汇编，C又更加抽象，所以C是抽象和底层的一个折衷。此外，C是一种精炼的语言（它的spec相对C++非常短），因而他也更加准确，
相对于其他软件，操作系统对于bug的成本是很高的。所以操作系统基本上用C语言来实现。

为什么没有人用python，java来实现操作系统？
- [x]  

> 
* python需要一个解释器，java需要一个虚拟机（需要一些底层的汇编代码来启动jvm并且访问硬件）。
* 他们在效率上和C有数量级上的差距。
* 其实已经有一些java实现的os比如JNode，JX和JavaOS。


请评价用C++来实现操作系统的利弊？
- [x]  

> 
* 利：可以使用C++面向对象编程的许多好的特性，抽象代码的逻辑。
* 弊：C++相比C是一种很复杂的语言，它的OOP所抽象的逻辑所编译出的汇编代码是非常不可读的，会使得调试变得非常麻烦；此外C++的可移植性没有C好；C++可能出现的问题也比C多。

---

## 开放思考题

---

请评价微内核、单体内核、外核（exo-kernel）架构的操作系统的利弊？
- [x]  

> 
* 在微内核中，微内核的功能被划分成为独立的过程，这样的缺点是不能向单内核一样直接调用函数，而是通过消息传递处理通信。优点在于不影响系统其他部分的情况下，用更高效的实现代替现有系统模块的工作将会更加容易。
* 单内
核就是把它从整体上作为一个单独的大过程来实现，并同时运行在一个单独的地址空间。因此这样的
内核通常以单个静态二进制文件的形式存放于磁盘。所有内核服务都在这样的一个大内核空间中运行。
内核之间的通信是微不足道的，因为大家都运行在内核态，并身处同一地址空间：内核可以直接调用函
数，这与用户空间没有什么区别。单模块具有简单和高性能的特点。 
* 外核，运作在核心空间的唯一行程就是内核，唯一工作就是负责分配系统资源，并防止使用者行程存取到其他行程的资源。每个使用者行程都拥有一个虚拟机器，可以执行自己的操作系统。

请评价用LISP,OCcaml, GO, D，RUST等实现操作系统的利弊？
- [x]  

> 都没用过。 

进程切换的可能实现思路？
- [x]  

> 设置一个计时器，计时器被触发后进入触发中断，调用系统内核态进行进程切换。

计算机与终端间通过串口通信的可能实现思路？
- [x]  

>  
* 轮询串口是否可读/写，事实上这也是上学期计算机组成原理中我们采取的方法。
* 当串口有数据需要读的时候触发中断，操作系统进行数据处理。

为什么微软的Windows没有在手机终端领域取得领先地位？
- [x]  

>
* 起步太晚，市场已经被android和ios瓜分。
* 应用比较匮乏。 

你认为未来（10年内）的操作系统应该具有什么样的特征和功能？
- [x]  

> 网络化，云端化，比如chrome os。

---
