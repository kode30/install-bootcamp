## Verify user privileges

```
[root@edge cloudera-scm-agent]# beeline
Java HotSpot(TM) 64-Bit Server VM warning: ignoring option MaxPermSize=512M; support was removed in 8.0
Java HotSpot(TM) 64-Bit Server VM warning: ignoring option MaxPermSize=512M; support was removed in 8.0
Beeline version 1.1.0-cdh5.16.1 by Apache Hive
beeline>
beeline> !connect jdbc:hive2://edge.cloudera.es:10000/default;principal=hive/edge.cloudera.es@KODE.COM
scan complete in 2ms
Connecting to jdbc:hive2://edge.cloudera.es:10000/default;principal=hive/edge.cloudera.es@KODE.COM
Connected to: Apache Hive (version 1.1.0-cdh5.16.1)
Driver: Hive JDBC (version 1.1.0-cdh5.16.1)
Transaction isolation: TRANSACTION_REPEATABLE_READ
0: jdbc:hive2://edge.cloudera.es:10000/defaul> show tables;
INFO  : Compiling command(queryId=hive_20190213173232_7a65ffcb-34a8-4e76-814a-52064f21bf0e): show tables
INFO  : Semantic Analysis Completed
INFO  : Returning Hive schema: Schema(fieldSchemas:[FieldSchema(name:tab_name, type:string, comment:from deserializer)], properties:null)
INFO  : Completed compiling command(queryId=hive_20190213173232_7a65ffcb-34a8-4e76-814a-52064f21bf0e); Time taken: 0.544 seconds
INFO  : Executing command(queryId=hive_20190213173232_7a65ffcb-34a8-4e76-814a-52064f21bf0e): show tables
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20190213173232_7a65ffcb-34a8-4e76-814a-52064f21bf0e); Time taken: 0.356 seconds
INFO  : OK
+-----------+--+
| tab_name  |
+-----------+--+
+-----------+--+
No rows selected (2.183 seconds)
0: jdbc:hive2://edge.cloudera.es:10000/defaul>

```
## Create Roles

