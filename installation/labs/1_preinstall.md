[centos@ip-172-31-25-204 ~]$ sysctl vm.swappiness
vm.swappiness = 60
[centos@ip-172-31-25-204 ~]$ sudo sysctl vm.swappiness=1
vm.swappiness = 1
[centos@ip-172-31-25-204 ~]$ sysctl vm.swappiness
vm.swappiness = 1
cat >>/etc/rc.d/rc.local <<EOF
sysctl vm.swappiness=1
echo "vm.swappiness = 1" >> /etc/sysctl.conf
echo 1 > /proc/sys/vm/swappiness
EOF


[centos@ip-172-31-25-204 ~]$ cat /etc/fstab

#
# /etc/fstab
# Created by anaconda on Mon May  1 18:49:36 2017
#
# Accessible filesystems, by reference, are maintained under '/dev/disk'
# See man pages fstab(5), findfs(8), mount(8) and/or blkid(8) for more info
#
UUID=b48e599f-bd30-4876-9a63-ecd015ba7454 /                       ext4    defaults        1 1
tmpfs                   /dev/shm                tmpfs   defaults        0 0
devpts                  /dev/pts                devpts  gid=5,mode=620  0 0
sysfs                   /sys                    sysfs   defaults        0 0
proc                    /proc                   proc    defaults        0 0


[root@ip-172-31-25-204 centos]# tune2fs -l UUID=b48e599f-bd30-4876-9a63-ecd015ba7454 |grep Reserv
Reserved block count:     104844
Reserved GDT blocks:      511
Reserved blocks uid:      0 (user root)
Reserved blocks gid:      0 (group root)


[root@ip-172-31-25-204 centos]# echo never > /sys/kernel/mm/transparent_hugepage/enabled
[root@ip-172-31-25-204 centos]# echo never > /sys/kernel/mm/transparent_hugepage/defrag
cat >>/etc/rc.d/rc.local <<EOF
# Remove THP feature (perfs issues)
if test -f /sys/kernel/mm/transparent_hugepage/enabled; then
   echo never > /sys/kernel/mm/transparent_hugepage/enabled
fi
if test -f /sys/kernel/mm/transparent_hugepage/defrag; then
   echo never > /sys/kernel/mm/transparent_hugepage/defrag
fi
EOF


yum install -y bind-utils

[root@ip-172-31-25-204 centos]# nslookup ip-172-31-25-204
Server:         172.31.0.2
Address:        172.31.0.2#53

Non-authoritative answer:
Name:   ip-172-31-25-204.eu-central-1.compute.internal
Address: 172.31.25.204

[root@ip-172-31-25-204 centos]# nslookup 172-31-25-204
Server:         172.31.0.2
Address:        172.31.0.2#53

** server can't find 172-31-25-204: NXDOMAIN

[root@ip-172-31-25-204 centos]# nslookup 172.31.25.204
Server:         172.31.0.2
Address:        172.31.0.2#53

Non-authoritative answer:
204.25.31.172.in-addr.arpa      name = ip-172-31-25-204.eu-central-1.compute.internal.
Authoritative answers can be found from:




[root@ip-172-31-25-204 centos]#yum -y install nscd
Installed:
  nscd.x86_64 0:2.12-1.209.el6_9.2
Dependency Updated:
  glibc.x86_64 0:2.12-1.209.el6_9.2                                                          glibc-common.x86_64 0:2.12-1.209.el6_9.2

Complete!
[root@ip-172-31-25-204 centos]# chkconfig nscd  on
[root@ip-172-31-25-204 centos]# ps -ef|grep nscd
root      5205  1597  0 13:51 pts/0    00:00:00 grep nscd
[root@ip-172-31-25-204 centos]# service nscd start
Starting nscd:                                             [  OK  ]
[root@ip-172-31-25-204 centos]# ps -ef|grep nscd
nscd      5222     1  0 13:51 ?        00:00:00 /usr/sbin/nscd
root      5236  1597  0 13:51 pts/0    00:00:00 grep nscd

[root@ip-172-31-25-204 centos]#yum -y install ntp
Installed:
  ntp.x86_64 0:4.2.6p5-10.el6.centos.2

Dependency Installed:
  ntpdate.x86_64 0:4.2.6p5-10.el6.centos.2

Complete!

