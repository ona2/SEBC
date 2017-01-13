```
installing MySQL 5.1 and fixing InnoDB issue (changing MYISAM engine to InnoDB)


1) [root@ip-172-30-2-251 mysql]# mysql -V
mysql  Ver 14.14 Distrib 5.1.73, for redhat-linux-gnu (x86_64) using readline 5.1

2) Change engine to innoDB:
  STEP 1:  edit my.cnf

[root@ip-172-30-2-251 mysql]#service mysql stop
[root@ip-172-30-2-251 mysql]#cat /etc/my.cnf
[mysqld]
transaction-isolation = READ-COMMITTED
# Disabling symbolic-links is recommended to prevent assorted security risks;
# to do so, uncomment this line:
# symbolic-links = 0

key_buffer_size = 32M
max_allowed_packet = 32M
thread_stack = 256K
thread_cache_size = 64
query_cache_limit = 8M
query_cache_size = 64M
query_cache_type = 1

max_connections = 550
#expire_logs_days = 10
#max_binlog_size = 100M

#log_bin should be on a disk with enough free space. Replace '/var/lib/mysql/mysql_binary_log' with an appropriate path for your system
#and chown the specified folder to the mysql user.
log_bin=/var/lib/mysql/mysql_binary_log

# For MySQL version 5.1.8 or later. For older versions, reference MySQL documentation for configuration help.
binlog_format = mixed

read_buffer_size = 2M
read_rnd_buffer_size = 16M
sort_buffer_size = 8M
join_buffer_size = 8M

# InnoDB settings
innodb_file_per_table = 1
innodb_flush_log_at_trx_commit  = 2
innodb_log_buffer_size = 64M
innodb_buffer_pool_size = 4G
innodb_thread_concurrency = 8
innodb_flush_method = O_DIRECT
innodb_log_file_size = 512M
default-storage-engine=innodb
default-table-type=innodb

[mysqld_safe]
log-error=/var/log/mysqld.log
pid-file=/var/run/mysqld/mysqld.pid

sql_mode=STRICT_ALL_TABLES


STEP 2 (mysql): 
[root@ip-172-30-2-251 mysql]# mv ib_logfile0 ib_logfile0_BACK
[root@ip-172-30-2-251 mysql]# mv ib_logfile1 ib_logfile1_BACK

STEP 3: check engine


mysql> use test;
Database changed
mysql> create table innodb_test(age int);
Query OK, 0 rows affected (0.02 sec)


mysql> show table status;
+-------------+--------+---------+------------+------+----------------+-------------+-----------------+--------------+-----------+----------------+---------------------+-------------+------------+-------------------+----------+----------------+---------+
| Name        | Engine | Version | Row_format | Rows | Avg_row_length | Data_length | Max_data_length | Index_length | Data_free | Auto_increment | Create_time         | Update_time | Check_time | Collation         | Checksum | Create_options | Comment |
+-------------+--------+---------+------------+------+----------------+-------------+-----------------+--------------+-----------+----------------+---------------------+-------------+------------+-------------------+----------+----------------+---------+
| innodb_test | InnoDB |      10 | Compact    |    0 |              0 |       16384 |               0 |            0 |         0 |           NULL | 2017-01-13 17:38:42 | NULL        | NULL       | latin1_swedish_ci |     NULL |                |         |
+-------------+--------+---------+------------+------+----------------+-------------+-----------------+--------------+-----------+----------------+---------------------+-------------+------------+-------------------+----------+----------------+---------+
1 row in set (0.00 sec)

============
copy my-slq-connector.jar to ALL nodes

scp -i bvt-aws-cloudera.pem  mysql/mysql-connector-java-5.1.38/mysql-connector-java-5.1.38-bin.jar root@172.30.2.98:/usr/share/java/mysql-connector-java.jar


====

CREATE DATABASES.

I will create database ooze  later as it requires to move my-sql-connector.jar to ooze directory. and it does not exists before i will start with CM.

mysql> show databases;
+--------------------+
| Database           |
+--------------------+
| information_schema |
| amon               |
| hue                |
| metastore          |
| mysql              |
| rman               |
| sentry             |
+--------------------+
7 rows in set (0.00 sec)



```