```
0: jdbc:hive2://edge.cloudera.es:10000/defaul> CREATE ROLE sentry_admin;
INFO  : Compiling command(queryId=hive_20190213174040_4212cfa2-433e-4b77-8a42-b7fab241513e): CREATE ROLE sentry_admin
INFO  : Semantic Analysis Completed
INFO  : Returning Hive schema: Schema(fieldSchemas:null, properties:null)
INFO  : Completed compiling command(queryId=hive_20190213174040_4212cfa2-433e-4b77-8a42-b7fab241513e); Time taken: 0.058 seconds
INFO  : Executing command(queryId=hive_20190213174040_4212cfa2-433e-4b77-8a42-b7fab241513e): CREATE ROLE sentry_admin
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20190213174040_4212cfa2-433e-4b77-8a42-b7fab241513e); Time taken: 0.069 seconds
INFO  : OK
No rows affected (0.136 seconds)

: jdbc:hive2://edge.cloudera.es:10000/defaul> GRANT ALL ON SERVER server1 TO ROLE sentry_admin;
INFO  : Compiling command(queryId=hive_20190213174141_d0d3b2b5-95fe-4bc4-b650-a01c554a9971): GRANT ALL ON SERVER server1 TO ROLE sentry_admin
INFO  : Semantic Analysis Completed
INFO  : Returning Hive schema: Schema(fieldSchemas:null, properties:null)
INFO  : Completed compiling command(queryId=hive_20190213174141_d0d3b2b5-95fe-4bc4-b650-a01c554a9971); Time taken: 0.059 seconds
INFO  : Executing command(queryId=hive_20190213174141_d0d3b2b5-95fe-4bc4-b650-a01c554a9971): GRANT ALL ON SERVER server1 TO ROLE sentry_admin
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20190213174141_d0d3b2b5-95fe-4bc4-b650-a01c554a9971); Time taken: 0.03 seconds
INFO  : OK
No rows affected (0.101 seconds)


0: jdbc:hive2://edge.cloudera.es:10000/defaul> GRANT ROLE sentry_admin TO GROUP kod30;
INFO  : Compiling command(queryId=hive_20190213174141_3faf2439-271a-4ffa-99a5-52141fd3be22): GRANT ROLE sentry_admin TO GROUP kod30
INFO  : Semantic Analysis Completed
INFO  : Returning Hive schema: Schema(fieldSchemas:null, properties:null)
INFO  : Completed compiling command(queryId=hive_20190213174141_3faf2439-271a-4ffa-99a5-52141fd3be22); Time taken: 0.057 seconds
INFO  : Executing command(queryId=hive_20190213174141_3faf2439-271a-4ffa-99a5-52141fd3be22): GRANT ROLE sentry_admin TO GROUP kod30
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20190213174141_3faf2439-271a-4ffa-99a5-52141fd3be22); Time taken: 0.05 seconds
INFO  : OK
No rows affected (0.117 seconds)


0: jdbc:hive2://edge.cloudera.es:10000/defaul> show tables;
INFO  : Compiling command(queryId=hive_20190213174242_51dcce72-0586-4f9f-af1a-e3ddd76d5572): show tables
INFO  : Semantic Analysis Completed
INFO  : Returning Hive schema: Schema(fieldSchemas:[FieldSchema(name:tab_name, type:string, comment:from deserializer)], properties:null)
INFO  : Completed compiling command(queryId=hive_20190213174242_51dcce72-0586-4f9f-af1a-e3ddd76d5572); Time taken: 0.079 seconds
INFO  : Executing command(queryId=hive_20190213174242_51dcce72-0586-4f9f-af1a-e3ddd76d5572): show tables
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20190213174242_51dcce72-0586-4f9f-af1a-e3ddd76d5572); Time taken: 0.095 seconds
INFO  : OK
+------------+--+
|  tab_name  |
+------------+--+
| customers  |
| sample_07  |
| sample_08  |
| web_logs   |
+------------+--+
4 rows selected (0.225 seconds)
```

## Create additional test users

Add new users to all cluster nodes

sudo groupadd selector
sudo groupadd inserters
sudo useradd -u 1100 -g selector george
sudo useradd -u 1200 -g inserters ferdinand
* add_principal george and ferdinand
```
$ sudo kadmin.local
Authenticating as principal cloudera-scm/admin@C.SAFARI-LAB.INTERNAL with password.
kadmin.local:  add_principal george
WARNING: no policy specified for george@C.SAFARI-LAB.INTERNAL; defaulting to no policy
Enter password for principal "george@C.SAFARI-LAB.INTERNAL": 
Re-enter password for principal "george@C.SAFARI-LAB.INTERNAL": 
Principal "george@C.SAFARI-LAB.INTERNAL" created.

kadmin.local:  add_principal ferdinand
WARNING: no policy specified for ferdinand@C.SAFARI-LAB.INTERNAL; defaulting to no policy
Enter password for principal "ferdinand@C.SAFARI-LAB.INTERNAL": 
Re-enter password for principal "ferdinand@C.SAFARI-LAB.INTERNAL": 
Principal "ferdinand@C.SAFARI-LAB.INTERNAL" created.

kadmin.local:  quit
```


## Create test roles

