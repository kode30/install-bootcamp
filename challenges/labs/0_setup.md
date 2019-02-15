In the file challenges/labs/0_setup.md:

List the cloud provider you are using (AWS, GCE, Azure, CloudCat, other)
```
AWS- EC2 instances Paris region, Os: RHEL 7 
```
        
List your instances by IP address and DNS name (don't use /etc/hosts for this)
```
[root@edge ec2-user]# getent hosts
        127.0.0.1       localhost localhost.localdomain localhost4 localhost4.localdomain4
        127.0.0.1       localhost localhost.localdomain localhost6 localhost6.localdomain6
        172.31.43.80    edge.cloudera.es edge
        172.31.37.140   master1.cloudera.es master1
        172.31.35.130   master2.cloudera.es master2
        172.31.36.222   worker1.cloudera.es worker1
        172.31.42.153   worker2.cloudera.es worker2
```

List the Linux release you are using
```
[root@edge ec2-user]# hostnamectl
         Static hostname: edge.cloudera.es
               Icon name: computer-vm
                 Chassis: vm
              Machine ID: ec27bd3c15b1808f522eb3625d87d378
                 Boot ID: e48a55429f704f2ba927e2a0f440c132
          Virtualization: kvm
        Operating System: Red Hat Enterprise Linux Server 7.5 (Maipo)
             CPE OS Name: cpe:/o:redhat:enterprise_linux:7.5:GA:server
                  Kernel: Linux 3.10.0-862.el7.x86_64
            Architecture: x86-64
 ```

List the file system capacity for the first node
 ```
[root@edge ec2-user]# df -h
        Filesystem      Size  Used Avail Use% Mounted on
        /dev/nvme0n1p2  100G  1.3G   99G   2% /
        devtmpfs        7.6G     0  7.6G   0% /dev
        tmpfs           7.6G     0  7.6G   0% /dev/shm
        tmpfs           7.6G  8.5M  7.6G   1% /run
        tmpfs           7.6G     0  7.6G   0% /sys/fs/cgroup
        /dev/nvme1n1     50G   53M   47G   1% /clouderadata
        tmpfs           1.6G     0  1.6G   0% /run/user/1000
        tmpfs           1.6G     0  1.6G   0% /run/user/0
```
        
List the command and output for yum repolist enabled
```
[root@edge ec2-user]# yum repolist enabled
Loaded plugins: amazon-id, rhui-lb, search-disabled-repos
repo id                                               repo name                                                            status
rhui-REGION-client-config-server-7/x86_64             Red Hat Update Infrastructure 2.0 Client Configuration Server 7           2
rhui-REGION-rhel-server-releases/7Server/x86_64       Red Hat Enterprise Linux Server 7 (RPMs)                             23,676
rhui-REGION-rhel-server-rh-common/7Server/x86_64      Red Hat Enterprise Linux Server 7 RH Common (RPMs)                      235
repolist: 23,913
```

List the /etc/passwd entries for rocky and denali
            Do not list the entire file - only in one node
```
[root@edge ec2-user]# cat /etc/passwd | grep rocky
rocky:x:3800:1002::/home/rocky:/bin/bash

[root@edge ec2-user]# cat /etc/passwd | grep denali
denali:x:3900:1001::/home/denali:/bin/bash
```
List the /etc/group entries for alaska and colorado
            Do not list the entire file - only in one node
```
[root@edge ec2-user]# cat /etc/group | grep alask
alaska:x:1001:
[root@edge ec2-user]# cat /etc/group | grep colorado
colorado:x:1002:
```

List the output of the following commands:
            getent group alaska
            getent passwd rocky
```
[root@edge ec2-user]#  getent group alaska
alaska:x:1001:
[root@edge ec2-user]# getent passwd rocky
rocky:x:3800:1002::/home/rocky:/bin/bash
```

