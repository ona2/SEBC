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

0: jdbc:hive2://ip-172-30-2-120.us-west-2.com> CREATE ROLE sentry_admin;
INFO  : Compiling command(queryId=hive_20170112202626_74e6d8cc-12e2-4779-b810-412236882a64): CREATE ROLE sentry_admin
INFO  : Semantic Analysis Completed
INFO  : Returning Hive schema: Schema(fieldSchemas:null, properties:null)
INFO  : Completed compiling command(queryId=hive_20170112202626_74e6d8cc-12e2-4779-b810-412236882a64); Time taken: 0.062 seconds
INFO  : Executing command(queryId=hive_20170112202626_74e6d8cc-12e2-4779-b810-412236882a64): CREATE ROLE sentry_admin
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20170112202626_74e6d8cc-12e2-4779-b810-412236882a64); Time taken: 0.501 seconds
INFO  : OK
No rows affected (0.578 seconds)
0: jdbc:hive2://ip-172-30-2-120.us-west-2.com> GRANT ALL ON SERVER server1 TO ROLE sentry_admin;
INFO  : Compiling command(queryId=hive_20170112203131_666a5552-e4e8-46d6-a0da-2fea83c36c5f): GRANT ALL ON SERVER server1 TO ROLE sentry_admin
INFO  : Semantic Analysis Completed
INFO  : Returning Hive schema: Schema(fieldSchemas:null, properties:null)
INFO  : Completed compiling command(queryId=hive_20170112203131_666a5552-e4e8-46d6-a0da-2fea83c36c5f); Time taken: 0.093 seconds
INFO  : Executing command(queryId=hive_20170112203131_666a5552-e4e8-46d6-a0da-2fea83c36c5f): GRANT ALL ON SERVER server1 TO ROLE sentry_admin
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20170112203131_666a5552-e4e8-46d6-a0da-2fea83c36c5f); Time taken: 0.081 seconds
INFO  : OK
No rows affected (0.189 seconds)
0: jdbc:hive2://ip-172-30-2-120.us-west-2.com> GRANT ROLE sentry_admin TO GROUP ona2;
INFO  : Compiling command(queryId=hive_20170112203131_b9d9fa2e-9109-44ee-839c-0e4cc1420f11): GRANT ROLE sentry_admin TO GROUP ona2
INFO  : Semantic Analysis Completed
INFO  : Returning Hive schema: Schema(fieldSchemas:null, properties:null)
INFO  : Completed compiling command(queryId=hive_20170112203131_b9d9fa2e-9109-44ee-839c-0e4cc1420f11); Time taken: 0.056 seconds
INFO  : Executing command(queryId=hive_20170112203131_b9d9fa2e-9109-44ee-839c-0e4cc1420f11): GRANT ROLE sentry_admin TO GROUP ona2
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20170112203131_b9d9fa2e-9109-44ee-839c-0e4cc1420f11); Time taken: 0.067 seconds
INFO  : OK
No rows affected (0.136 seconds)
0: jdbc:hive2://ip-172-30-2-120.us-west-2.com> show tables;
INFO  : Compiling command(queryId=hive_20170112203232_005fd63b-aedd-4794-a5eb-5bdcfe113dd8): show tables
INFO  : Semantic Analysis Completed
INFO  : Returning Hive schema: Schema(fieldSchemas:[FieldSchema(name:tab_name, type:string, comment:from deserializer)], properties:null)
INFO  : Completed compiling command(queryId=hive_20170112203232_005fd63b-aedd-4794-a5eb-5bdcfe113dd8); Time taken: 0.056 seconds
INFO  : Executing command(queryId=hive_20170112203232_005fd63b-aedd-4794-a5eb-5bdcfe113dd8): show tables
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20170112203232_005fd63b-aedd-4794-a5eb-5bdcfe113dd8); Time taken: 0.125 seconds
INFO  : OK
+------------+--+
|  tab_name  |
+------------+--+
| customers  |
| sample_07  |
| sample_08  |
| web_logs   |
+------------+--+
4 rows selected (0.234 seconds)


