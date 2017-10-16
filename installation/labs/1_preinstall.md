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




[root@ip-172-31-25-204 centos]#yum install nscd
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

[root@ip-172-31-25-204 centos]#yum install ntp
Installed:
  ntp.x86_64 0:4.2.6p5-10.el6.centos.2

Dependency Installed:
  ntpdate.x86_64 0:4.2.6p5-10.el6.centos.2

Complete!

[root@ip-172-31-25-204 centos]# service ntpd start
Starting ntpd:                                             [  OK  ]
[root@ip-172-31-25-204 centos]# chkconfig ntpd on


!!!! --> wrong installation of mysql --> vm terminated and recreated !!!!