[root@ip-172-31-25-204 centos]# service ntpd start
Starting ntpd:                                             [  OK  ]
[root@ip-172-31-25-204 centos]# chkconfig ntpd on


!!!! --> wrong installation of mysql --> vm terminated and recreated !!!!


Mysql55 repository :
yum install -y wget
wget http://repo.mysql.com/mysql-community-release-el5-5.noarch.rpm
rpm -ivh mysql-community-release-el5-5.noarch.rpm

[root@ip-172-31-43-15 yum.repos.d]# cat mysql-community.repo
[mysql-connectors-community]
name=MySQL Connectors Community
baseurl=http://repo.mysql.com/yum/mysql-connectors-community/el/5/$basearch/
enabled=1
gpgcheck=1
gpgkey=file:/etc/pki/rpm-gpg/RPM-GPG-KEY-mysql

# Enable to use MySQL 5.6
[mysql56-community]
name=MySQL 5.6 Community Server
baseurl=http://repo.mysql.com/yum/mysql-5.6-community/el/5/$basearch/
enabled=0
gpgcheck=1
gpgkey=file:/etc/pki/rpm-gpg/RPM-GPG-KEY-mysql

# Note: MySQL 5.7 is currently in development. For use at your own risk.
# Please read with sub pages: https://dev.mysql.com/doc/relnotes/mysql/5.7/en/
[mysql57-community-dmr]
name=MySQL 5.7 Community Server Development Milestone Release
baseurl=http://repo.mysql.com/yum/mysql-5.7-community/el/5/$basearch/
enabled=0
gpgcheck=1
gpgkey=file:/etc/pki/rpm-gpg/RPM-GPG-KEY-mysql


due to dependencies error, I hide this previous mysql repository

[root@ip-172-31-43-15 yum.repos.d]# mv mysql-community.repo ..
[root@ip-172-31-43-15 yum.repos.d]# yum install mysql
Installed:
  mysql.x86_64 0:5.1.73-8.el6_8

Dependency Installed:
  perl.x86_64 4:5.10.1-144.el6              perl-Module-Pluggable.x86_64 1:3.90-144.el6         perl-Pod-Escapes.x86_64 1:1.04-144.el6         perl-Pod-Simple.x86_64 1:3.13-144.el6
  perl-libs.x86_64 4:5.10.1-144.el6         perl-version.x86_64 3:0.77-144.el6

Complete!

[root@ip-172-31-43-15 yum.repos.d]# yum install mysql-server
Installed:
  mysql-server.x86_64 0:5.1.73-8.el6_8

Dependency Installed:
  perl-DBD-MySQL.x86_64 0:4.013-3.el6                                                              perl-DBI.x86_64 0:1.609-4.el6

Complete!

JDBC connector on all nodes. Download then USe of sftp of filezilla to push on all nodes.

[root@ip-172-31-43-15 yum.repos.d]# cd /home/centos
[root@ip-172-31-43-15 centos]# tar zxvf /home/centos/mysql-connector-java-5.1.44.tar.gz
...
mysql-connector-java-5.1.44/src/testsuite/ssl-test-certs/mykey.pub
mysql-connector-java-5.1.44/src/testsuite/ssl-test-certs/server-cert.pem
mysql-connector-java-5.1.44/src/testsuite/ssl-test-certs/server-key.pem
[root@ip-172-31-37-53 centos]# mkdir -p /usr/share/java/
[root@ip-172-31-37-53 centos]# cp mysql-connector-java-5.1.44/mysql-connector-java-5.1.44-bin.jar /usr/share/java/mysql-connector-java.jar


On both mysqlserver nodes :

[root@ip-172-31-37-53 centos]# /usr/bin/mysql_secure_installation




NOTE: RUNNING ALL PARTS OF THIS SCRIPT IS RECOMMENDED FOR ALL MySQL
      SERVERS IN PRODUCTION USE!  PLEASE READ EACH STEP CAREFULLY!


In order to log into MySQL to secure it, we'll need the current
password for the root user.  If you've just installed MySQL, and
you haven't set the root password yet, the password will be blank,
so you should just press enter here.

Enter current password for root (enter for none):
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: YES)
Enter current password for root (enter for none):
OK, successfully used password, moving on...

Setting the root password ensures that nobody can log into the MySQL
root user without the proper authorisation.

Set root password? [Y/n] cloudera
New password:
Re-enter new password:
Sorry, passwords do not match.

