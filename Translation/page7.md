1.2MPTCP之于网络栈
MPTCP工作于传输层，并且对于其它层来说都是透明的。MPTCP实质上实在标准TCP之上的扩展。图一揭示了MPTCP和网络栈各层的关系。
MPTC被设计为在无需对应用做出任何改动的情况下使应用直接支持MPTCP。有关更多MPTCP如何与应用交互的问题参阅RFC6897

picture reserved

图一：标准TCP与MPTCP协议栈的比较。

1.3术语
这份文档使用了一些特有的，或在使用情景中存在特定含义的词语。如下：
链路(Path):接收侧和发送侧间的一系列连接，在某些情境中可以被描述为原地址+端口和目标地址+端口的4元组地址/端口对。（如
IP#-A2）
分流(Subflow):在不同链路上通过的TCP片段流，许多的分流组合成了一个MPTCP连接。分流的新建和终止与常规TCP类似。
(MPTCP)连接(Connection):一个或多个分流的集合，负责为应用提供服务并与主机通信，每个应用的套接字与连接存在一对一对应关系。
Data-Level:装载的数据名义上是通过连接(Connection)传输，实际上是由分流传输的(Subflow)，故data-level与connection-level
等价，但与subflow-level不同，subflow-level是单独隶属于分流的性质。
Token:主机(Host)赋予每个MPTCP连接的唯一标识符，也可能指代连接ID。(Connection ID)
除了以上术语外，还有一些术语在本文档中的语义有些些许变化，详见本文档第4章。