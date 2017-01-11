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
 [hdfs@ip-172-30-2-157 root]$  hadoop jar  /opt/cloudera/parcels/CDH-5.8.2-1.cdh5.8.2.p0.3/jars/hadoop-examples.jar  teragen -help
teragen <num rows> <output dir>

----
Step 4 - Generate 10GB data : 100,000,000 here is a <number of 100-byte rows>, num. of mappers=4, blocksize=32MB (33554432 bytes)

NOTES: available space on alley 3 datanodes is 20 GB > I can generate only ~ 6GB dataset instead of 10 GB; tried 6 GB and 5 GB -FAILED
Finally, create  dataset of size 4 GB - SUCCESS
But down the road I would use terasort, which ill take another 4 GB of HDFS space, which I do have, so
1. Generate 2 GB file
2. run terasort
------
 [hdfs@ip-172-30-2-157 root]$time sudo -u hdfs hadoop jar   /opt/cloudera/parcels/CDH-5.8.2-1.cdh5.8.2.p0.3/jars/hadoop-examples.jar  teragen -D mapreduce.job.maps=4 -D dfs.blocksize=33554432 20000000 /user/ona2/teragen2  

17/01/11 00:56:03 INFO mapreduce.Job:  map 100% reduce 0%
17/01/11 00:56:03 INFO mapreduce.Job: Job job_1484011018527_0009 completed successfully
17/01/11 00:56:03 INFO mapreduce.Job: Counters: 31
	File System Counters
		FILE: Number of bytes read=0
		FILE: Number of bytes written=485952
		FILE: Number of read operations=0
		FILE: Number of large read operations=0
		FILE: Number of write operations=0
		HDFS: Number of bytes read=337
		HDFS: Number of bytes written=2000000000
		HDFS: Number of read operations=16
		HDFS: Number of large read operations=0
		HDFS: Number of write operations=8
	Job Counters 
		Launched map tasks=4
		Other local map tasks=4
		Total time spent by all maps in occupied slots (ms)=80724
		Total time spent by all reduces in occupied slots (ms)=0
		Total time spent by all map tasks (ms)=80724
		Total vcore-seconds taken by all map tasks=80724
		Total megabyte-seconds taken by all map tasks=82661376
	Map-Reduce Framework
		Map input records=20000000
		Map output records=20000000
		Input split bytes=337
		Spilled Records=0
		Failed Shuffles=0
		Merged Map outputs=0
		GC time elapsed (ms)=795
		CPU time spent (ms)=47000
		Physical memory (bytes) snapshot=1509552128
		Virtual memory (bytes) snapshot=6360453120
		Total committed heap usage (bytes)=2301624320
	org.apache.hadoop.examples.terasort.TeraGen$Counters
		CHECKSUM=42957274697559007
	File Input Format Counters 
		Bytes Read=0
	File Output Format Counters 
		Bytes Written=2000000000

real	0m31.710s
user	0m4.769s
sys	0m0.266s

——
step 5 - check dataset in HDFS
——
[hdfs@ip-172-30-2-157 root]$ hadoop fs -ls /user/ona2/teragen2
Found 5 items
-rw-r--r--   3 hdfs supergroup          0 2017-01-11 01:00 /user/ona2/teragen2/_SUCCESS
-rw-r--r--   3 hdfs supergroup  500000000 2017-01-11 01:00 /user/ona2/teragen2/part-m-00000
-rw-r--r--   3 hdfs supergroup  500000000 2017-01-11 01:00 /user/ona2/teragen2/part-m-00001
-rw-r--r--   3 hdfs supergroup  500000000 2017-01-11 01:00 /user/ona2/teragen2/part-m-00002
-rw-r--r--   3 hdfs supergroup  500000000 2017-01-11 01:00 /user/ona2/teragen2/part-m-00003


——
step 6 - run terasort on generated data
———
[hdfs@ip-172-30-2-157 root]$ time  hadoop jar   /opt/cloudera/parcels/CDH-5.8.2-1.cdh5.8.2.p0.3/jars/hadoop-examples.jar  terasort  -D mapreduce.job.maps=4 -D dfs.blocksize=33554432   /user/ona2/teragen2 /user/ona2/terasort2

……..
17/01/11 01:05:22 INFO terasort.TeraSort: done

real	1m6.196s
user	0m6.594s
sys	0m0.337s

——
step 7 - check terasort results
——
[hdfs@ip-172-30-2-157 root]$ hadoop fs -ls /user/ona2/terasort2
Found 14 items
-rw-r--r--   1 hdfs supergroup          0 2017-01-11 01:05 /user/ona2/terasort2/_SUCCESS
-rw-r--r--  10 hdfs supergroup        121 2017-01-11 01:04 /user/ona2/terasort2/_partition.lst
-rw-r--r--   1 hdfs supergroup  169872800 2017-01-11 01:05 /user/ona2/terasort2/part-r-00000
-rw-r--r--   1 hdfs supergroup  165970400 2017-01-11 01:05 /user/ona2/terasort2/part-r-00001
-rw-r--r--   1 hdfs supergroup  166407100 2017-01-11 01:05 /user/ona2/terasort2/part-r-00002
-rw-r--r--   1 hdfs supergroup  166601100 2017-01-11 01:05 /user/ona2/terasort2/part-r-00003
-rw-r--r--   1 hdfs supergroup  165377900 2017-01-11 01:05 /user/ona2/terasort2/part-r-00004
-rw-r--r--   1 hdfs supergroup  166560900 2017-01-11 01:05 /user/ona2/terasort2/part-r-00005
-rw-r--r--   1 hdfs supergroup  164310400 2017-01-11 01:05 /user/ona2/terasort2/part-r-00006
-rw-r--r--   1 hdfs supergroup  165795300 2017-01-11 01:05 /user/ona2/terasort2/part-r-00007
-rw-r--r--   1 hdfs supergroup  168019100 2017-01-11 01:05 /user/ona2/terasort2/part-r-00008
-rw-r--r--   1 hdfs supergroup  164341300 2017-01-11 01:05 /user/ona2/terasort2/part-r-00009
-rw-r--r--   1 hdfs supergroup  166936300 2017-01-11 01:05 /user/ona2/terasort2/part-r-00010
-rw-r--r--   1 hdfs supergroup  169807400 2017-01-11 01:05 /user/ona2/terasort2/part-r-00011

```