# 分布式计算框架MapReduce
### MapReduce简介
######  MapReduce是一种用在大群商场硬件集群对海量数据实施可靠的，高容错的分布式计算框架，MapReduce采用”分而治之”的思想，把对大规模数据集的操作，分发给一个主节点管理下的各个分节点共同完成，然后通过整合各个节点的中间结果，得到最终结果。
######  在分布式计算中，MapReduce框架负责处理了并行编程中分布式存储.工作调度.负载均衡.容错均衡。容错处理以及网络通信等复杂问题，把处理过程高度抽象为两个函数：map和reduce，map负责把任务分解成多个任务，reduce负责把分解后多任务处理的结果汇总起来.需要注意的是，用MapReduce来处理的数据集（或任务）必须具备这样的特点：待处理的数据集可以分解成许多小的数据集，而且每一个小数据集都可以完全并行地进行处理。
### MapReduce编程模型
###### 1.简单模型 2复杂模型
### MapReduce编程实例

### MapReduce数据流
###### MpaReduce是Hadoop的核心组件，它通过将工作划分为一组独立的任务来并行处理大量数据,在 MapReduce 中数据是一步一步从 Mapper 流向 Reducer。
##### 1. 分片.格式化数据源（InputFormat）
###### InputFormat主要有两个任务，对源文件进行切片并确定mapper的数量；对各分片进行格式化，处理成<key,value>形式的数据流并传递给mapper。
##### Map过程
###### mapper接收并处理数据，具体的处理过程由用户定义。它处理每条输入记录（来自 RecordReader）并生成新的键值对，而 Mapper 生成的这个键值对与输入对完全不同。Mapper 的输出也称为中间输出，写入本地磁盘。
##### 3.Combiner过程
###### combiner的作用就是对map（）端的输出先做一次合并，减少map和reduce之间的传输，一旦被执行，他的输出将通过partitioner进一步执行。
##### 4.Shuffle过程
###### shuffle的过程是指从mapper产生的直接输出结果，经过一系列的处理成为最终的reduce直接输出数据为止的整个过程。
##### 5.Reduce过程
###### Reducer主要是让mapper产生的中间数据作为输入数据，并调用reducer函数对每对键值对进行处理。
##### 6.RecordWriter
###### 用于将Reducer产生的key-value写入到输出文件中
##### OutputFormat
###### RecordWriter 将这些输出键值对写入输出文件的方式由 OutputFormat 决定。Hadoop 提供的OutputFormat 实例用于在HDFS或本地磁盘上写入文件。
### MapReduce任务运行流程
![](https://huatu.98youxi.com/markdown/work/uploads/upload_f3affde4b4616ef2f7cef3d35a099439.png)