[root@ip-172-30-2-88 ~]# groupadd selector
[root@ip-172-30-2-88 ~]# groupadd inserters
[root@ip-172-30-2-88 ~]# useradd -u 1100 -g selector george
[root@ip-172-30-2-88 ~]# id -u george
1100
[root@ip-172-30-2-88 ~]# useradd -u 1200 -g inserters ferdinand
[root@ip-172-30-2-88 ~]# kadmin.local
Authenticating as principal hdfs/admin@US-WEST-2.COMPUTE.INTERNAL with password.
kadmin.local:  addprinc george
WARNING: no policy specified for george@US-WEST-2.COMPUTE.INTERNAL; defaulting to no policy
Enter password for principal "george@US-WEST-2.COMPUTE.INTERNAL": 
Re-enter password for principal "george@US-WEST-2.COMPUTE.INTERNAL": 
Principal "george@US-WEST-2.COMPUTE.INTERNAL" created.
kadmin.local:  addprinc ferdinand
WARNING: no policy specified for ferdinand@US-WEST-2.COMPUTE.INTERNAL; defaulting to no policy
Enter password for principal "ferdinand@US-WEST-2.COMPUTE.INTERNAL": 
Re-enter password for principal "ferdinand@US-WEST-2.COMPUTE.INTERNAL": 
Principal "ferdinand@US-WEST-2.COMPUTE.INTERNAL" created.
kadmin.local:  exit


[root@ip-172-30-2-88 ~]# su - ona2
[ona2@ip-172-30-2-88 ~]$ beeline
2017-01-12 20:42:36,367 WARN  [main] mapreduce.TableMapReduceUtil: The hbase-prefix-tree module jar containing PrefixTreeCodec is not present.  Continuing without it.
Beeline version 1.1.0-cdh5.9.0 by Apache Hive
beeline> !connect jdbc:hive2://ip-172-30-2-120.us-west-2.compute.internal:10000/default;principal=hive/ip-172-30-2-120@US-WEST-2.COMPUTE.INTERNAL
scan complete in 1ms
Connecting to jdbc:hive2://ip-172-30-2-120.us-west-2.compute.internal:10000/default;principal=hive/ip-172-30-2-120@US-WEST-2.COMPUTE.INTERNAL
Connected to: Apache Hive (version 1.1.0-cdh5.9.0)
Driver: Hive JDBC (version 1.1.0-cdh5.9.0)
Transaction isolation: TRANSACTION_REPEATABLE_READ
0: jdbc:hive2://ip-172-30-2-120.us-west-2.com> CREATE ROLE reads;
INFO  : Compiling command(queryId=hive_20170112204242_5332c907-f9da-4ad5-a9fb-7b8d5e2dc8c5): CREATE ROLE reads
INFO  : Semantic Analysis Completed
INFO  : Returning Hive schema: Schema(fieldSchemas:null, properties:null)
INFO  : Completed compiling command(queryId=hive_20170112204242_5332c907-f9da-4ad5-a9fb-7b8d5e2dc8c5); Time taken: 0.132 seconds
INFO  : Executing command(queryId=hive_20170112204242_5332c907-f9da-4ad5-a9fb-7b8d5e2dc8c5): CREATE ROLE reads
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20170112204242_5332c907-f9da-4ad5-a9fb-7b8d5e2dc8c5); Time taken: 0.041 seconds
INFO  : OK
No rows affected (0.228 seconds)
0: jdbc:hive2://ip-172-30-2-120.us-west-2.com> CREATE ROLE writes;
INFO  : Compiling command(queryId=hive_20170112204343_809cfd27-baed-4312-8514-af2cab47bb0f): CREATE ROLE writes
INFO  : Semantic Analysis Completed
INFO  : Returning Hive schema: Schema(fieldSchemas:null, properties:null)
INFO  : Completed compiling command(queryId=hive_20170112204343_809cfd27-baed-4312-8514-af2cab47bb0f); Time taken: 0.053 seconds
INFO  : Executing command(queryId=hive_20170112204343_809cfd27-baed-4312-8514-af2cab47bb0f): CREATE ROLE writes
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20170112204343_809cfd27-baed-4312-8514-af2cab47bb0f); Time taken: 0.024 seconds
INFO  : OK
No rows affected (0.089 seconds)


