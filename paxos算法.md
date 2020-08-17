

三个角色

- proposer，提出提案，提案包括提案编号和value
- acceptor，收到提案后可以接受（accept）提案，若提案获得多数派（majority）的 acceptors 的接受，则称该提案被批准（chosen）
- learner，只能学习被批准的的提案

精确的定义问题：

- 决议（value）只有在被 proposers 提出后才能被批准（未经批准的决议称为“提案（proposal）”）；

- 在一次 Paxos 算法的执行实例中，只批准（chosen）一个 value；

- learners 只能获得被批准（chosen）的 value。

# 参考资料

- [Paxos算法](https://zh.wikipedia.org/wiki/Paxos算法)