Login to beeline as your admin user
```
kinit kod30
$ beeline
!connect jdbc:hive2://edge.cloudera.es:10000/default;principal=hive/edge.cloudera.es@KODE.COM

[root@edge home]# beeline
Java HotSpot(TM) 64-Bit Server VM warning: ignoring option MaxPermSize=512M; support was removed in 8.0
Java HotSpot(TM) 64-Bit Server VM warning: ignoring option MaxPermSize=512M; support was removed in 8.0
Beeline version 1.1.0-cdh5.16.1 by Apache Hive
beeline> !connect jdbc:hive2://edge.cloudera.es:10000/default;principal=hive/edge.cloudera.es@KODE.COM
scan complete in 1ms
Connecting to jdbc:hive2://edge.cloudera.es:10000/default;principal=hive/edge.cloudera.es@KODE.COM
Connected to: Apache Hive (version 1.1.0-cdh5.16.1)
Driver: Hive JDBC (version 1.1.0-cdh5.16.1)
Transaction isolation: TRANSACTION_REPEATABLE_READ
0: jdbc:hive2://edge.cloudera.es:10000/defaul> create roles reads;
Error: Error while compiling statement: FAILED: ParseException line 1:7 cannot recognize input near 'create' 'roles' 'reads' in ddl statement (state=42000,code=40000)
0: jdbc:hive2://edge.cloudera.es:10000/defaul> create role reads;
INFO  : Compiling command(queryId=hive_20190213175050_11b964a9-6948-4f41-8799-0d57babf16f0): create role reads
INFO  : Semantic Analysis Completed
INFO  : Returning Hive schema: Schema(fieldSchemas:null, properties:null)
INFO  : Completed compiling command(queryId=hive_20190213175050_11b964a9-6948-4f41-8799-0d57babf16f0); Time taken: 0.067 seconds
INFO  : Executing command(queryId=hive_20190213175050_11b964a9-6948-4f41-8799-0d57babf16f0): create role reads
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20190213175050_11b964a9-6948-4f41-8799-0d57babf16f0); Time taken: 0.021 seconds
INFO  : OK
No rows affected (0.12 seconds)
0: jdbc:hive2://edge.cloudera.es:10000/defaul> create role writes;
INFO  : Compiling command(queryId=hive_20190213175151_40facfdd-9d20-4d86-9ace-7a004435f642): create role writes
INFO  : Semantic Analysis Completed
INFO  : Returning Hive schema: Schema(fieldSchemas:null, properties:null)
INFO  : Completed compiling command(queryId=hive_20190213175151_40facfdd-9d20-4d86-9ace-7a004435f642); Time taken: 0.054 seconds
INFO  : Executing command(queryId=hive_20190213175151_40facfdd-9d20-4d86-9ace-7a004435f642): create role writes
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20190213175151_40facfdd-9d20-4d86-9ace-7a004435f642); Time taken: 0.009 seconds
INFO  : OK
No rows affected (0.073 seconds)
```



## Grant read privilege for all tables to reads

GRANT SELECT ON DATABASE default TO ROLE reads;
```
0: jdbc:hive2://edge.cloudera.es:10000/defaul> GRANT SELECT ON DATABASE default TO ROLE reads;
INFO  : Compiling command(queryId=hive_20190213175151_11b79a2b-acf9-4a1c-95de-720ec7e88ad0): GRANT SELECT ON DATABASE default TO ROLE reads
INFO  : Semantic Analysis Completed
INFO  : Returning Hive schema: Schema(fieldSchemas:null, properties:null)
INFO  : Completed compiling command(queryId=hive_20190213175151_11b79a2b-acf9-4a1c-95de-720ec7e88ad0); Time taken: 0.053 seconds
INFO  : Executing command(queryId=hive_20190213175151_11b79a2b-acf9-4a1c-95de-720ec7e88ad0): GRANT SELECT ON DATABASE default TO ROLE reads
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20190213175151_11b79a2b-acf9-4a1c-95de-720ec7e88ad0); Time taken: 0.014 seconds
INFO  : OK
No rows affected (0.078 seconds)
```

GRANT ROLE reads TO GROUP selector;
```
0: jdbc:hive2://edge.cloudera.es:10000/defaul> GRANT ROLE reads TO GROUP selector;
INFO  : Compiling command(queryId=hive_20190213175252_0c3a4eb4-8464-43d7-b828-ae42f301232a): GRANT ROLE reads TO GROUP selector
INFO  : Semantic Analysis Completed
INFO  : Returning Hive schema: Schema(fieldSchemas:null, properties:null)
INFO  : Completed compiling command(queryId=hive_20190213175252_0c3a4eb4-8464-43d7-b828-ae42f301232a); Time taken: 0.071 seconds
INFO  : Executing command(queryId=hive_20190213175252_0c3a4eb4-8464-43d7-b828-ae42f301232a): GRANT ROLE reads TO GROUP selector
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20190213175252_0c3a4eb4-8464-43d7-b828-ae42f301232a); Time taken: 0.01 seconds
INFO  : OK
No rows affected (0.09 seconds)
```

