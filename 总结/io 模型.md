

# 概述

io分为

- 文件io
- 网络io

Io模型分为以下几种

- 阻塞模型

> 发起请求一直阻塞，直到数据完成

- 非阻塞

> 没有数据，返回，重复请求

- 多路复用
- 信息驱动
- 异步







# FAQ

**为什么select有最大数1024的限制，而poll，epoll却没有？**

> 1. 通过man可以看到select是90年代实现的，结合当时那个年代硬件的最佳建议数字
> 2. epoll与poll也不是没有最大数限制，可以通过sysctl设置，连表实现
> 3. 考虑到兼容性，所以不能直接修改select，而重新开发epoll或poll模式的功能
> 4. 在数量较少的情况下select模式（轮循模式）有可能会比epoll模式效率更高

**IO效率是否随文件描述符（fd）的增加而线性下降**
传统的select/poll的一个致命弱点就是当你拥有一个很大的socket集合时，不过任一时间只有部分socket是活跃的，select/poll每次调用都会线性扫描整个socket集合，这将导致IO处理效率呈现线性下降。

但是，epoll不存在这个问题，它只会对活跃的socket进行操作，这是因为在内核实现中，epoll是根据每个fd上面的callback函数实现的。因此，只有活跃的socket才会主动去调用callback函数，其他idle状态socket则不会。在这一点上，epoll实现了一个伪AIO，其内部推动力在内核。

在一些benchmark中，如果所有的socket基本上都是活跃的，如高速LAN环境，epoll并不比select/poll效率高，相反，过多使用epoll_ctl，其效率反而还有稍微下降。但是，一旦使用idle connections模拟WAN环境，epoll的效率就远在select/poll之上了。

**使用mmap加速内核与用户空间的消息传递**
无论是select，poll还是epoll，它们都需要内核把fd消息通知给用户空间。因此，如何避免不必要的内存拷贝就很重要了。对于该问题，epoll通过内核与用户空间mmap同一块内存来实现。

# 参考资料

[**I/O Systems**](https://www.cs.uic.edu/~jbell/CourseNotes/OperatingSystems/13_IOSystems.html)

[c demo](https://github.com/hitzhangjie/Linux-IO-Model)

[linux五种IO模型](https://juejin.im/post/5c725dbe51882575e37ef9ed)

[Linux Network IO Model、Socket IO Model - select、poll、epoll](https://www.cnblogs.com/LittleHann/p/3897910.html)

[Linux I/O Models and GO Network Model Part I](https://xiaoxubeii.github.io/articles/linux-io-models-and-go-network-model/)

[透彻Linux(Unix)五种IO模型](https://mp.weixin.qq.com/s?__biz=MzIxMjAzMDA1MQ==&mid=2648945760&idx=1&sn=125c5e29e7e53e0e0c66d327fa09f828&chksm=8f5b536cb82cda7a6c7a4f57b4671439a558a2b695026090b5ef80899df1689981892e9c4724#rd)

[5种网络IO模型](https://zhuanlan.zhihu.com/p/54580385)

> UNIX® Network Programming Volume 1, Third Edition: The Sockets Networking

https://blog.csdn.net/zhaobryant/article/details/80557262



https://www.zhihu.com/question/37219281?sort=created