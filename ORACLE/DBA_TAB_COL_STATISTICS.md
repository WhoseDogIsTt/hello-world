>列的统计信息
```
owner      varchar2(30)   table, view or cluster owner
table_name varchar2(30)   table, view or cluster name
column_name varchar2(30) column name
num_distinct number      the number of distinct values in the column
low_value    raw(32)    the low value in the column
high_value   raw(32)    the high value in the column
density       number     the density of the column （目标列的密度 只跟直方图有关）
num_nulls     number    the number of nulls in the column
num_buckets    number   the number of buckets in histogram for the column(直方图所用桶的数量)
last_analyzed   date     the date of the most recent time this column was analyzed
sample_size      number     the sample size used in analyzing this column
global_stats     varchar2(3)     are the statistics calculated without merging underlying partitions?
user_stats    varchar2(3)   were the statistics entered directly by the user?
avg_col_lennumber          the average length of the column in bytes
histogram                varchar2(15)







```