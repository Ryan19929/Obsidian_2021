# HBase

## HBase简介
- HBase是一种分布式、可扩展、支持海量数据存储的NoSQL数据库
- 数据模型:有行有列，底层物理存储结构是(K-V)，更像一个multi-dimensional map

### HBase逻辑结构
![[HBase逻辑结构.png]]
- 总体是一张表，然后对表进行拆分
- NameSpace相当于DataBase概念，命名空间下有多张表。HBase自带两个命名空间，hbase和default，分别存放HBase内置表和用户默认使用的命名空间
- Region相当于切片
- Row Key相当于主键唯一且按字典顺序存取，查询数据只能依靠RowKey检索
- Column由**Column Family**和**Column Qualifier**进行限定，如info: name ,info: age。
- Time Stamp用于标识数据的不同版本
- Cell{rowkey,column Family: column Qualifier,time Stamp}唯一确定的单元
### HBase物理存储结构
![[HBase物理存储结构.png]]

## HBase基本架构
### HBase架构
![[HBase架构.png]]
- Region Server:管理Region，对数据和Region操作
- Master:管理Region，对表和RegionServer操作
- Zookeeper:HBase通过Zookeeper来做Master的高可用、RegionServer的监控、元数据的入口以及集群配置等工作
- HDFS:提供最终底层数据存储服务

### HBase Shell操作
	1.表的操作
	创建表:create 'student','info'