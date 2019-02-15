Record the following in challenges/labs/1_db-server.md

A command and output that shows the hostname of your database server
```
[root@edge home]# hostname
edge.cloudera.es
[root@edge home]#  systemctl status mysql
● mysql.service - LSB: start and stop MariaDB
   Loaded: loaded (/etc/rc.d/init.d/mysql; bad; vendor preset: disabled)
   Active: active (running) since Fri 2019-02-15 09:05:04 UTC; 14min ago
     Docs: man:systemd-sysv-generator(8)
  Process: 1610 ExecStop=/etc/rc.d/init.d/mysql stop (code=exited, status=0/SUCCESS)
  Process: 2322 ExecStart=/etc/rc.d/init.d/mysql start (code=exited, status=0/SUCCESS)
   CGroup: /system.slice/mysql.service
           ├─2328 /bin/sh /usr/bin/mysqld_safe --datadir=/var/lib/mysql --pid-file=/var/lib/mysql/edge.cloudera.es.pi...
           └─2424 /usr/sbin/mysqld --basedir=/usr --datadir=/var/lib/mysql --plugin-dir=/usr/lib64/mysql/plugin --use...

Feb 15 09:05:02 edge.cloudera.es systemd[1]: Starting LSB: start and stop MariaDB...
Feb 15 09:05:02 edge.cloudera.es mysql[2322]: Starting MariaDB.190215 09:05:02 mysqld_safe Logging to '/var/lib/...err'.
Feb 15 09:05:02 edge.cloudera.es mysql[2322]: 190215 09:05:02 mysqld_safe Starting mysqld daemon with databases ...mysql
Feb 15 09:05:04 edge.cloudera.es mysql[2322]: . SUCCESS!
Feb 15 09:05:04 edge.cloudera.es systemd[1]: Started LSB: start and stop MariaDB.
Hint: Some lines were ellipsized, use -l to show in full.
```

A command and output that reports the database server version
```
[root@edge home]# mysql -V
mysql  Ver 15.1 Distrib 5.5.63-MariaDB, for Linux (x86_64) using readline 5.1
```

A command and output that lists all the databases in the server
```
MariaDB [(none)]> show databases;
+--------------------+
| Database           |
+--------------------+
| information_schema |
| hue                |
| metastore          |
| mysql              |
| oozie              |
| performance_schema |
| rman               |
| scm                |
+--------------------+
8 rows in set (0.00 sec)

```

