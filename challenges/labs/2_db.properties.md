In challenges/labs/2_db.properties.md add:

The first line of the server log
```
[root@master1 5]# head -1 /var/log/cloudera-scm-server/cloudera-scm-server.log
2019-02-15 10:01:03,805 INFO main:com.cloudera.server.cmf.Main: ================================================================================
```

The line(s) that contain the phrase "Started Jetty server"
```
2019-02-15 10:01:44,221 INFO WebServerImpl:org.mortbay.log: Started SelectChannelConnector@0.0.0.0:7180
2019-02-15 10:01:44,221 INFO WebServerImpl:com.cloudera.server.cmf.WebServerImpl: Started Jetty server.
2019-02-15 10:01:49,198 INFO ScmActive-0:com.cloudera.server.cmf.components.ScmActive: ScmActive completed successfully.
```

The content of the db.properties file
```
[root@master1 cloudera-scm-server]# cat db.properties
# Auto-generated by scm_prepare_database.sh on Fri Feb 15 09:58:28 UTC 2019
#
# For information describing how to configure the Cloudera Manager Server
# to connect to databases, see the "Cloudera Manager Installation Guide."
#
com.cloudera.cmf.db.type=mysql
com.cloudera.cmf.db.host=edge.cloudera.es
com.cloudera.cmf.db.name=scm
com.cloudera.cmf.db.user=scm
com.cloudera.cmf.db.setupType=EXTERNAL
com.cloudera.cmf.db.password=sc
```
