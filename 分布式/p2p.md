## p2p算法学习笔记

Chord、Pastry、CAN、Kademlia
kad--结构化--以太坊，ipfs

gossip--非结构化--比特币，fabric

https://zhuanlan.zhihu.com/p/43340851

**Kad**

Ethereum使用DHT算法并不是很合理，因为它使用节点保存整个链数据，不像IPFS那样分片保存数据，因此Ethereum真正适合的协议应该是像Bitcoin那样的Gossip协议。

**Gossip protocal/Epidemic protocal，流行病协议/流言算法/疫情传播算法**

https://www.jianshu.com/p/8279d6fd65bb

主要用于分布式数据库中各个副本节点同步数据，这种场景的一个最大特点是组成的网络节点都是对等节点，是非结构化网络。

Gossip过程由种子节点发起，它会随机地选择周围几个节点散播消息，收到消息的节点也会重复该过程，直到最终网络中所有的节点都收到了消息。这个过程可能需要一定的时间，由于不能保证某个时刻所有节点都收到消息，但是理论上最终所有节点都会收到消息，因此它是一个最终一致性协议。

优势：1，扩展性 2，容错 3，去中心化 4，一致性收敛（消息传播速度logN） 5，简单

缺陷：1，消息延迟 2，消息冗余