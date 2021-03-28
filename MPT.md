# MPT

TODO

https://ethfans.org/posts/merkle-patricia-tree-in-detail?spm=a2c4e.10696291.0.0.275319a4c2NlTq

https://blog.csdn.net/TurkeyCock/article/details/80609475

https://blog.csdn.net/weixin_41545330/article/details/79370198

https://fisco-bcos-documentation.readthedocs.io/zh_CN/latest/docs/design/storage/mpt.html

https://yq.aliyun.com/articles/679582

MPT 全称 Merkle Patricia Trie，是以太坊用来存储数据的一种数据结构。MPT 融合了 Trie、Patricia Trie、Merkle Tree 这三种数据结构的优点，从而实现快速查找并节省存储空间。

1，Trie，字典树/前缀树。

2，Patricia Trie，压缩前缀树，在Trie的基础上进行了存储空间的优化。

3，Merkle Tree，存储hash值的树，是一种用于快速验证内容完整性的数据结构。从可信源获得Merkle Tree Root，可以从其他不可信源获取Merkle Tree，通过可信的树根来检查Merkle Tree。Merkle Tree可以一次下载一个分支，并立即验证这个分支。

扩展：简单支付验证（SPV，Simplified Payment Verification）：轻节点只下载区块头，SPV即轻节点确认一个交易的过程，思路是去相邻的全节点请求部分Merkle树信息，到本地验证通过，则说明其他全节点接受了这个交易。SPV用于实现侧链技术？

4，MPT，融合了上面3中数据结构又有细微差别。用来检索字节数据，所以是16叉树，分别代表0x0~0xF。

MPT中四种节点类型：

- 空节点（NULL）
- 分支节点（branch node）：包含16个分支，以及1个value
- 扩展节点（extension node）：只有一个子节点
- 叶子节点（leaf node）：没有子节点，包含一个value

Merkle路径是啥啊，是怎么通过路径定位交易