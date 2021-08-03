# HBase

## HBase简介
- HBase是一种分布式、可扩展、支持海量数据存储的NoSQL数据库
- 数据模型:有行有列，底层物理存储结构是(K-V)，更像一个multi-dimensional map

### HBase逻辑结构
![[HBase逻辑结构.png]]
- 总体是一张表，然后对表进行拆分
- Region相当于切片
- Row Key相当于主键唯一且按字典顺序存取，查询数据只能依靠RowKey检索
- Column由**Column Family**和**Column Qualifier**进行限定，如info: name ,info: age。
- Time Stamp用于标识数据的不同版本
- Cell{rowkey,column Family: column Qualifier,time Stamp}唯一确定的单元
### HBase物理存储结构
![[HBase物理存储结构.png]]
