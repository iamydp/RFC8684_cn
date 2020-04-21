这份文档取代了MPTCP第零版设计和内容（RFC6824）。本文中的第一版MPTCP并不具备向后兼容第零版的能力。本文还为MPTCP的实施额
外定义了版本协商程序。

1.1设计理念
为防止可能遗留较大的再设计余地，MPTCP工作组在本文提及的MPTCP设计中设定了两条约束性规则：
为增加普及，MPTCP必须向后兼容现有的常规TCP。
链接中的一方或双方必须有多个地址或是多宿主的。
为使设计易于理解，我们可以假定远程主机的地址充分到足以表明会话中存在多条链路，这些链路不需要完全的不相干，它们可以共享一些
路由。即使共享了部分路由，使用多条链路也是有益的，这可以提高网络资源使用率和对网络的容差率。在RFC6356中定义的拥塞控制算法
可以保证使用多条链路不会产生负面影响。同时，在某些情况下有些主机的不同端口也会提供不同的链路（如通过Equal-Cost 
Multipath（ECMP）(RFC2992)），MPTCP也被设计成支持这种情况。
有关MPTCP的向后兼容能力主要围绕三条约束设计（更多参阅RFC6182）：
外部约束：协议必须能在所有现存的中间件（如防火墙、NAT、代理）下工作，所以和常规的TCP看起来要尽可能的像。同时基于现实协议
发出的每个包在到达时都不可能是完整的——他们可能会被切割或合并，TCP Options也可能会被改变。
应用约束：协议需沿用现有的TCP API从而在不对现有应用做任何改动的情况下使其支持MPTCP（尽管在一些太过老旧的应用中所有功能不
会实现）。同时，协议也必须与传统TCP一样具备相同的服务模式。
回退：协议在为与传统主机通讯时应无需用户干预自动回退到标准TCP。
完整有关应用的考量文档（RFC6897）中讨论了提供向后兼容能力的API的特性、传递MPTCP行为的API，以及与常规单链路TCP共同享有的
信息。
有关设计约束的更多讨论和与设计相关的决断参阅MPTCP基本构型（RFC8162）和howhard