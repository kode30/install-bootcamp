
Install Cloudera Manager on the second node listed in 0_setup.md
 List the command and output for ls /etc/yum.repos.d in challenges/labs/2_cm.md
```
#Before Install
[root@master1 /]# ls /etc/yum.repos.d
mariadb.repo  redhat-rhui-client-config.repo  redhat-rhui.repo  rhui-load-balancers.conf

##After Download Repo.
[root@master1 /]# ls /etc/yum.repos.d
cloudera-manager.repo  mariadb.repo  redhat-rhui-client-config.repo  redhat-rhui.repo  rhui-load-balancers.conf
```

Copy cloudera-manager.repo to challenges/labs/2_cloudera-manager.repo.md
```
[root@master1 /]# cat /etc/yum.repos.d/cloudera-manager.repo
[cloudera-manager]
# Packages for Cloudera Manager, Version 5, on RedHat or CentOS 7 x86_64
name=Cloudera Manager
baseurl=https://archive.cloudera.com/cm5/redhat/7/x86_64/cm/5.14.4/
gpgkey =https://archive.cloudera.com/cm5/redhat/7/x86_64/cm/RPM-GPG-KEY-cloudera
gpgcheck = 1
```

Connect Cloudera Manager Server to its database
  Use the scm_prepare_database.sh script to create the db.properties file
        List the full command and its output in 2_cm.md
```
[root@master1 5]# sudo /usr/share/cmf/schema/scm_prepare_database.sh mysql -h edge.cloudera.es -utemp -ptemp --scm-host master1.cloudera.es scm scm sc
JAVA_HOME=/usr/java/jre1.8.0_201-amd64
Verifying that we can write to /etc/cloudera-scm-server
Creating SCM configuration file in /etc/cloudera-scm-server
Executing:  /usr/java/jre1.8.0_201-amd64/bin/java -cp /usr/share/java/mysql-connector-java.jar:/usr/share/java/oracle-connector-java.jar:/usr/share/cmf/schema/../lib/* com.cloudera.enterprise.dbutil.DbCommandExecutor /etc/cloudera-scm-server/db.properties com.cloudera.cmf.db.
[                          main] DbCommandExecutor              INFO  Successfully connected to database.
All done, your SCM database is configured correctly

```


