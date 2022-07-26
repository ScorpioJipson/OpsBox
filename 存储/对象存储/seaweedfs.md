### seaweedfs
seaweedfs是一个非常优秀的由 golang 开发的分布式存储开源项目。它是用来存储文件的系统，并且与使用的语言无关，使得文件储存在云端变得非常方便。

SeaweedFS是基于go语言开发的高可用文件存储系统，主要特征
- 存储上亿的文件(最终受限制于硬盘大小)
- 速度快，内存占用小
 上手使用比fastDFS要简单很多，自带Rest API。

SeaWeeDFS作为对象存储库来有效地处理小文件。不是管理中央主机中的所有文件元数据，中央主机只管理文件卷，它允许这些卷服务器管理文件和它们的元数据。
这减轻了来自中央主机的并发压力，并将文件元数据扩展到卷服务器，允许更快的文件访问（仅一个磁盘读取操作）。

每个文件的元数据只有40字节的磁盘存储开销。

在逻辑上Seaweedfs的几个概念：
- master 存储映射关系，文件和fid的映射关系 weed master
- Node 系统抽象的结点，抽象为datacenter、rack、datanode
- datacenter 数据中心，包含多个rack，类似一个机房
- rack ：属于一个datacenter，类似机房中的一个机架
- datanode ： 存储节点，存储多个volume，类似机架中的一个机器 weed volume
- volume ：逻辑卷，存储needle
- needle： 逻辑卷中的object，对应存储的文件
- collection：文件集，默认所有文件都属于””文件集。如果想给某些文件单独分类，可以在申请id的时候指定相同的文件集
- filer ：指向一个或多个master的file服务器，多个使用逗号隔开。

https://github.com/chrislusf/seaweedfs