```

[ona2@ip-172-30-2-88 ~]$ beeline
2017-01-12 20:21:44,880 WARN  [main] mapreduce.TableMapReduceUtil: The hbase-prefix-tree module jar containing PrefixTreeCodec is not present.  Continuing without it.
Beeline version 1.1.0-cdh5.9.0 by Apache Hive
beeline> !connect jdbc:hive2://ip-172-30-2-120.us-west-2.compute.internal:10000/default;principal=hive/ip-172-30-2-120@US-WEST-2.COMPUTE.INTERNAL
scan complete in 1ms
Connecting to jdbc:hive2://ip-172-30-2-120.us-west-2.compute.internal:10000/default;principal=hive/ip-172-30-2-120@US-WEST-2.COMPUTE.INTERNAL
Connected to: Apache Hive (version 1.1.0-cdh5.9.0)
Driver: Hive JDBC (version 1.1.0-cdh5.9.0)
Transaction isolation: TRANSACTION_REPEATABLE_READ
0: jdbc:hive2://ip-172-30-2-120.us-west-2.com> show tables;
INFO  : Compiling command(queryId=hive_20170112202222_7e1575c8-2e18-4333-a4e7-9d4cfa805013): show tables
INFO  : Semantic Analysis Completed
INFO  : Returning Hive schema: Schema(fieldSchemas:[FieldSchema(name:tab_name, type:string, comment:from deserializer)], properties:null)
INFO  : Completed compiling command(queryId=hive_20170112202222_7e1575c8-2e18-4333-a4e7-9d4cfa805013); Time taken: 0.319 seconds
INFO  : Executing command(queryId=hive_20170112202222_7e1575c8-2e18-4333-a4e7-9d4cfa805013): show tables
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20170112202222_7e1575c8-2e18-4333-a4e7-9d4cfa805013); Time taken: 0.236 seconds
INFO  : OK
+-----------+--+
| tab_name  |
+-----------+--+
+-----------+--+
No rows selected (1.836 seconds)


```