Add the following to 3_cm.md:

Create user directories in HDFS for rocky and denali
The command and output for hdfs dfs -ls /user
```
sudo -u hdfs hdfs dfs -mkdir -p /user/rocky
sudo -u hdfs hdfs dfs -chown rocky:colorado /user/rocky
sudo -u hdfs hdfs dfs -mkdir -p /user/denali
sudo -u hdfs hdfs dfs -chown denali:alaska /user/denali

[root@edge ec2-user]# sudo -u hdfs hdfs dfs -ls /user
Found 7 items
drwxr-xr-x   - denali alaska            0 2019-02-15 10:26 /user/denali
drwxrwxrwx   - mapred hadoop            0 2019-02-15 10:23 /user/history
drwxrwxr-t   - hive   hive              0 2019-02-15 10:23 /user/hive
drwxrwxr-x   - hue    hue               0 2019-02-15 10:24 /user/hue
drwxrwxr-x   - impala impala            0 2019-02-15 10:24 /user/impala
drwxrwxr-x   - oozie  oozie             0 2019-02-15 10:24 /user/oozie
drwxr-xr-x   - rocky  colorado          0 2019-02-15 10:26 /user/rocky
```


The command and output from the CM API call ../api/v14/hosts
```
[root@edge ec2-user]# curl -u admin:admin 'http://ec2-35-180-39-206.eu-west-3.compute.amazonaws.com:7180/api/v14/hosts'
{
  "items" : [ {
    "hostId" : "e8e66071-6b22-4456-a3ba-a910ac672800",
    "ipAddress" : "172.31.43.80",
    "hostname" : "edge.cloudera.es",
    "rackId" : "/default",
    "hostUrl" : "http://master1.cloudera.es:7180/cmf/hostRedirect/e8e66071-6b22-4456-a3ba-a910ac672800",
    "maintenanceMode" : false,
    "maintenanceOwners" : [ ],
    "commissionState" : "COMMISSIONED",
    "numCores" : 4,
    "numPhysicalCores" : 2,
    "totalPhysMemBytes" : 16170962944
  }, {
    "hostId" : "451d43cd-d4fc-4f27-9b24-378e4f32465c",
    "ipAddress" : "172.31.37.140",
    "hostname" : "master1.cloudera.es",
    "rackId" : "/default",
    "hostUrl" : "http://master1.cloudera.es:7180/cmf/hostRedirect/451d43cd-d4fc-4f27-9b24-378e4f32465c",
    "maintenanceMode" : false,
    "maintenanceOwners" : [ ],
    "commissionState" : "COMMISSIONED",
    "numCores" : 4,
    "numPhysicalCores" : 2,
    "totalPhysMemBytes" : 16170954752
  }, {
    "hostId" : "e4efe7f9-84ac-4ed8-b35e-5ae941045e64",
    "ipAddress" : "172.31.35.130",
    "hostname" : "master2.cloudera.es",
    "rackId" : "/default",
    "hostUrl" : "http://master1.cloudera.es:7180/cmf/hostRedirect/e4efe7f9-84ac-4ed8-b35e-5ae941045e64",
    "maintenanceMode" : false,
    "maintenanceOwners" : [ ],
    "commissionState" : "COMMISSIONED",
    "numCores" : 4,
    "numPhysicalCores" : 2,
    "totalPhysMemBytes" : 16170962944
  }, {
    "hostId" : "c363ca45-66a3-4607-a307-def90348eff8",
    "ipAddress" : "172.31.36.222",
    "hostname" : "worker1.cloudera.es",
    "rackId" : "/default",
    "hostUrl" : "http://master1.cloudera.es:7180/cmf/hostRedirect/c363ca45-66a3-4607-a307-def90348eff8",
    "maintenanceMode" : false,
    "maintenanceOwners" : [ ],
    "commissionState" : "COMMISSIONED",
    "numCores" : 4,
    "numPhysicalCores" : 2,
    "totalPhysMemBytes" : 16170962944
  }, {
    "hostId" : "943e652f-ab38-4fba-bf50-6b384d675af0",
    "ipAddress" : "172.31.42.153",
    "hostname" : "worker2.cloudera.es",
    "rackId" : "/default",
    "hostUrl" : "http://master1.cloudera.es:7180/cmf/hostRedirect/943e652f-ab38-4fba-bf50-6b384d675af0",
    "maintenanceMode" : false,
    "maintenanceOwners" : [ ],
    "commissionState" : "COMMISSIONED",
    "numCores" : 4,
    "numPhysicalCores" : 2,
    "totalPhysMemBytes" : 16170962944
  } ]

```