Grant read privilege for default.sample07 only to 'writes':

REVOKE ALL ON DATABASE default FROM ROLE writes;

```
0: jdbc:hive2://edge.cloudera.es:10000/defaul> REVOKE ALL ON DATABASE default FROM ROLE writes;
INFO  : Compiling command(queryId=hive_20190213175252_b1e85459-c684-4ea9-b922-4e8b065881a1): REVOKE ALL ON DATABASE default FROM ROLE writes
INFO  : Semantic Analysis Completed
INFO  : Returning Hive schema: Schema(fieldSchemas:null, properties:null)
INFO  : Completed compiling command(queryId=hive_20190213175252_b1e85459-c684-4ea9-b922-4e8b065881a1); Time taken: 0.054 seconds
INFO  : Executing command(queryId=hive_20190213175252_b1e85459-c684-4ea9-b922-4e8b065881a1): REVOKE ALL ON DATABASE default FROM ROLE writes
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20190213175252_b1e85459-c684-4ea9-b922-4e8b065881a1); Time taken: 0.041 seconds
INFO  : OK
No rows affected (0.105 seconds)
```

GRANT SELECT ON default.sample_07 TO ROLE writes;

```
0: jdbc:hive2://edge.cloudera.es:10000/defaul> GRANT SELECT ON default.sample_07 TO ROLE writes;
INFO  : Compiling command(queryId=hive_20190213175353_aec3ad6c-e7a6-426b-838f-1b33f9778b2a): GRANT SELECT ON default.sample_07 TO ROLE writes
INFO  : Semantic Analysis Completed
INFO  : Returning Hive schema: Schema(fieldSchemas:null, properties:null)
INFO  : Completed compiling command(queryId=hive_20190213175353_aec3ad6c-e7a6-426b-838f-1b33f9778b2a); Time taken: 0.056 seconds
INFO  : Executing command(queryId=hive_20190213175353_aec3ad6c-e7a6-426b-838f-1b33f9778b2a): GRANT SELECT ON default.sample_07 TO ROLE writes
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20190213175353_aec3ad6c-e7a6-426b-838f-1b33f9778b2a); Time taken: 0.013 seconds
INFO  : OK
No rows affected (0.079 seconds)
```

GRANT ROLE writes TO GROUP inserters;

```
0: jdbc:hive2://edge.cloudera.es:10000/defaul> GRANT ROLE writes TO GROUP inserters;
INFO  : Compiling command(queryId=hive_20190213175353_befc7abc-944f-43c3-b88a-bb6013e3636f): GRANT ROLE writes TO GROUP inserters
INFO  : Semantic Analysis Completed
INFO  : Returning Hive schema: Schema(fieldSchemas:null, properties:null)
INFO  : Completed compiling command(queryId=hive_20190213175353_befc7abc-944f-43c3-b88a-bb6013e3636f); Time taken: 0.053 seconds
INFO  : Executing command(queryId=hive_20190213175353_befc7abc-944f-43c3-b88a-bb6013e3636f): GRANT ROLE writes TO GROUP inserters
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20190213175353_befc7abc-944f-43c3-b88a-bb6013e3636f); Time taken: 0.01 seconds
INFO  : OK
No rows affected (0.072 seconds)
```

kinit as george, then login to beeline
kinit as george, login to beeline, and use SHOW TABLES;
george should be able to see all tables

