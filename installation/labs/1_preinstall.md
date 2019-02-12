1) Check vm.swappiness on all your nodes 

[root@ip-172-31-34-49 ~]# cat /etc/sysctl.conf
# sysctl settings are defined through files in
# /usr/lib/sysctl.d/, /run/sysctl.d/, and /etc/sysctl.d/.
#
# Vendors settings live in /usr/lib/sysctl.d/.
# To override a whole file, create a new file with the same in
# /etc/sysctl.d/ and put new settings there. To override
# only specific settings, add a file with a lexically later
# name in /etc/sysctl.d/ and put new settings there.
#
# For more information, see sysctl.conf(5) and sysctl.d(5).
vm.swappiness = 1

[root@ip-172-31-43-192 ec2-user]# cat /etc/sysctl.conf
# sysctl settings are defined through files in
# /usr/lib/sysctl.d/, /run/sysctl.d/, and /etc/sysctl.d/.
#
# Vendors settings live in /usr/lib/sysctl.d/.
# To override a whole file, create a new file with the same in
# /etc/sysctl.d/ and put new settings there. To override
# only specific settings, add a file with a lexically later
# name in /etc/sysctl.d/ and put new settings there.
#
# For more information, see sysctl.conf(5) and sysctl.d(5).
vm.swappiness = 1

[root@ip-172-31-36-36 ec2-user]# cat /etc/sysctl.conf
# sysctl settings are defined through files in
# /usr/lib/sysctl.d/, /run/sysctl.d/, and /etc/sysctl.d/.
#
# Vendors settings live in /usr/lib/sysctl.d/.
# To override a whole file, create a new file with the same in
# /etc/sysctl.d/ and put new settings there. To override
# only specific settings, add a file with a lexically later
# name in /etc/sysctl.d/ and put new settings there.
#
# For more information, see sysctl.conf(5) and sysctl.d(5).
vm.swappiness = 1

[root@ip-172-31-38-139 ec2-user]# cat /etc/sysctl.conf
# sysctl settings are defined through files in
# /usr/lib/sysctl.d/, /run/sysctl.d/, and /etc/sysctl.d/.
#
# Vendors settings live in /usr/lib/sysctl.d/.
# To override a whole file, create a new file with the same in
# /etc/sysctl.d/ and put new settings there. To override
# only specific settings, add a file with a lexically later
# name in /etc/sysctl.d/ and put new settings there.
#
# For more information, see sysctl.conf(5) and sysctl.d(5).
vm.swappiness = 1

[root@ip-172-31-36-148 ec2-user]# cat /etc/sysctl.conf
# sysctl settings are defined through files in
# /usr/lib/sysctl.d/, /run/sysctl.d/, and /etc/sysctl.d/.
#
# Vendors settings live in /usr/lib/sysctl.d/.
# To override a whole file, create a new file with the same in
# /etc/sysctl.d/ and put new settings there. To override
# only specific settings, add a file with a lexically later
# name in /etc/sysctl.d/ and put new settings there.
#
# For more information, see sysctl.conf(5) and sysctl.d(5).
vm.swappiness = 1

2) Show the mount attributes of your volume(s)