0: jdbc:hive2://ip-172-30-2-120.us-west-2.com> grant select on database default to role reads;
INFO  : Compiling command(queryId=hive_20170112204444_eb522ffd-ac74-46cf-b054-770c69e33ad5): grant select on database default to role reads
INFO  : Semantic Analysis Completed
INFO  : Returning Hive schema: Schema(fieldSchemas:null, properties:null)
INFO  : Completed compiling command(queryId=hive_20170112204444_eb522ffd-ac74-46cf-b054-770c69e33ad5); Time taken: 0.063 seconds
INFO  : Executing command(queryId=hive_20170112204444_eb522ffd-ac74-46cf-b054-770c69e33ad5): grant select on database default to role reads
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20170112204444_eb522ffd-ac74-46cf-b054-770c69e33ad5); Time taken: 0.037 seconds
INFO  : OK
No rows affected (0.113 seconds)
0: jdbc:hive2://ip-172-30-2-120.us-west-2.com> grant role reads to group selector;
INFO  : Compiling command(queryId=hive_20170112204444_a3a82fa3-371b-4c0a-874f-356989776647): grant role reads to group selector
INFO  : Semantic Analysis Completed
INFO  : Returning Hive schema: Schema(fieldSchemas:null, properties:null)
INFO  : Completed compiling command(queryId=hive_20170112204444_a3a82fa3-371b-4c0a-874f-356989776647); Time taken: 0.053 seconds
INFO  : Executing command(queryId=hive_20170112204444_a3a82fa3-371b-4c0a-874f-356989776647): grant role reads to group selector
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20170112204444_a3a82fa3-371b-4c0a-874f-356989776647); Time taken: 0.029 seconds
INFO  : OK
No rows affected (0.094 seconds)
0: jdbc:hive2://ip-172-30-2-120.us-west-2.com> show tables;
INFO  : Compiling command(queryId=hive_20170112204545_a091b91b-85f6-4ae5-a7e8-d99bddbc4cea): show tables
INFO  : Semantic Analysis Completed
INFO  : Returning Hive schema: Schema(fieldSchemas:[FieldSchema(name:tab_name, type:string, comment:from deserializer)], properties:null)
INFO  : Completed compiling command(queryId=hive_20170112204545_a091b91b-85f6-4ae5-a7e8-d99bddbc4cea); Time taken: 0.054 seconds
INFO  : Executing command(queryId=hive_20170112204545_a091b91b-85f6-4ae5-a7e8-d99bddbc4cea): show tables
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20170112204545_a091b91b-85f6-4ae5-a7e8-d99bddbc4cea); Time taken: 0.129 seconds
INFO  : OK
+------------+--+
|  tab_name  |
+------------+--+
| customers  |
| sample_07  |
| sample_08  |
| web_logs   |
+------------+--+
4 rows selected (0.237 seconds)
0: jdbc:hive2://ip-172-30-2-120.us-west-2.com> revoke all on database default from role writes;
INFO  : Compiling command(queryId=hive_20170112204545_e5edea50-267b-4213-a765-ce6a0988629a): revoke all on database default from role writes
INFO  : Semantic Analysis Completed
INFO  : Returning Hive schema: Schema(fieldSchemas:null, properties:null)
INFO  : Completed compiling command(queryId=hive_20170112204545_e5edea50-267b-4213-a765-ce6a0988629a); Time taken: 0.054 seconds
INFO  : Executing command(queryId=hive_20170112204545_e5edea50-267b-4213-a765-ce6a0988629a): revoke all on database default from role writes
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20170112204545_e5edea50-267b-4213-a765-ce6a0988629a); Time taken: 0.075 seconds
INFO  : OK
No rows affected (0.146 seconds)
0: jdbc:hive2://ip-172-30-2-120.us-west-2.com> grant select on default.sample_07 to role writes;
INFO  : Compiling command(queryId=hive_20170112204646_05204fa8-e059-4833-aaad-160995c0b42a): grant select on default.sample_07 to role writes
INFO  : Semantic Analysis Completed
INFO  : Returning Hive schema: Schema(fieldSchemas:null, properties:null)
INFO  : Completed compiling command(queryId=hive_20170112204646_05204fa8-e059-4833-aaad-160995c0b42a); Time taken: 0.056 seconds
INFO  : Executing command(queryId=hive_20170112204646_05204fa8-e059-4833-aaad-160995c0b42a): grant select on default.sample_07 to role writes
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20170112204646_05204fa8-e059-4833-aaad-160995c0b42a); Time taken: 0.037 seconds
INFO  : OK
No rows affected (0.104 seconds)
0: jdbc:hive2://ip-172-30-2-120.us-west-2.com> grant role writes to group inserters;
INFO  : Compiling command(queryId=hive_20170112204646_4e3a9df2-b872-4a2f-81c7-3a7b2b927512): grant role writes to group inserters
INFO  : Semantic Analysis Completed
INFO  : Returning Hive schema: Schema(fieldSchemas:null, properties:null)
INFO  : Completed compiling command(queryId=hive_20170112204646_4e3a9df2-b872-4a2f-81c7-3a7b2b927512); Time taken: 0.053 seconds
INFO  : Executing command(queryId=hive_20170112204646_4e3a9df2-b872-4a2f-81c7-3a7b2b927512): grant role writes to group inserters
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20170112204646_4e3a9df2-b872-4a2f-81c7-3a7b2b927512); Time taken: 0.028 seconds
INFO  : OK
No rows affected (0.094 seconds)

0: jdbc:hive2://ip-172-30-2-120.us-west-2.com> !quit
Closing: 0: jdbc:hive2://ip-172-30-2-120.us-west-2.compute.internal:10000/default;principal=hive/ip-172-30-2-120@US-WEST-2.COMPUTE.INTERNAL

[ona2@ip-172-30-2-88 ~]$ exit
logout