```
[root@edge home]# kinit george
Password for george@KODE.COM:
[root@edge home]# beeline
Java HotSpot(TM) 64-Bit Server VM warning: ignoring option MaxPermSize=512M; support was removed in 8.0
Java HotSpot(TM) 64-Bit Server VM warning: ignoring option MaxPermSize=512M; support was removed in 8.0
Beeline version 1.1.0-cdh5.16.1 by Apache Hive
beeline> !connect jdbc:hive2://edge.cloudera.es:10000/default;principal=hive/edge.cloudera.es@KODE.COM
scan complete in 2ms
Connecting to jdbc:hive2://edge.cloudera.es:10000/default;principal=hive/edge.cloudera.es@KODE.COM
Connected to: Apache Hive (version 1.1.0-cdh5.16.1)
Driver: Hive JDBC (version 1.1.0-cdh5.16.1)
Transaction isolation: TRANSACTION_REPEATABLE_READ
0: jdbc:hive2://edge.cloudera.es:10000/defaul> show tables;
INFO  : Compiling command(queryId=hive_20190213175454_35cce3e9-4743-4635-943f-65253d5f88a4): show tables
INFO  : Semantic Analysis Completed
INFO  : Returning Hive schema: Schema(fieldSchemas:[FieldSchema(name:tab_name, type:string, comment:from deserializer)], properties:null)
INFO  : Completed compiling command(queryId=hive_20190213175454_35cce3e9-4743-4635-943f-65253d5f88a4); Time taken: 0.063 seconds
INFO  : Executing command(queryId=hive_20190213175454_35cce3e9-4743-4635-943f-65253d5f88a4): show tables
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20190213175454_35cce3e9-4743-4635-943f-65253d5f88a4); Time taken: 0.105 seconds
INFO  : OK
+------------+--+
|  tab_name  |
+------------+--+
| customers  |
| sample_07  |
| sample_08  |
| web_logs   |
+------------+--+
4 rows selected (0.233 seconds)
```

Repeat the process as ferdinand, ferdinand should see sample_07

```
[root@edge home]# kinit ferdinand
Password for ferdinand@KODE.COM:
[root@edge home]# !connect jdbc:hive2://edge.cloudera.es:10000/default;principal=hive/edge.cloudera.es@KODE.COM
bash: !connect: event not found
[root@edge home]# beeline
Java HotSpot(TM) 64-Bit Server VM warning: ignoring option MaxPermSize=512M; support was removed in 8.0
Java HotSpot(TM) 64-Bit Server VM warning: ignoring option MaxPermSize=512M; support was removed in 8.0
Beeline version 1.1.0-cdh5.16.1 by Apache Hive
beeline> !connect jdbc:hive2://edge.cloudera.es:10000/default;principal=hive/edge.cloudera.es@KODE.COM
scan complete in 2ms
Connecting to jdbc:hive2://edge.cloudera.es:10000/default;principal=hive/edge.cloudera.es@KODE.COM
Connected to: Apache Hive (version 1.1.0-cdh5.16.1)
Driver: Hive JDBC (version 1.1.0-cdh5.16.1)
Transaction isolation: TRANSACTION_REPEATABLE_READ
0: jdbc:hive2://edge.cloudera.es:10000/defaul> show tables;
INFO  : Compiling command(queryId=hive_20190213175555_836880fd-4671-4477-b583-6cc742177ba3): show tables
INFO  : Semantic Analysis Completed
INFO  : Returning Hive schema: Schema(fieldSchemas:[FieldSchema(name:tab_name, type:string, comment:from deserializer)], properties:null)
INFO  : Completed compiling command(queryId=hive_20190213175555_836880fd-4671-4477-b583-6cc742177ba3); Time taken: 0.062 seconds
INFO  : Executing command(queryId=hive_20190213175555_836880fd-4671-4477-b583-6cc742177ba3): show tables
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20190213175555_836880fd-4671-4477-b583-6cc742177ba3); Time taken: 0.098 seconds
INFO  : OK
+------------+--+
|  tab_name  |
+------------+--+
| sample_07  |
+------------+--+
1 row selected (0.229 seconds)
```