The command and output from the CM API call ../api/v8/clusters/<githubName>/services

```
}[root@edge ec2-user]# curl -u admin:admin 'http://ec2-35-180-39-206.eu-west-3.compute.amazonaws.com:7180/api/v14/clusters/kode30/services'
{
  "items" : [ {
    "name" : "zookeeper",
    "type" : "ZOOKEEPER",
    "clusterRef" : {
      "clusterName" : "cluster"
    },
    "serviceUrl" : "http://master1.cloudera.es:7180/cmf/serviceRedirect/zookeeper",
    "roleInstancesUrl" : "http://master1.cloudera.es:7180/cmf/serviceRedirect/zookeeper/instances",
    "serviceState" : "STARTED",
    "healthSummary" : "GOOD",
    "healthChecks" : [ {
      "name" : "ZOOKEEPER_CANARY_HEALTH",
      "summary" : "GOOD",
      "suppressed" : false
    }, {
      "name" : "ZOOKEEPER_SERVERS_HEALTHY",
      "summary" : "GOOD",
      "suppressed" : false
    } ],
    "configStalenessStatus" : "FRESH",
    "clientConfigStalenessStatus" : "FRESH",
    "maintenanceMode" : false,
    "maintenanceOwners" : [ ],
    "displayName" : "ZooKeeper",
    "entityStatus" : "GOOD_HEALTH"
  }, {
    "name" : "oozie",
    "type" : "OOZIE",
    "clusterRef" : {
      "clusterName" : "cluster"
    },
    "serviceUrl" : "http://master1.cloudera.es:7180/cmf/serviceRedirect/oozie",
    "roleInstancesUrl" : "http://master1.cloudera.es:7180/cmf/serviceRedirect/oozie/instances",
    "serviceState" : "STARTED",
    "healthSummary" : "GOOD",
    "healthChecks" : [ {
      "name" : "OOZIE_OOZIE_SERVERS_HEALTHY",
      "summary" : "GOOD",
      "suppressed" : false
    } ],
    "configStalenessStatus" : "FRESH",
    "clientConfigStalenessStatus" : "FRESH",
    "maintenanceMode" : false,
    "maintenanceOwners" : [ ],
    "displayName" : "Oozie",
    "entityStatus" : "GOOD_HEALTH"
  }, {
    "name" : "hue",
    "type" : "HUE",
    "clusterRef" : {
      "clusterName" : "cluster"
    },
    "serviceUrl" : "http://master1.cloudera.es:7180/cmf/serviceRedirect/hue",
    "roleInstancesUrl" : "http://master1.cloudera.es:7180/cmf/serviceRedirect/hue/instances",
    "serviceState" : "STARTED",
    "healthSummary" : "GOOD",
    "healthChecks" : [ {
      "name" : "HUE_HUE_SERVERS_HEALTHY",
      "summary" : "GOOD",
      "suppressed" : false
    }, {
      "name" : "HUE_LOAD_BALANCER_HEALTHY",
      "summary" : "GOOD",
      "suppressed" : false
    } ],
    "configStalenessStatus" : "FRESH",
    "clientConfigStalenessStatus" : "FRESH",
    "maintenanceMode" : false,
    "maintenanceOwners" : [ ],
    "displayName" : "Hue",
    "entityStatus" : "GOOD_HEALTH"
  }, {
    "name" : "hdfs",
    "type" : "HDFS",
    "clusterRef" : {
      "clusterName" : "cluster"
    },
    "serviceUrl" : "http://master1.cloudera.es:7180/cmf/serviceRedirect/hdfs",
    "roleInstancesUrl" : "http://master1.cloudera.es:7180/cmf/serviceRedirect/hdfs/instances",
    "serviceState" : "STARTED",
    "healthSummary" : "GOOD",
    "healthChecks" : [ {
      "name" : "HDFS_BLOCKS_WITH_CORRUPT_REPLICAS",
      "summary" : "GOOD",
      "suppressed" : false
    }, {
      "name" : "HDFS_CANARY_HEALTH",
      "summary" : "GOOD",
      "suppressed" : false
    }, {
      "name" : "HDFS_DATA_NODES_HEALTHY",
      "summary" : "GOOD",
      "suppressed" : false
    }, {
      "name" : "HDFS_FREE_SPACE_REMAINING",
      "summary" : "GOOD",
      "suppressed" : false
    }, {
      "name" : "HDFS_HA_NAMENODE_HEALTH",
      "summary" : "GOOD",
      "suppressed" : false
    }, {
      "name" : "HDFS_MISSING_BLOCKS",
      "summary" : "GOOD",
      "suppressed" : false
    }, {
      "name" : "HDFS_UNDER_REPLICATED_BLOCKS",
      "summary" : "GOOD",
      "suppressed" : false
    } ],
    "configStalenessStatus" : "FRESH",
    "clientConfigStalenessStatus" : "FRESH",
    "maintenanceMode" : false,
    "maintenanceOwners" : [ ],
    "displayName" : "HDFS",
    "entityStatus" : "GOOD_HEALTH"
  }, {
    "name" : "impala",
    "type" : "IMPALA",
    "clusterRef" : {
      "clusterName" : "cluster"
    },
    "serviceUrl" : "http://master1.cloudera.es:7180/cmf/serviceRedirect/impala",
    "roleInstancesUrl" : "http://master1.cloudera.es:7180/cmf/serviceRedirect/impala/instances",
    "serviceState" : "STARTED",
    "healthSummary" : "GOOD",
    "healthChecks" : [ {
      "name" : "IMPALA_ASSIGNMENT_LOCALITY",
      "summary" : "DISABLED",
      "suppressed" : false
    }, {
      "name" : "IMPALA_CATALOGSERVER_HEALTH",
      "summary" : "GOOD",
      "suppressed" : false
    }, {
      "name" : "IMPALA_IMPALADS_HEALTHY",
      "summary" : "GOOD",
      "suppressed" : false
    }, {
      "name" : "IMPALA_STATESTORE_HEALTH",
      "summary" : "GOOD",
      "suppressed" : false
    } ],
    "configStalenessStatus" : "FRESH",
    "clientConfigStalenessStatus" : "FRESH",
    "maintenanceMode" : false,
    "maintenanceOwners" : [ ],
    "displayName" : "Impala",
    "entityStatus" : "GOOD_HEALTH"
  }, {
    "name" : "yarn",
    "type" : "YARN",
    "clusterRef" : {
      "clusterName" : "cluster"
    },
    "serviceUrl" : "http://master1.cloudera.es:7180/cmf/serviceRedirect/yarn",
    "roleInstancesUrl" : "http://master1.cloudera.es:7180/cmf/serviceRedirect/yarn/instances",
    "serviceState" : "STARTED",
    "healthSummary" : "GOOD",
    "healthChecks" : [ {
      "name" : "YARN_JOBHISTORY_HEALTH",
      "summary" : "GOOD",
      "suppressed" : false
    }, {
      "name" : "YARN_NODE_MANAGERS_HEALTHY",
      "summary" : "GOOD",
      "suppressed" : false
    }, {
      "name" : "YARN_RESOURCEMANAGERS_HEALTH",
      "summary" : "GOOD",
      "suppressed" : false
    }, {
      "name" : "YARN_USAGE_AGGREGATION_HEALTH",
      "summary" : "DISABLED",
      "suppressed" : false
    } ],
    "configStalenessStatus" : "FRESH",
    "clientConfigStalenessStatus" : "FRESH",
    "maintenanceMode" : false,
    "maintenanceOwners" : [ ],
    "displayName" : "YARN (MR2 Included)",
    "entityStatus" : "GOOD_HEALTH"
  }, {
    "name" : "hive",
    "type" : "HIVE",
    "clusterRef" : {
      "clusterName" : "cluster"
    },
    "serviceUrl" : "http://master1.cloudera.es:7180/cmf/serviceRedirect/hive",
    "roleInstancesUrl" : "http://master1.cloudera.es:7180/cmf/serviceRedirect/hive/instances",
    "serviceState" : "STARTED",
    "healthSummary" : "GOOD",
    "healthChecks" : [ {
      "name" : "HIVE_HIVEMETASTORES_HEALTHY",
      "summary" : "GOOD",
      "suppressed" : false
    }, {
      "name" : "HIVE_HIVESERVER2S_HEALTHY",
      "summary" : "GOOD",
      "suppressed" : false
    } ],
    "configStalenessStatus" : "FRESH",
    "clientConfigStalenessStatus" : "FRESH",
    "maintenanceMode" : false,
    "maintenanceOwners" : [ ],
    "displayName" : "Hive",
    "entityStatus" : "GOOD_HEALTH"
  } ]

```