[root@ip-172-30-2-88 ~]# su - george
[george@ip-172-30-2-88 ~]$ kinit
Password for george@US-WEST-2.COMPUTE.INTERNAL: 
[george@ip-172-30-2-88 ~]$ beeline
2017-01-12 21:07:25,006 WARN  [main] mapreduce.TableMapReduceUtil: The hbase-prefix-tree module jar containing PrefixTreeCodec is not present.  Continuing without it.
Beeline version 1.1.0-cdh5.9.0 by Apache Hive
beeline> !connect jdbc:hive2://ip-172-30-2-120.us-west-2.compute.internal:10000/default;principal=hive/ip-172-30-2-120@US-WEST-2.COMPUTE.INTERNAL
scan complete in 1ms
Connecting to jdbc:hive2://ip-172-30-2-120.us-west-2.compute.internal:10000/default;principal=hive/ip-172-30-2-120@US-WEST-2.COMPUTE.INTERNAL
Connected to: Apache Hive (version 1.1.0-cdh5.9.0)
Driver: Hive JDBC (version 1.1.0-cdh5.9.0)
Transaction isolation: TRANSACTION_REPEATABLE_READ
0: jdbc:hive2://ip-172-30-2-120.us-west-2.com> show tables;
INFO  : Compiling command(queryId=hive_20170112210707_93296038-f0db-4d63-a85a-b81e8266ebef): show tables
INFO  : Semantic Analysis Completed
INFO  : Returning Hive schema: Schema(fieldSchemas:[FieldSchema(name:tab_name, type:string, comment:from deserializer)], properties:null)
INFO  : Completed compiling command(queryId=hive_20170112210707_93296038-f0db-4d63-a85a-b81e8266ebef); Time taken: 0.07 seconds
INFO  : Executing command(queryId=hive_20170112210707_93296038-f0db-4d63-a85a-b81e8266ebef): show tables
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20170112210707_93296038-f0db-4d63-a85a-b81e8266ebef); Time taken: 0.122 seconds
INFO  : OK
+------------+--+
|  tab_name  |
+------------+--+
| customers  |
| sample_07  |
| sample_08  |
| web_logs   |
+------------+--+
4 rows selected (0.277 seconds)
0: jdbc:hive2://ip-172-30-2-120.us-west-2.com> !quit
Closing: 0: jdbc:hive2://ip-172-30-2-120.us-west-2.compute.internal:10000/default;principal=hive/ip-172-30-2-120@US-WEST-2.COMPUTE.INTERNAL
[george@ip-172-30-2-88 ~]$ exit
logout
[root@ip-172-30-2-88 ~]# su - ferdinand
[ferdinand@ip-172-30-2-88 ~]$ kinit
Password for ferdinand@US-WEST-2.COMPUTE.INTERNAL: 
[ferdinand@ip-172-30-2-88 ~]$ beeline
2017-01-12 21:09:42,063 WARN  [main] mapreduce.TableMapReduceUtil: The hbase-prefix-tree module jar containing PrefixTreeCodec is not present.  Continuing without it.
Beeline version 1.1.0-cdh5.9.0 by Apache Hive
beeline> !connect jdbc:hive2://ip-172-30-2-120.us-west-2.compute.internal:10000/default;principal=hive/ip-172-30-2-120@US-WEST-2.COMPUTE.INTERNAL
scan complete in 2ms
Connecting to jdbc:hive2://ip-172-30-2-120.us-west-2.compute.internal:10000/default;principal=hive/ip-172-30-2-120@US-WEST-2.COMPUTE.INTERNAL
Connected to: Apache Hive (version 1.1.0-cdh5.9.0)
Driver: Hive JDBC (version 1.1.0-cdh5.9.0)
Transaction isolation: TRANSACTION_REPEATABLE_READ
0: jdbc:hive2://ip-172-30-2-120.us-west-2.com> show tables;
INFO  : Compiling command(queryId=hive_20170112211010_8b554b09-08c6-426d-8e5a-595f55201e5b): show tables
INFO  : Semantic Analysis Completed
INFO  : Returning Hive schema: Schema(fieldSchemas:[FieldSchema(name:tab_name, type:string, comment:from deserializer)], properties:null)
INFO  : Completed compiling command(queryId=hive_20170112211010_8b554b09-08c6-426d-8e5a-595f55201e5b); Time taken: 0.063 seconds
INFO  : Executing command(queryId=hive_20170112211010_8b554b09-08c6-426d-8e5a-595f55201e5b): show tables
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20170112211010_8b554b09-08c6-426d-8e5a-595f55201e5b); Time taken: 0.125 seconds
INFO  : OK
+------------+--+
|  tab_name  |
+------------+--+
| sample_07  |
+------------+--+
1 row selected (0.293 seconds)

```