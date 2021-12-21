**表字段说明**

| 字段名 | 说明 |
| ------------- | ------------- |
| OWNER  | 表属于哪个用户 |
| TABLE_NAME | 表名或者是在CLUSTER_NAME不为空是表示的是他的溢出表，  |
| TABLESPACE_NAME | 所属表空间  |
| CLUSTER_NAME | 该表存在哪个聚簇的名字  |
| IOT_NAME | （索引组织表）表名，该字段不为空表示该表是索引组织表，不是普通的 heap table(堆表)  |
| STATUS  | 如果以前的（drop）删除表操作失败，表的状态将不可用，否则有效  |
| PCT_FREE  | 块中可用空间的最小百分比（一个块保留的空间百分比（预留10%用于update操作），默认是10，表示当数据块的可用空间低于10%后，就不可以被insert了，只能被update）  |
| PCT_USED | 块中使用空间的最小百分比  |
| INI_TRANS  | 初始事务的数量  |
| MAX_TRANS  | 允许的最大的事务数量  |
| INITIAL_EXTENT | 以字节为单位的初始区段大小  |
| NEXT_EXTENT | 下一个extent分配大小，分区表为空  |
| MIN_EXTENTS |  段中分配的区中的最小值，分区表为空  |
MAX_EXTENTS | 段中分配的区中的最大值，分区表为空  |
| PCT_INCREASE  |   在extents中，增长的比例，分区表为空  |
| FREELISTS  |   分配到段中自由列表的数量，分区表为空  |
| FREELIST_GROUPS | 分配到段中的自由列表组数量，分区表为空    |
| LOGGING | 是否记录日志，分区表为空   |
|BACKED_UP |   在上一次修改过后是否备份     |
| NUM_ROWS  | 表示表的行数  |
| BLOCKS  |  表中没有使用过的块  |
| EMPTY_BLOCKS | 以字节为单位的初始区段大小  |
| AVG_SPACE | 可用的平均空间大小    |
| CHAIN_CNT  | 表中跨越多个块的行数量  |
| AVG_ROW_LEN  | 平均行长度，包括行开销  |
| AVG_SPACE_FREELIST_BLOCKS | 在freelist上所有块的平均可用空间  |
| NUM_FREELIST_BLOCKS | 每个实例有多少线程可以同时扫描表   |
|DEGREE | 每个实例有多少线程可以同时扫描表   |
| INSTANCES  |  多少实例可以同时扫描表  |
| CACHE  | 是否将表缓存在缓冲区缓存中  |
| TABLE_LOCK | 表锁定是启用还是禁用  |
| SAMPLE_SIZE | 分析此表时使用的样本大小  |
| LAST_ANALYZED | 最近一次分析该表的日期  |
| PARTITIONED | 是否是分区表  |
| IOT_TYPE | 是否是索引组织表   |
| TEMPORARY | 是否是临时表 |
| SECONDARY | 不懂  |
| NESTED | 是否是嵌套表  |
| BUFFER_POOL | 一级缓存mode设置  KEEP和buffer_pool参数对应的keep含义一样 DEFAULT和buffer_pool参数对应的含义一样(按照类似LRU算法将长时间不用的数据从flash disk中清理出去 NONE表示不起用 |
| FLASH_CACHE | Flash cache是对sga内部的buffer cache的扩展，使用高速固态存储设备为内存和磁盘间提供二级缓存，以增强内存和机械盘之间的吞吐性能，减少响应时间，是一种性能和成本的折衷方案  |
| CELL_FLASH_CACHE | 以字节为单位的扩展区段的大小  |
| ROW_MOVEMENT | 是否启用或禁用行移动  |
|  GLOBAL_STATS |  是否在不合并基础分区的情况下计算统计信息  |
| USER_STATS | 统计数据是否由用户直接输入  |
| DURATION |  临时表的持续时间  |
| SKIP_CORRUPT | 是否启用或禁用跳过损坏块  |
| MONITORING | 是否应该跟踪修改量  |
| CLUSTER_OWNER | 簇表的拥有者  |
| DEPENDENCIES | 是否开启行级别的依赖（每个行被更新的时间戳 默认是块级别的时间戳 https://developer.aliyun.com/article/283585）|
| COMPRESSION | 表示是否压缩 compression  |
| COMPRESS_FOR | 压缩的种类  |
| DROPPED | 表是否已删除且是否在回收站中  |
| READ_ONLY | 表是否只读  |
| SEGMENT_CREATED | 表的段是否已经创建  |
| RESULT_CACHE | 结果缓存模式（MANUAL 默认的模式 仅仅有指定hint result_cache的时候才干使用结果缓存）,(force 全部不包括hint no_result_cache的查询语句都会使用结果缓存) ,auto  在11g下执行相同的SQL第三次，缓存才起作用|






- oracle 3中不同表 https://www.cnblogs.com/51linux/p/6274457.html https://blog.csdn.net/luke_wang/article/details/78544480
- 行迁移与行链接 https://blog.csdn.net/tomato__/article/details/40146573
- 嵌套表 （在一个表 解决一对多） https://www.cnblogs.com/oldcat/archive/2011/09/17/2179928.html
.- 块，区，段，表空间 https://www.cnblogs.com/polestar/p/4225675.html