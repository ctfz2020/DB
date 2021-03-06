# 需求分析文档

随着互联网和物联网的发展, 接入网的设备越来越多, 随之产生的数据爆炸性增长, 如何实时高效的从这些数据中分析出有用的信息成为了难题.

对产生的大量日志进行处理, 可以提取出结构化数据. 这些数据必然含有产生时间属性, 并且包括多种维度信息, 标识不同意义的指标数据等. 分析需求包括数据过滤, 分组, 聚合等.  

存储这种数据并支持分析你可以想到非常多的方案, 包括传统数据库mysql, oracle,  大数据方案Hadoop,Impala, Hive, Hbase, Apache Druid,Elasticsearch等. 但这些方案在OLAP分析都有自己的优缺点:

#### Hadoop

Hadoop提供了HDFS和YARN两种服务,其中HDFS可以存储数据, YARN可以运行MapReduce程序, MapReduce提供了编程接口, 可以根据需求对数据进行分析, 缺点是需求变化就需要重新写程序, 分析离线数据,并且运行慢.

#### Hadoop+Hive

hive是运行在Hadoop之上的服务, 用于解决MapReduce编写问题, 可以接收用户编写的sql语句并转化为MapReduce程序,  但是其它两个缺点还是存在.

#### Hadoop+Impala

Impala功能与Hive类似, 不同点是Impala没有用到MapReduce, 而是基于内存重写了计算逻辑, 执行速度有了质变的提升, 但是数据不实时的却点还是存在.

#### Apache Druid

节点类型和依赖组件过多, 内存管理不完善, 运维困难

#### Elasticsearch

不适合多维分析



列举这么多缺点不是说以上这些方案都一无是处, 每个产品和方案都是在不同的需求下产生的, 在特定的使用场景下都是利器, 只是在运维简单, 实时处理, 多维分析的场景下不适用.

我和小伙伴在Apache Druid和Presto, 分布式文件系统上都有很深入的研究, 深知它们在实现上都有局限性, 但也不想对它们进行过多的修改, 都强烈希望能开发一款符合我们需求的数据库, 走自己的路. 虽然我们知道开发一款数据库并不是简单的事情, 我们会坚持, 投入时间在自己感兴趣的事情上是令人兴奋的.

综合以上原因,所以我们决定开发一款运维简单, 高效的分布式分析数据库.