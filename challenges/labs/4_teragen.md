Put the following in challenges/labs/4_teragen.md


The full teragen command and output
```
[rocky@edge ec2-user]$ time hadoop jar /opt/cloudera/parcels/CDH/lib/hadoop-0.20-mapreduce/hadoop-examples.jar teragen -Dmapreduce.job.maps=8 -Dmapreduce.map.memory.mb=805 12345000 /user/rocky/tgen
19/02/15 11:27:32 INFO client.RMProxy: Connecting to ResourceManager at master1.cloudera.es/172.31.37.140:8032
19/02/15 11:27:33 INFO terasort.TeraGen: Generating 12345000 using 8
19/02/15 11:27:33 INFO mapreduce.JobSubmitter: number of splits:8
19/02/15 11:27:33 INFO mapreduce.JobSubmitter: Submitting tokens for job: job_1550226181954_0002
19/02/15 11:27:33 INFO impl.YarnClientImpl: Submitted application application_1550226181954_0002
19/02/15 11:27:33 INFO mapreduce.Job: The url to track the job: http://master1.cloudera.es:8088/proxy/application_1550226181954_0002/
19/02/15 11:27:33 INFO mapreduce.Job: Running job: job_1550226181954_0002
19/02/15 11:27:38 INFO mapreduce.Job: Job job_1550226181954_0002 running in uber mode : false
19/02/15 11:27:38 INFO mapreduce.Job:  map 0% reduce 0%
19/02/15 11:27:45 INFO mapreduce.Job:  map 25% reduce 0%
19/02/15 11:27:46 INFO mapreduce.Job:  map 50% reduce 0%
19/02/15 11:27:47 INFO mapreduce.Job:  map 75% reduce 0%
19/02/15 11:27:48 INFO mapreduce.Job:  map 88% reduce 0%
19/02/15 11:27:50 INFO mapreduce.Job:  map 100% reduce 0%
19/02/15 11:27:50 INFO mapreduce.Job: Job job_1550226181954_0002 completed successfully
19/02/15 11:27:50 INFO mapreduce.Job: Counters: 31
        File System Counters
                FILE: Number of bytes read=0
                FILE: Number of bytes written=1193583
                FILE: Number of read operations=0
                FILE: Number of large read operations=0
                FILE: Number of write operations=0
                HDFS: Number of bytes read=677
                HDFS: Number of bytes written=1234500000
                HDFS: Number of read operations=32
                HDFS: Number of large read operations=0
                HDFS: Number of write operations=16
        Job Counters
                Launched map tasks=8
                Other local map tasks=8
                Total time spent by all maps in occupied slots (ms)=46284
                Total time spent by all reduces in occupied slots (ms)=0
                Total time spent by all map tasks (ms)=46284
                Total vcore-milliseconds taken by all map tasks=46284
                Total megabyte-milliseconds taken by all map tasks=47394816
        Map-Reduce Framework
                Map input records=12345000
                Map output records=12345000
                Input split bytes=677
                Spilled Records=0
                Failed Shuffles=0
                Merged Map outputs=0
                GC time elapsed (ms)=892
                CPU time spent (ms)=28930
                Physical memory (bytes) snapshot=2202415104
                Virtual memory (bytes) snapshot=20786315264
                Total committed heap usage (bytes)=2271215616
        org.apache.hadoop.examples.terasort.TeraGen$Counters
                CHECKSUM=26510014434051487
        File Input Format Counters
                Bytes Read=0
        File Output Format Counters
                Bytes Written=1234500000

```

The result of the time command
```
real    0m19.871s
user    0m5.522s
sys     0m0.282s
```

The command and output of hdfs dfs -ls /user/rocky/tgen
```
[rocky@edge conf]$ hdfs dfs -ls /user/rocky/tgen
Found 9 items
-rw-r--r--   3 rocky colorado          0 2019-02-15 11:27 /user/rocky/tgen/_SUCCESS
-rw-r--r--   3 rocky colorado  154312500 2019-02-15 11:27 /user/rocky/tgen/part-m-00000
-rw-r--r--   3 rocky colorado  154312500 2019-02-15 11:27 /user/rocky/tgen/part-m-00001
-rw-r--r--   3 rocky colorado  154312500 2019-02-15 11:27 /user/rocky/tgen/part-m-00002
-rw-r--r--   3 rocky colorado  154312500 2019-02-15 11:27 /user/rocky/tgen/part-m-00003
-rw-r--r--   3 rocky colorado  154312500 2019-02-15 11:27 /user/rocky/tgen/part-m-00004
-rw-r--r--   3 rocky colorado  154312500 2019-02-15 11:27 /user/rocky/tgen/part-m-00005
-rw-r--r--   3 rocky colorado  154312500 2019-02-15 11:27 /user/rocky/tgen/part-m-00006
-rw-r--r--   3 rocky colorado  154312500 2019-02-15 11:27 /user/rocky/tgen/part-m-00007
```

The command and output of hadoop fsck -blocks /user/rocky
```
[rocky@edge conf]$ hdfs fsck -blocks /user/rocky
Connecting to namenode via http://master1.cloudera.es:50070/fsck?ugi=rocky&blocks=1&path=%2Fuser%2Frocky
FSCK started by rocky (auth:SIMPLE) from /172.31.43.80 for path /user/rocky at Fri Feb 15 11:28:24 UTC 2019
....................Status: HEALTHY
 Total size:    3703500000 B
 Total dirs:    9
 Total files:   20
 Total symlinks:                0
 Total blocks (validated):      42 (avg. block size 88178571 B)
 Minimally replicated blocks:   42 (100.0 %)
 Over-replicated blocks:        0 (0.0 %)
 Under-replicated blocks:       0 (0.0 %)
 Mis-replicated blocks:         0 (0.0 %)
 Default replication factor:    3
 Average block replication:     3.0
 Corrupt blocks:                0
 Missing replicas:              0 (0.0 %)
 Number of data-nodes:          3
 Number of racks:               1
FSCK ended at Fri Feb 15 11:28:24 UTC 2019 in 2 milliseconds

The filesystem under path '/user/rocky' is HEALTHY

```
