# Sqoop User Guide

## 1.介绍
- Sqoop用于在关系型数据库和HDFS中转换传输数据。
- 使用MapReduce来传输数据

## 2.版本
- Sqoop v1.4.7

### 3.用途
- 数据库到HDFS，Sqoop会一条一条的读取数据，对于 mainframe datasets, Sqoop 会从每一个 mainframe dataset 读取数据并传输到 HDFS。
- HDFS到数据库，