New password:
Re-enter new password:
Password updated successfully!
Reloading privilege tables..
 ... Success!


By default, a MySQL installation has an anonymous user, allowing anyone
to log into MySQL without having to have a user account created for
them.  This is intended only for testing, and to make the installation
go a bit smoother.  You should remove them before moving into a
production environment.

Remove anonymous users? [Y/n] Y
 ... Success!

Normally, root should only be allowed to connect from 'localhost'.  This
ensures that someone cannot guess at the root password from the network.

Disallow root login remotely? [Y/n] Y
 ... Success!

By default, MySQL comes with a database named 'test' that anyone can
access.  This is also intended only for testing, and should be removed
before moving into a production environment.

Remove test database and access to it? [Y/n] Y
 - Dropping test database...
 ... Success!
 - Removing privileges on test database...
 ... Success!

Reloading the privilege tables will ensure that all changes made so far
will take effect immediately.

Reload privilege tables now? [Y/n] Y
 ... Success!

Cleaning up...


[root@ip-172-31-37-53 centos]# service mysqld restart
Stopping mysqld:                                           [  OK  ]
Starting mysqld:                                           [  OK  ]



All done!  If you've completed all of the above steps, your MySQL
installation should now be secure.

Thanks for using MySQL!

[root@ip-172-31-37-53 centos]# service mysqld restart
Stopping mysqld:                                           [  OK  ]
Starting mysqld:                                           [  OK  ]
[root@ip-172-31-37-53 centos]#
[root@ip-172-31-37-53 centos]#
[root@ip-172-31-37-53 centos]#
[root@ip-172-31-37-53 centos]# find / -name my.cn
[root@ip-172-31-37-53 centos]# find / -name my.cnf
/etc/my.cnf

[root@ip-172-31-37-53 centos]# cp /etc/my.cnf /etc/my.cnf.ORIG
[root@ip-172-31-37-53 centos]# vi /etc/my.cnf
[root@ip-172-31-37-53 centos]# service mysqld stop
Stopping mysqld:                                           [  OK  ]


[root@ip-172-31-37-53 centos]# vi /etc/my.cnf
[root@ip-172-31-37-53 centos]# cat /etc/my.cnf
[mysqld]
datadir=/var/lib/mysql
socket=/var/lib/mysql/mysql.sock
user=mysql
# Disabling symbolic-links is recommended to prevent assorted security risks
symbolic-links=0
log-bin=mysql-bin
server-id=1
innodb_flush_log_at_trx_commit=1
sync_binlog=1

[mysqld_safe]
log-error=/var/log/mysqld.log
pid-file=/var/run/mysqld/mysqld.pid
[root@ip-172-31-37-53 centos]# service mysqld restart
Stopping mysqld:                                           [  OK  ]
Starting mysqld:                                           [  OK  ]
[root@ip-172-31-37-53 centos]# mysql -u root -p





[root@ip-172-31-43-15 centos]# nslookup ip-172-31-43-15
Server:         172.31.0.2
Address:        172.31.0.2#53

Non-authoritative answer:
Name:   ip-172-31-43-15.eu-central-1.compute.internal
Address: 172.31.43.15


On SQL master node :
Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

mysql>  GRANT REPLICATION SLAVE ON *.* TO 'root'@'ip-172-31-43-15.eu-central-1.compute.internal' IDENTIFIED BY 'cloudera';
Query OK, 0 rows affected (0.01 sec)

mysql> SET GLOBAL binlog_format = 'ROW';
Query OK, 0 rows affected (0.00 sec)

mysql> FLUSH TABLES WITH READ LOCK;
Query OK, 0 rows affected (0.00 sec)



second master terminal :
mysql> SHOW MASTER STATUS;
+------------------+----------+--------------+------------------+
| File             | Position | Binlog_Do_DB | Binlog_Ignore_DB |
+------------------+----------+--------------+------------------+
| mysql-bin.000001 |      294 |              |                  |
+------------------+----------+--------------+------------------+
1 row in set (0.00 sec)


On slave :

mysql> CHANGE MASTER TO MASTER_HOST='ip-172-31-37-53.eu-central-1.compute.internal', MASTER_USER='root', MASTER_PASSWORD='cloudera', MASTER_LOG_FILE='mysql-bin.000001', MASTER_LOG_POS=294; 
Query OK, 0 rows affected (0.02 sec)

