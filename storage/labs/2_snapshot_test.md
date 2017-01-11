```
-
step 1- create dir
———

[hdfs@ip-172-30-2-157 root]$ hadoop fs -mkdir /precious
[hdfs@ip-172-30-2-157 root]$ hadoop fs -ls /
Found 4 items
drwxr-xr-x   - hdfs supergroup          0 2017-01-10 21:41 /OLGA
drwxr-xr-x   - hdfs supergroup          0 2017-01-11 01:20 /precious
drwxrwxrwt   - hdfs supergroup          0 2017-01-10 01:18 /tmp
drwxr-xr-x   - hdfs supergroup          0 2017-01-10 20:05 /user


——
step 2 - put file into HDFS
——

exit
[root@ip-172-30-2-157 precious]#  hadoop fs -put SEBC-master.zip /precious
[root@ip-172-30-2-157 precious]# hadoop fs -ls /precious
Found 1 items
-rw-r--r--   3 root supergroup     414940 2017-01-11 01:27 /precious/SEBC-master.zip


—
step 3 - enable snapshot for /precious
-
Clusters > HDFS > File Browser > [choose dir] > Enable Snapshots

——
step 4 - take a snapshot
—

Cluster > HDFS > File Browser > [select path] > [enter name] > Take Snapshot


——
step 5 - delete file
——
[hdfs@ip-172-30-2-157 precious]$ hadoop fs -rm -r -skipTrash /precious/SEBC-master.zip
Deleted /precious/SEBC-master.zip
[hdfs@ip-172-30-2-157 precious]$ hadoop fs -ls /precious
[hdfs@ip-172-30-2-157 precious]$ 


—
step 6 - restore file from a snapshot
——

Cluster > HDFS > File Browser > [select path] > restore Directory from Snapshot

[hdfs@ip-172-30-2-157 precious]$ hadoop fs -ls /precious
Found 1 items
-rw-r--r--   3 hdfs supergroup     414940 2017-01-11 01:51 /precious/SEBC-master.zip



```