[root@ip-172-31-36-148 ec2-user]# cat /proc/mounts
rootfs / rootfs rw 0 0
sysfs /sys sysfs rw,seclabel,nosuid,nodev,noexec,relatime 0 0
proc /proc proc rw,nosuid,nodev,noexec,relatime 0 0
devtmpfs /dev devtmpfs rw,seclabel,nosuid,size=7873776k,nr_inodes=1968444,mode=755 0 0
securityfs /sys/kernel/security securityfs rw,nosuid,nodev,noexec,relatime 0 0
tmpfs /dev/shm tmpfs rw,seclabel,nosuid,nodev 0 0
devpts /dev/pts devpts rw,seclabel,nosuid,noexec,relatime,gid=5,mode=620,ptmxmode=000 0 0
tmpfs /run tmpfs rw,seclabel,nosuid,nodev,mode=755 0 0
tmpfs /sys/fs/cgroup tmpfs ro,seclabel,nosuid,nodev,noexec,mode=755 0 0
cgroup /sys/fs/cgroup/systemd cgroup rw,seclabel,nosuid,nodev,noexec,relatime,xattr,release_agent=/usr/lib/systemd/systemd-cgroups-agent,name=systemd 0 0
pstore /sys/fs/pstore pstore rw,nosuid,nodev,noexec,relatime 0 0
cgroup /sys/fs/cgroup/pids cgroup rw,seclabel,nosuid,nodev,noexec,relatime,pids 0 0
cgroup /sys/fs/cgroup/cpuset cgroup rw,seclabel,nosuid,nodev,noexec,relatime,cpuset 0 0
cgroup /sys/fs/cgroup/blkio cgroup rw,seclabel,nosuid,nodev,noexec,relatime,blkio 0 0
cgroup /sys/fs/cgroup/memory cgroup rw,seclabel,nosuid,nodev,noexec,relatime,memory 0 0
cgroup /sys/fs/cgroup/net_cls,net_prio cgroup rw,seclabel,nosuid,nodev,noexec,relatime,net_prio,net_cls 0 0
cgroup /sys/fs/cgroup/hugetlb cgroup rw,seclabel,nosuid,nodev,noexec,relatime,hugetlb 0 0
cgroup /sys/fs/cgroup/cpu,cpuacct cgroup rw,seclabel,nosuid,nodev,noexec,relatime,cpuacct,cpu 0 0
cgroup /sys/fs/cgroup/perf_event cgroup rw,seclabel,nosuid,nodev,noexec,relatime,perf_event 0 0
cgroup /sys/fs/cgroup/devices cgroup rw,seclabel,nosuid,nodev,noexec,relatime,devices 0 0
cgroup /sys/fs/cgroup/freezer cgroup rw,seclabel,nosuid,nodev,noexec,relatime,freezer 0 0
configfs /sys/kernel/config configfs rw,relatime 0 0
/dev/nvme0n1p2 / xfs rw,seclabel,relatime,attr2,inode64,noquota 0 0
selinuxfs /sys/fs/selinux selinuxfs rw,relatime 0 0
debugfs /sys/kernel/debug debugfs rw,relatime 0 0
systemd-1 /proc/sys/fs/binfmt_misc autofs rw,relatime,fd=27,pgrp=1,timeout=0,minproto=5,maxproto=5,direct,pipe_ino=13045 0 0
mqueue /dev/mqueue mqueue rw,seclabel,relatime 0 0
hugetlbfs /dev/hugepages hugetlbfs rw,seclabel,relatime 0 0
tmpfs /run/user/0 tmpfs rw,seclabel,nosuid,nodev,relatime,size=1579196k,mode=700 0 0
tmpfs /run/user/1000 tmpfs rw,seclabel,nosuid,nodev,relatime,size=1579196k,mode=700,uid=1000,gid=1000 0 0


3) If you have ext-based volumes, list the reserve space setting 
[root@edge zookeeper]# lsblk
NAME        MAJ:MIN RM SIZE RO TYPE MOUNTPOINT
nvme0n1     259:1    0  25G  0 disk
├─nvme0n1p1 259:2    0   1M  0 part
└─nvme0n1p2 259:3    0  25G  0 part /
nvme1n1     259:0    0  25G  0 disk /clouderadata
[root@edge zookeeper]# df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/nvme0n1p2   25G   15G   11G  57% /
devtmpfs        7.6G     0  7.6G   0% /dev
tmpfs           7.6G     0  7.6G   0% /dev/shm
tmpfs           7.6G  8.6M  7.6G   1% /run
tmpfs           7.6G     0  7.6G   0% /sys/fs/cgroup
tmpfs           1.6G     0  1.6G   0% /run/user/997
tmpfs           1.6G     0  1.6G   0% /run/user/0
cm_processes    7.6G   15M  7.6G   1% /run/cloudera-scm-agent/process
tmpfs           1.6G     0  1.6G   0% /run/user/1000
/dev/nvme1n1     25G  434M   23G   2% /clouderadata


