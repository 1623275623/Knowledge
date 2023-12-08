# Basic of OperationSystem

#### 4.4.2 中断 <a href="#n2cfj" id="n2cfj"></a>

中断是一个发送到CPU的信号告诉他，一个低端的事情来了。比如像按了一下键盘或者是来自外部设备的信号。当这样的事情发生的时候，一个中断请求 interrupt request IRQ 就被提出了。如果操作系统想要回应这个中断就会停下现在正在做的事情然后调用一个特殊的函数被称为ISR interrupt service routine 。然后这个函数会执行一些操作去回应这个事件（理想状态下是尽可能的快）然后控制就回到了中断发生前正在运行的程序。

一共有两种中断，硬件中断和软件中断，如果一个硬件中断要请求就需要放非0电压在CPU的一个针脚上。一个硬件中断可能是由键盘或者鼠标发出的，或者一个周期性计时器在主板上的，还可能是CPU自己发出的。

#### 4.4.5 Process 进程 <a href="#mhlfq" id="mhlfq"></a>

进程是操作系统管理正在运行的程序的一种标志。进程只存在于正在运行的程序当中，当一个程序退出，被杀死，或者崩溃的时候，操作系统就会摧毁和这个进程相关的实例。

多个进程可以同时运行在一个给定的时间，

程序员通过操作系统提供的api和进程进行交互。操作系统之间的API虽然不尽相同但是他们之间所有的关键的概念是相同的。

**4.4.5.1 进程的结构**

一个进程由下面几个部分组成:

1. 进程`id`也叫做`pid`是进程在操作系统当中的唯一的标识。
2. 一系列的权限比如被那个用户拥有，每一个进程都有其所对应的用户群组
3. 来自于父进程的引用，如果有的话
4. 一个专属于该进程的虚拟空间。

所有全部定义的环境变量。

这个进程当前正在工作的目录

一个或者多个的线程

一个进程可以创建很多的线程，可以允许超过一个的指令流同时执行。

Kernel pages

在大多数的操作系统当中，一个进程的地址空间可以被分为两个连续的块。用户空间和内核空间。例如在32位的windows系统当中，用户空间所代表的区域是从0x0 到 0x7fffffff 小于2Gb的地址空间。内核空间所对应的地址范围是0x80000000 到 0xffffffff

用户空间是每一个进程单独有一个虚表进行映射。内核空间使用另一个被所有进程共享的虚表。

fiber 纤程

fiber states

一个纤程可以有两种状态，激活或者不激活
