**[root@edge journal]# curl -u kode30:cloudera 'http://ec2-35-180-198-7.eu-west-3.compute.amazonaws.com:7180/api/v13/clusters/Kode30/services/hive/'
```
{
  "name" : "hive",
  "type" : "HIVE",
  "clusterRef" : {
    "clusterName" : "cluster"
  },
  "serviceUrl" : "http://edge.cloudera.es:7180/cmf/serviceRedirect/hive",
  "roleInstancesUrl" : "http://edge.cloudera.es:7180/cmf/serviceRedirect/hive/instances",
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
}
```
  
**[root@edge journal]# curl -u kode30:cloudera -X POST 'http://ec2-35-180-198-7.eu-west-3.compute.amazonaws.com:7180/api/v13/clusters/Kode30/services/hive/commands/stop'
```
{
  "id" : 1203,
  "name" : "Stop",
  "startTime" : "2019-02-13T11:47:33.730Z",
  "active" : true,
  "serviceRef" : {
    "clusterName" : "cluster",
    "serviceName" : "hive"
  }
```

**[root@edge journal]# curl -u kode30:cloudera -X POST 'http://ec2-35-180-198-7.eu-west-3.compute.amazonaws.com:7180/api/v13/clusters/Kode30/services/hive/commands/start'
```
{
  "id" : 1207,
  "name" : "Start",
  "startTime" : "2019-02-13T11:48:09.814Z",
  "active" : true,
  "serviceRef" : {
    "clusterName" : "cluster",
    "serviceName" : "hive"
  }
```
