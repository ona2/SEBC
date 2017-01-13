```
[hdfs@ip-172-30-2-251 schema]$ hadoop fs -mkdir /user/vladimir
[hdfs@ip-172-30-2-251 schema]$ hadoop fs -mkdir /user/donald
[hdfs@ip-172-30-2-251 schema]$ hadoop fs -ls /user
Found 8 items
drwxr-xr-x   - hdfs   supergroup          0 2017-01-13 20:07 /user/donald
drwxr-xr-x   - hdfs   supergroup          0 2017-01-13 20:04 /user/hdfs
drwxrwxrwx   - mapred hadoop              0 2017-01-13 19:59 /user/history
drwxrwxr-t   - hive   hive                0 2017-01-13 20:00 /user/hive
drwxrwxr-x   - hue    hue                 0 2017-01-13 20:01 /user/hue
drwxr-xr-x   - ona2   ona2                0 2017-01-13 20:03 /user/ona2
drwxrwxr-x   - oozie  oozie               0 2017-01-13 20:01 /user/oozie
drwxr-xr-x   - hdfs   supergroup          0 2017-01-13 20:07 /user/vladimir


```