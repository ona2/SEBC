```

---------
Step 1 - find hadoop examples
---------
[hdfs@ip-172-30-2-157 root]$ find / -name hadoop-*examples*.jar

----
Step 2 - look for availab;e examples
----
[hdfs@ip-172-30-2-157 root]$  hadoop jar /opt/cloudera/parcels/CDH-5.8.2-1.cdh5.8.2.p0.3/jars/hadoop-examples.jar
 
 ----
 Step 3 - look at help
 ---------
 [hdfs@ip-172-30-2-157 root]$  hadoop jar /opt/cloudera/parcels/CDH-5.8.2-1.cdh5.8.2.p0.3/jars/hadoop-examples.jar  teragen -help
teragen <num rows> <output dir>

----
Step 4 - Generate 500 MB data : 5,000,000 here is a <number of 100-byte rows>
------
 hadoop jar /opt/cloudera/parcels/CDH-5.8.2-1.cdh5.8.2.p0.3/jars/hadoop-examples.jar teragen 5000000 /user/ona2/teragen

[hdfs@ip-172-30-2-157 root]$ hadoop fs -ls /user/ona2/teragen
Found 3 items
-rw-r--r--   3 hdfs supergroup          0 2017-01-10 20:05 /user/ona2/teragen/_SUCCESS
-rw-r--r--   3 hdfs supergroup  250000000 2017-01-10 20:05 /user/ona2/teragen/part-m-00000
-rw-r--r--   3 hdfs supergroup  250000000 2017-01-10 20:05 /user/ona2/teragen/part-m-00001

 ---
step 5 - test files and blocks of generated data
———
 [root@ip-172-30-2-157 ~]# hadoop fsck /user/ona2/teragen -files -blocks
DEPRECATED: Use of this script to execute hdfs command is deprecated.
Instead use the hdfs command for it.

Connecting to namenode via http://ip-172-30-2-184.us-west-2.compute.internal:50070
FSCK started by root (auth:SIMPLE) from /172.30.2.157 for path /user/ona2/teragen at Tue Jan 10 20:56:38 UTC 2017
/user/ona2/teragen <dir>
/user/ona2/teragen/_SUCCESS 0 bytes, 0 block(s):  OK

/user/ona2/teragen/part-m-00000 250000000 bytes, 2 block(s):  OK
0. BP-1976019229-172.30.2.184-1484010968522:blk_1073743640_2816 len=134217728 Live_repl=3
1. BP-1976019229-172.30.2.184-1484010968522:blk_1073743642_2818 len=115782272 Live_repl=3

/user/ona2/teragen/part-m-00001 250000000 bytes, 2 block(s):  OK
0. BP-1976019229-172.30.2.184-1484010968522:blk_1073743641_2817 len=134217728 Live_repl=3
1. BP-1976019229-172.30.2.184-1484010968522:blk_1073743643_2819 len=115782272 Live_repl=3

Status: HEALTHY
 Total size:	500000000 B
 Total dirs:	1
 Total files:	3
 Total symlinks:		0
 Total blocks (validated):	4 (avg. block size 125000000 B)
 Minimally replicated blocks:	4 (100.0 %)
 Over-replicated blocks:	0 (0.0 %)
 Under-replicated blocks:	0 (0.0 %)
 Mis-replicated blocks:		0 (0.0 %)
 Default replication factor:	3
 Average block replication:	3.0
 Corrupt blocks:		0
 Missing replicas:		0 (0.0 %)
 Number of data-nodes:		3
 Number of racks:		1
FSCK ended at Tue Jan 10 20:56:38 UTC 2017 in 2 milliseconds


The filesystem under path '/user/ona2/teragen' is HEALTHY


—
step 6   - copy data to Benjamin Cluster
——
[root@ip-172-30-2-184 ~]# sudo -u hdfs hadoop  distcp hdfs://172.30.2.184:8020/user/ona2/teragen hdfs://172.30.2.137:8020/BVT 

—
step 7 - check Benjamin Cluster
———
[root@ip-172-30-2-184 ~]# hadoop fs -ls /BVT/teragen
Found 3 items
-rw-r--r--   3 hdfs supergroup          0 2017-01-10 21:57 /BVT/teragen/_SUCCESS
-rw-r--r--   3 hdfs supergroup  250000000 2017-01-10 21:57 /BVT/teragen/part-m-00000
-rw-r--r--   3 hdfs supergroup  250000000 2017-01-10 21:57 /BVT/teragen/part-m-00001

——
step 8
——
Use BDR to copy data from Benjamin Cluster to my cluster (ona2)

Backup > Cluster >Peers:

name: andre
URL: http://35.166.208.243:7180

Backup > Replication > Create Replication

Source: Cluster 1@andre:/BVT
Destination: ona2:/user/ona2/BVT

Schedule: immediate  

SUCCESS
—

——
step 9 - check BDR job results
——
drwxr-xr-x   - hdfs supergroup          0 2017-01-10 23:23 /user/ona2/BVT/teragen
[root@ip-172-30-2-184 ~]# hdfs dfs -ls /user/ona2
Found 4 items
drwxr-xr-x   - hdfs supergroup          0 2017-01-10 23:23 /user/ona2/BVT
drwxr-xr-x   - hdfs supergroup          0 2017-01-10 20:05 /user/ona2/teragen
drwxr-xr-x   - hdfs supergroup          0 2017-01-10 20:24 /user/ona2/terasort
drwxr-xr-x   - hdfs supergroup          0 2017-01-10 20:25 /user/ona2/teravalidate
[root@ip-172-30-2-184 ~]# hdfs dfs -ls /user/ona2/BVT/teragen
Found 3 items
-rw-r--r--   3 hdfs supergroup          0 2017-01-10 21:57 /user/ona2/BVT/teragen/_SUCCESS
-rw-r--r--   3 hdfs supergroup  250000000 2017-01-10 21:57 /user/ona2/BVT/teragen/part-m-00000
-rw-r--r--   3 hdfs supergroup  250000000 2017-01-10 21:57 /user/ona2/BVT/teragen/part-m-00001

```