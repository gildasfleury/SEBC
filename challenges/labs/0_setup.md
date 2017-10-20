AWS instances CentOS 7 (x86_64) - with Updates HVM
3.10.0-327.10.1.el7.x86_64
m3x.large

[root@ip-172-31-19-20 centos]# df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/xvda1      100G  1.1G   99G   2% /
devtmpfs        7.3G     0  7.3G   0% /dev
tmpfs           7.2G     0  7.2G   0% /dev/shm
tmpfs           7.2G   17M  7.2G   1% /run

[root@ip-172-31-16-124 centos]# df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/xvda1      100G  1.1G   99G   2% /
devtmpfs        7.3G     0  7.3G   0% /dev


[root@ip-172-31-31-254 centos]# df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/xvda1      100G  1.1G   99G   2% /
devtmpfs        7.3G     0  7.3G   0% /dev

[root@ip-172-31-21-148 centos]# df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/xvda1      100G  1.1G   99G   2% /
devtmpfs        7.3G     0  7.3G   0% /dev

[root@ip-172-31-24-153 centos]# df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/xvda1      100G  1.1G   99G   2% /
devtmpfs        7.3G     0  7.3G   0% /dev


[root@ip-172-31-19-20 centos]# yum repolist enabled
Loaded plugins: fastestmirror
Loading mirror speeds from cached hostfile
 * base: mirror.23media.de
 * extras: mirror.imt-systems.com
 * updates: ftp.antilo.de
repo id                             repo name                             status
base/7/x86_64                       CentOS-7 - Base                       9,591
extras/7/x86_64                     CentOS-7 - Extras                       227
updates/7/x86_64                    CentOS-7 - Updates                      741
repolist: 10,559


[root@ip-172-31-16-124 centos]# yum repolist enabled
Loaded plugins: fastestmirror
Loading mirror speeds from cached hostfile
 * base: mirror.23media.de
 * extras: ftp.antilo.de
 * updates: ftp.antilo.de
repo id                               repo name                               status
base/7/x86_64                         CentOS-7 - Base                         9,591
extras/7/x86_64                       CentOS-7 - Extras                         227
updates/7/x86_64                      CentOS-7 - Updates                        741
repolist: 10,559

[root@ip-172-31-31-254 centos]# yum repolist enabled
Loaded plugins: fastestmirror
Loading mirror speeds from cached hostfile
 * base: mirror.wiuwiu.de
 * extras: mirror.imt-systems.com
 * updates: ftp.antilo.de
repo id                               repo name                                status
base/7/x86_64                         CentOS-7 - Base                          9,591
extras/7/x86_64                       CentOS-7 - Extras                          227
updates/7/x86_64                      CentOS-7 - Updates                         741
repolist: 10,559


[root@ip-172-31-21-148 centos]# yum repolist enabled
Loaded plugins: fastestmirror
Loading mirror speeds from cached hostfile
 * base: mirror.23media.de
 * extras: mirror.imt-systems.com
 * updates: mirror.ratiokontakt.de
repo id                               repo name                                status
base/7/x86_64                         CentOS-7 - Base                          9,591
extras/7/x86_64                       CentOS-7 - Extras                          227
updates/7/x86_64                      CentOS-7 - Updates                         741
repolist: 10,559

[root@ip-172-31-24-153 centos]# yum repolist enabled
Loaded plugins: fastestmirror
Loading mirror speeds from cached hostfile
 * base: mirror.23media.de
 * extras: mirror.imt-systems.com
 * updates: mirror.eu.oneandone.net
repo id                                repo name                                status
base/7/x86_64                          CentOS-7 - Base                          9,591
extras/7/x86_64                        CentOS-7 - Extras                          227
updates/7/x86_64                       CentOS-7 - Updates                         741
repolist: 10,559
[root@ip-172-31-24-153 centos]#



[root@ip-172-31-19-20 centos]# cat /etc/passwd|egrep "ernest|siwi"
ernest:x:2000:2001::/home/ernest:/bin/bash
siwicki:x:3000:2002::/home/siwicki:/bin/bash
[root@ip-172-31-19-20 centos]# cat /etc/group|egrep "usa|emea"
usa:x:2001:
emea:x:2002:


[root@ip-172-31-16-124 centos]# cat /etc/group|egrep "usa|emea"
usa:x:2001:
emea:x:2002:
[root@ip-172-31-16-124 centos]# cat /etc/passwd|egrep "ernest|siwi"
ernest:x:2000:2000::/home/ernest:/bin/bash
siwicki:x:3000:2002::/home/siwicki:/bin/bash


[root@ip-172-31-31-254 centos]# cat /etc/group|egrep "usa|emea"
usa:x:1001:
emea:x:1002:
[root@ip-172-31-31-254 centos]# cat /etc/passwd|egrep "ernest|siwi"
ernest:x:2000:1001::/home/ernest:/bin/bash
siwicki:x:3000:1002::/home/siwicki:/bin/bash


[root@ip-172-31-21-148 centos]# cat /etc/group|egrep "usa|emea"
usa:x:1001:
emea:x:1002:
[root@ip-172-31-21-148 centos]# cat /etc/passwd|egrep "ernest|siwi"
ernest:x:2000:1001::/home/ernest:/bin/bash
siwicki:x:3000:1002::/home/siwicki:/bin/bash


[root@ip-172-31-24-153 centos]# cat /etc/group|egrep "usa|emea"
usa:x:1001:
emea:x:1002:
[root@ip-172-31-24-153 centos]# cat /etc/passwd|egrep "ernest|siwi"
ernest:x:2000:1001::/home/ernest:/bin/bash
siwicki:x:3000:1002::/home/siwicki:/bin/bash
















