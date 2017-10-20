[root@ip-172-31-19-20 centos]# hostname
ip-172-31-19-20


[root@ip-172-31-19-20 centos]# mysql --version
mysql  Ver 14.14 Distrib 5.5.58, for Linux (x86_64) using readline 5.1


mysql> show databases
    -> ;
+--------------------+
| Database           |
+--------------------+
| information_schema |
| hive               |
| hue                |
| mysql              |
| oozie              |
| performance_schema |
| rman               |
| scm                |
| sentry             |
+--------------------+
9 rows in set (0.00 sec)
