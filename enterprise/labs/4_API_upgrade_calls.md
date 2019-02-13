# Upgrade Cloudera Manager 5.15X


## Cloudera Current Version:
******* I install the last version i can`t upgrade but this its the steps
```
$ curl -u kode30:cloudera 'http://ec2-35-180-198-7.eu-west-3.compute.amazonaws.com:7180/api/v17/cm/version'
{
  "version" : "5.16.1",
  "buildUser" : "jenkins",
  "buildTimestamp" : "20181120-1809",
  "gitHash" : "6a13b87a6fcdf4afad6d4474a68a9434b24d6c67",
  "snapshot" : false
}
```



Back up the following directories on the Cloudera Manager server host:
/etc/cloudera-scm-server
/etc/cloudera-scm-agent

```
$ sudo mkdir /etc/cloudera-scm-server-backup/
$ sudo cp -pR /etc/cloudera-scm-server/* /etc/cloudera-scm-server-backup/
```

```
$ sudo mkdir /etc/cloudera-scm-agent-backup/
$ sudo cp -pR /etc/cloudera-scm-agent/* /etc/cloudera-scm-agent-backup/
```

Upgrade with Cloudera repository:

Back up the current Cloudera Manager repo file, located in /etc/yum.repos.d/
```
$ sudo mkdir /etc/yum.repos.d-backup/
$ sudo cp -pR /etc/yum.repos.d/* /etc/yum.repos.d-backup/
```

Download the Cloudera .repo file for your distribution by starting at https://archive.cloudera.com/cm5/ and navigating to the directory that matches your operating system.


```
$ wget https://archive.cloudera.com/cm5/redhat/7/x86_64/cm/cloudera-manager.repo
```

Copy the cloudera-manager.repo file to the configuration location for the package management software for your system:
RHEL
Copy cloudera-manager.repo to /etc/yum.repos.d/

```
$ sudo cp cloudera-manager.repo /etc/yum.repos.d/cloudera-manager.repo
```

Run the following command to clean the cache directories and upgrade the software:
RHEL
```
sudo yum clean all
sudo yum upgrade cloudera-manager-server cloudera-manager-daemons cloudera-manager-agent
```

On the Cloudera Manager Server host, verify that you now have the following packages, corresponding to the version of Cloudera Manager you installed, by running the following command:
RPM-based distributions
```
$ rpm -qa 'cloudera-manager-*'
cloudera-manager-server-5.16.0-0.cm5160.p0.120.el6.x86_64
cloudera-manager-agent-5.16.0-0.cm5160.p0.120.el6.x86_64
cloudera-manager-daemons-5.16.0-0.cm5160.p0.120.el6.x86_64
```
Start Cloudera Manager Server. On the Cloudera Manager Server host (the host on which you installed the cloudera-manager-server package), do the following:
```
sudo service cloudera-scm-server start
```

Log in to the Cloudera Manager Admin Console. It can take several minutes for Cloudera Manager Server to start, and the console is unavailable until the server startup is complete.
The Upgrade Wizard displays.



## Use the API on the command line to:
* Report the latest available version of the API
```
$ curl -u admin:admin 'http://ec2-35-180-198-7.eu-west-3.compute.amazonaws.com:7180/api/version'
v19
```

* Report the CM version
```
$ curl -u kode30:cloudera 'http://ec2-35-180-198-7.eu-west-3.compute.amazonaws.com:7180/api/v17/cm/version'
{
  "version" : "5.16.1",
  "buildUser" : "jenkins",
  "buildTimestamp" : "20181120-1809",
  "gitHash" : "6a13b87a6fcdf4afad6d4474a68a9434b24d6c67",
  "snapshot" : false
}
```
```
* List all CM users
```
$ curl -u kode30:cloudera 'http://ec2-35-180-198-7.eu-west-3.compute.amazonaws.com:7180/api/v17/users'
{
  "items" : [ {
    "name" : "admin",
    "roles" : [ "ROLE_LIMITED" ]
  }, {
    "name" : "kode30",
    "roles" : [ "ROLE_ADMIN" ]
  }, {
    "name" : "minotaur",
    "roles" : [ "ROLE_CONFIGURATOR" ]
  } ]
}
```
* Report the database server in use by CM
```
$ curl -u kode30:cloudera 'http://ec2-35-180-198-7.eu-west-3.compute.amazonaws.com:7180/api/v17/cm/scmDbInfo'
{
  "scmDbType" : "MYSQL",
  "embeddedDbUsed" : false
}