4) Disable transparent hugepage support
[root@ip-172-31-34-49 ec2-user]# cat /etc/rc.d/rc.local
#!/bin/bash
# THIS FILE IS ADDED FOR COMPATIBILITY PURPOSES
#
# It is highly advisable to create own systemd services or udev rules
# to run scripts during boot instead of using this file.
#
# In contrast to previous versions due to parallel execution during boot
# this script will NOT be run after all other services.
#
# Please note that you must run 'chmod +x /etc/rc.d/rc.local' to ensure
# that this script will be executed during boot.

touch /var/lock/subsys/local
echo never > /sys/kernel/mm/transparent_hugepage/enabled
echo never > /sys/kernel/mm/transparent_hugepage/defrag

5) List your network interface configuration

[root@ip-172-31-34-49 ec2-user]# netstat -l
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State
tcp        0      0 0.0.0.0:ssh             0.0.0.0:*               LISTEN
tcp        0      0 localhost:smtp          0.0.0.0:*               LISTEN
tcp6       0      0 [::]:ssh                [::]:*                  LISTEN
tcp6       0      0 localhost:smtp          [::]:*                  LISTEN
udp        0      0 localhost:323           0.0.0.0:*
udp        0      0 0.0.0.0:bootpc          0.0.0.0:*
udp6       0      0 localhost:323           [::]:*
Active UNIX domain sockets (only servers)
Proto RefCnt Flags       Type       State         I-Node   Path
unix  2      [ ACC ]     STREAM     LISTENING     16080    public/flush
unix  2      [ ACC ]     STREAM     LISTENING     16095    public/showq
unix  2      [ ACC ]     STREAM     LISTENING     10513    /run/systemd/journal/stdout
unix  2      [ ACC ]     STREAM     LISTENING     13844    /var/run/NetworkManager/private-dhcp
unix  2      [ ACC ]     STREAM     LISTENING     16058    public/qmgr
unix  2      [ ACC ]     STREAM     LISTENING     9049     /run/systemd/private
unix  2      [ ACC ]     STREAM     LISTENING     16062    private/tlsmgr
unix  2      [ ACC ]     STREAM     LISTENING     16065    private/rewrite
unix  2      [ ACC ]     STREAM     LISTENING     16068    private/bounce
unix  2      [ ACC ]     STREAM     LISTENING     16055    public/cleanup
unix  2      [ ACC ]     SEQPACKET  LISTENING     9102     /run/udev/control
unix  2      [ ACC ]     STREAM     LISTENING     13223    /run/dbus/system_bus_socket
unix  2      [ ACC ]     STREAM     LISTENING     16071    private/defer
unix  2      [ ACC ]     STREAM     LISTENING     16074    private/trace
unix  2      [ ACC ]     STREAM     LISTENING     16077    private/verify
unix  2      [ ACC ]     STREAM     LISTENING     16083    private/proxymap
unix  2      [ ACC ]     STREAM     LISTENING     16086    private/proxywrite
unix  2      [ ACC ]     STREAM     LISTENING     16089    private/smtp
unix  2      [ ACC ]     STREAM     LISTENING     16092    private/relay
unix  2      [ ACC ]     STREAM     LISTENING     16098    private/error
unix  2      [ ACC ]     STREAM     LISTENING     16101    private/retry
unix  2      [ ACC ]     STREAM     LISTENING     16104    private/discard
unix  2      [ ACC ]     STREAM     LISTENING     16107    private/local
unix  2      [ ACC ]     STREAM     LISTENING     16110    private/virtual
unix  2      [ ACC ]     STREAM     LISTENING     16113    private/lmtp
unix  2      [ ACC ]     STREAM     LISTENING     16116    private/anvil
unix  2      [ ACC ]     STREAM     LISTENING     16119    private/scache
unix  2      [ ACC ]     STREAM     LISTENING     16051    public/pickup

