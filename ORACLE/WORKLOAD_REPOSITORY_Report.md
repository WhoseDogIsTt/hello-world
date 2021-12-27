Snapshot Information的sessions 实例连接的会话数 表示并发数
https://zhuanlan.zhihu.com/p/361593201

http://www.zhaibibei.cn/
> 负载概况 Load Profile
```

Per Second（每秒）                        Per Transaction（每个事务）

Redo size 431,200.16                18,627,847.04z
每秒产生的重做日志大小(单位字节)，可标志数据变更频率, 数据库任务的繁重与否。本例中平均每秒产生了430K左右的重做，每个事务品均产生了18M的重做
Logical reads: 4,150.76               179,312.72
平次每秒产生的逻辑读，单位是block。
Block changes: 2,252.52                97,309.00
每秒block变化数量，数据库事务带来改变的块数量。
Physical reads: 23.93                    1,033.56
平均每秒数据库从磁盘读取的block数。
Physical writes: 68.08                     2,941.04
平均每秒数据库写磁盘的block数。
User calls: 0.96                      41.36
每秒用户call次数。
Parses: 1.12                                   48.44
Hard parses: 0.04                         1.92
每秒大约1.12个解析，其中有4%为硬解析，系统每25秒分析一些SQL，都还不错。对于优化好的系统，运行了好几天后，这一列应该达到0，所有的sql在一段时间后都应该在共享池中。


Sorts: 0.77                              33.28
每秒产生的排序次数。
Logons: 0.00                            0.20
登入次数 （不知道是不是正确）
Executes: 2.36                          102.12
每秒产生的排序次数。
Transactions: 0.02  
每秒产生的事务数，反映数据库任务繁重与否。
```
-------
> 负载概况LoadProfile
```
该部分可以提前找出ORACLE潜在将要发生的性能问题，很重要。
Instance Efficiency Percentages (Target 100%)

~~~~~~~~~~~~~~~~~~~~

Buffer Nowait %: 100.00  在去访问pga中的数据时，不需要等待的次数
Redo NoWait %: 100.00     该指标指的是redo条目(redo-entries )在redo log中可立即生成而不用等待的次数与全部redo entries的比例 redo entry对应的是每一个DML语句
Buffer Hit %: 99.42   是数据库请求的数据在buffer cache（内存）中直接命中的比例
In-memory Sort %: 100.00 内存内排序和磁盘排序之间的比例  (DeltaMemorySorts / (DeltaDiskSorts + DeltaMemorySorts)) * 100
Library Hit %: 98.11   执行的SQL 语句或者PL/SQL 代码已经存在于shared pool中的library cache中并可复用
Soft Parse %: 96.04  软解析指的是需要执行的SQL语句或PL/SQL程序可以在library cache中找到并重复使用
Execute to Parse %: 52.57   SQL执行次数和解析次数的比值 round(100*(1-parse/exe),2) 当parse远小于execute使，比值接近1，说明解析一次可以执行多次，这是非常好的
Latch Hit %: 100.00   指的是latch（锁）不需要等待即可获取的比例
Parse CPU to Parse Elapsd %: 11.40 %    解析过程中CPU时间占的比重  解析需要CPU进行操作，如在解析过程中有什么东西阻止进程访问CPU，则会导致该比例过小  比例为100%说明解析过程中没有等待 (parse time cpu/parse time elapsed)*100
Non-Parse CPU: 99.55  用在非解析上面的CPU时间




```



> Shared Pool Statistic 共享池的的数据（开始到结束）

Memory Usage %:	35.79	36.34    Oracle数据库Shared Pool的使用率  一般要求在70%-85%之间 一般要求在70%-85%之间  过低说明Shared Pool 剩余空间过多，造成内存的浪费需要减少Shared Pool 的大小                                                                                         
% SQL with executions>1:	91.89	93.94  Shared Pool 中的SQL语句执行次数大于1的比例 低说明SQL 未被复用，请检查绑定变量的问题
% Memory for SQL w/exec>1:	85.56	90.26 执行次数大于1的SQL语句占用的Shared Pool内存比例 越低说明Shared Pool内存更多的被用在存储不能复用的语句上


select * from dba_hist_snapshot order by 1 desc    -- dba_hist_snapshot 视图中查看生成的快照。 dba_hist_snapshot 视图中查看生成的快照。默认情况下，Oracle Database 每小时产生一次快照，并将统计信息在工作负载信息库中保留 8 天，默认情况下，Oracle Database 每小时产生一次快照，并将统计信息在工作负载信息库中保留 8 天
--AWR采用的策略是：每小时对v$active_session_history进行采样一次，并将信息保存到磁盘中，并且保留7天，7天后旧的记录才会被覆盖。这些采样信息被保存在视图wrh$_active_session_history中。而这个采样频率（1小时）和保留时间（7天）是可以根据实际情况进行调整的，这就给DBA们提供了更加有效的系统监测工具

select * from table(dbms_workload_repository.awr_report_html(
3428984334, --DBID
1,          --INSTANCE_NUMBBER
28529,       --SNAP_ID(起始值)
28530))  



SELECT DBMS_WORKLOAD_REPOSITORY.AWR_REPORT_HTML(1569719816,
                                                      1,
                                                      6023,
                                                      6024,
                                                      0) FROM dual;
物理读与逻辑读
Cursors/session  平均会话打开游标的数量

在Oracle的官方文档上，对Session和Connection是这样解释的：
---------------

https://blog.csdn.net/jimsonhappy/article/details/54707694

Connection: Communicate pathway between a client process and an Oracle database instance.
            连接：一个客户端进程和Oracle数据库实例之间的通信链路。

Session: A logical entity in the database instance memory that represnts the state of a current user login to a database. A single connection can have 0, 1 or more sessions established on it.
            会话：用于展示当前登录到数据库用户的状态的数据库实例内存中的一个逻辑实体。一个单独的连接可以有0，1，或者更多的会话。
————————————————
版权声明：本文为CSDN博主「Jerry_yyw」的原创文章，遵循CC 4.0 BY-SA版权协议，转载请附上原文出处链接及本声明。
原文链接：https://blog.csdn.net/yywhawk/article/details/50417739
----------------------
http://www.zhaibibei.cn/awr/1.1/#1
Oracle Real Application Cluster=真实网络集群