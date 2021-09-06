# Day1

## 1.介绍
The Hadoop Distributed File System (HDFS) is a distributed file system designed to run on commodity hardware. It has many similarities with existing distributed file systems. However, the differences from other distributed file systems are significant. HDFS is highly fault-tolerant and is designed to be deployed on low-cost hardware. HDFS provides high throughput access to application data and is suitable for applications that have large data sets. HDFS relaxes a few POSIX requirements to enable streaming access to file system data. HDFS was originally built as infrastructure for the Apache Nutch web search engine project. HDFS is part of the Apache Hadoop Core project. The project URL is [http://hadoop.apache.org/](http://hadoop.apache.org/).


## 2.目标
- 对硬件错误的宽容
- 流式数据访问
- 大数据集
- 一次写，多次读，可以末尾添加
- 计算时，数据在附近
- 兼容性非常好
## 2.总体架构
![[Pasted image 20210831110939.png]]
- master/slave=NameNode/DataNode
- HDFS块的大小设置主要取决于磁盘传输速率