6) Show that forward and reverse host lookups are correctly resolved
[root@ip-172-31-34-49 ec2-user]# getent hosts
127.0.0.1       localhost localhost.localdomain localhost4 localhost4.localdomain4
127.0.0.1       localhost localhost.localdomain localhost6 localhost6.localdomain6
172.31.34.49    edge.cloudera.es edge
172.31.43.192   master1.cloudera.es master1
172.31.36.36    master2.cloudera.es master2
172.31.38.139   worker1.cloudera.es worker1
172.31.36.148   worker2.cloudera.es worker2

7) Show the nscd service is running
[root@ip-172-31-34-49 ec2-user]# systemctl status nscd.service
● nscd.service - Name Service Cache Daemon
   Loaded: loaded (/usr/lib/systemd/system/nscd.service; enabled; vendor preset: disabled)
   Active: active (running) since Mon 2019-02-11 14:00:22 UTC; 13s ago
 Main PID: 1415 (nscd)
   CGroup: /system.slice/nscd.service
           └─1415 /usr/sbin/nscd

Feb 11 14:00:22 edge.cloudera.es nscd[1415]: 1415 monitoring file `/etc/hosts` (4)
Feb 11 14:00:22 edge.cloudera.es nscd[1415]: 1415 monitoring directory `/etc` (2)
Feb 11 14:00:22 edge.cloudera.es nscd[1415]: 1415 monitoring file `/etc/resolv.conf` (5)
Feb 11 14:00:22 edge.cloudera.es nscd[1415]: 1415 monitoring directory `/etc` (2)
Feb 11 14:00:22 edge.cloudera.es nscd[1415]: 1415 monitoring file `/etc/services` (6)
Feb 11 14:00:22 edge.cloudera.es nscd[1415]: 1415 monitoring directory `/etc` (2)
Feb 11 14:00:22 edge.cloudera.es nscd[1415]: 1415 disabled inotify-based monitoring for file `/etc/netgroup': ...ctory
Feb 11 14:00:22 edge.cloudera.es nscd[1415]: 1415 stat failed for file `/etc/netgroup'; will try again later: ...ctory
Feb 11 14:00:22 edge.cloudera.es nscd[1415]: 1415 Access Vector Cache (AVC) started
Feb 11 14:00:22 edge.cloudera.es systemd[1]: Started Name Service Cache Daemon.
Hint: Some lines were ellipsized, use -l to show in full.

8)Show the ntpd service is running
.
[root@ip-172-31-34-49 ec2-user]# systemctl status ntpd
● ntpd.service - Network Time Service
   Loaded: loaded (/usr/lib/systemd/system/ntpd.service; enabled; vendor preset: disabled)
   Active: active (running) since Mon 2019-02-11 14:04:52 UTC; 7s ago
 Main PID: 1535 (ntpd)
   CGroup: /system.slice/ntpd.service
           └─1535 /usr/sbin/ntpd -u ntp:ntp -g

Feb 11 14:04:52 edge.cloudera.es ntpd[1535]: Listen and drop on 1 v6wildcard :: UDP 123
Feb 11 14:04:52 edge.cloudera.es ntpd[1535]: Listen normally on 2 lo 127.0.0.1 UDP 123
Feb 11 14:04:52 edge.cloudera.es ntpd[1535]: Listen normally on 3 eth0 172.31.34.49 UDP 123
Feb 11 14:04:52 edge.cloudera.es ntpd[1535]: Listen normally on 4 lo ::1 UDP 123
Feb 11 14:04:52 edge.cloudera.es ntpd[1535]: Listen normally on 5 eth0 fe80::c2e:4dff:fef1:9172 UDP 123
Feb 11 14:04:52 edge.cloudera.es ntpd[1535]: Listening on routing socket on fd #22 for interface updates
Feb 11 14:04:53 edge.cloudera.es ntpd[1535]: 0.0.0.0 c016 06 restart
Feb 11 14:04:53 edge.cloudera.es ntpd[1535]: 0.0.0.0 c012 02 freq_set kernel 0.000 PPM
Feb 11 14:04:53 edge.cloudera.es ntpd[1535]: 0.0.0.0 c011 01 freq_not_set
Feb 11 14:04:59 edge.cloudera.es ntpd[1535]: 0.0.0.0 c614 04 freq_mode





