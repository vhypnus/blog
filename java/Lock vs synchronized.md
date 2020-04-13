





> Impossible. It can be implemented in different ways, e.g., via the [Compare-and-swap](http://en.wikipedia.org/wiki/Compare-and-swap) where the hardware guarantees sequential execution. It can get a bit complicated in presence of multiple cores or even multiple sockets and needs a complicated [protocol](http://en.wikipedia.org/wiki/MESI_protocol) between the cores, but this is all taken care of.



synchronized 锁升级

无锁 偏向锁(CAS，对象头)  轻量级锁(自旋，JVM参数自旋次数,空耗CPU)  重量级锁(休眠，不参与调度，唤醒成本较高)

Lock

- 原理AQS

CAS 

- ABA问题
- 通过版本号处理

