-> Create User & Directory
useradd kod30
passwd kod30
usermod -G wheel kod30

sudo su - kod30
sudo -u hdfs hdfs dfs -mkdir /user/kod30
#sudo -u hdfs hdfs dfs -chown kod30:kod30 /user/kod30

->Create a 10 GB file using teragen

[kod30@edge jars]$ time hadoop jar /opt/cloudera/parcels/CDH/jars/hadoop-examples.jar teragen -D dfs.blocksize=33554432 -D dfs.replication=1 1000000 /user/kode30/teragen

19/02/12 13:10:26 INFO Configuration.deprecation: session.id is deprecated. Instead, use dfs.metrics.session-id
19/02/12 13:10:26 INFO jvm.JvmMetrics: Initializing JVM Metrics with processName=JobTracker, sessionId=
19/02/12 13:10:26 INFO terasort.TeraGen: Generating 1000000 using 1
19/02/12 13:10:26 INFO mapreduce.JobSubmitter: number of splits:1
19/02/12 13:10:26 INFO mapreduce.JobSubmitter: Submitting tokens for job: job_local1832604834_0001
19/02/12 13:10:26 INFO mapreduce.Job: The url to track the job: http://localhost:8080/
19/02/12 13:10:26 INFO mapreduce.Job: Running job: job_local1832604834_0001
19/02/12 13:10:26 INFO mapred.LocalJobRunner: OutputCommitter set in config null
19/02/12 13:10:26 INFO output.FileOutputCommitter: File Output Committer Algorithm version is 1
19/02/12 13:10:26 INFO output.FileOutputCommitter: FileOutputCommitter skip cleanup _temporary folders under output directory:false, ignore cleanup failures: false
19/02/12 13:10:26 INFO mapred.LocalJobRunner: OutputCommitter is org.apache.hadoop.mapreduce.lib.output.FileOutputCommitter
19/02/12 13:10:26 INFO mapred.LocalJobRunner: Waiting for map tasks
19/02/12 13:10:26 INFO mapred.LocalJobRunner: Starting task: attempt_local1832604834_0001_m_000000_0
19/02/12 13:10:26 INFO output.FileOutputCommitter: File Output Committer Algorithm version is 1
19/02/12 13:10:26 INFO output.FileOutputCommitter: FileOutputCommitter skip cleanup _temporary folders under output directory:false, ignore cleanup failures: false
19/02/12 13:10:26 INFO mapred.Task:  Using ResourceCalculatorProcessTree : [ ]
19/02/12 13:10:26 INFO mapred.MapTask: Processing split: org.apache.hadoop.examples.terasort.TeraGen$RangeInputFormat$RangeInputSplit@59b0ddf6
19/02/12 13:10:27 INFO mapreduce.Job: Job job_local1832604834_0001 running in uber mode : false
19/02/12 13:10:27 INFO mapreduce.Job:  map 0% reduce 0%
19/02/12 13:10:27 INFO mapred.LocalJobRunner:
19/02/12 13:10:27 INFO mapred.Task: Task:attempt_local1832604834_0001_m_000000_0 is done. And is in the process of committing
19/02/12 13:10:28 INFO mapred.LocalJobRunner:
19/02/12 13:10:28 INFO mapred.Task: Task attempt_local1832604834_0001_m_000000_0 is allowed to commit now
19/02/12 13:10:28 INFO output.FileOutputCommitter: Saved output of task 'attempt_local1832604834_0001_m_000000_0' to hdfs://CDH-HA/user/kode30/teragen/_temporary/0/task_local1832604834_0001_m_000000
19/02/12 13:10:28 INFO mapred.LocalJobRunner: map
19/02/12 13:10:28 INFO mapred.Task: Task 'attempt_local1832604834_0001_m_000000_0' done.
19/02/12 13:10:28 INFO mapred.LocalJobRunner: Finishing task: attempt_local1832604834_0001_m_000000_0
19/02/12 13:10:28 INFO mapred.LocalJobRunner: map task executor complete.
19/02/12 13:10:28 INFO mapreduce.Job:  map 100% reduce 0%
19/02/12 13:10:28 INFO mapreduce.Job: Job job_local1832604834_0001 completed successfully
19/02/12 13:10:28 INFO mapreduce.Job: Counters: 21
        File System Counters
                FILE: Number of bytes read=276518
                FILE: Number of bytes written=624494
                FILE: Number of read operations=0
                FILE: Number of large read operations=0
                FILE: Number of write operations=0
                HDFS: Number of bytes read=0
                HDFS: Number of bytes written=100000000
                HDFS: Number of read operations=4
                HDFS: Number of large read operations=0
                HDFS: Number of write operations=3
        Map-Reduce Framework
                Map input records=1000000
                Map output records=1000000
                Input split bytes=82
                Spilled Records=0
                Failed Shuffles=0
                Merged Map outputs=0
                GC time elapsed (ms)=37
                Total committed heap usage (bytes)=245366784
        org.apache.hadoop.examples.terasort.TeraGen$Counters
                CHECKSUM=2148987642402270
        File Input Format Counters
                Bytes Read=0
        File Output Format Counters
                Bytes Written=100000000

real    0m9.358s
user    0m6.273s
sys     0m0.242s

->Run the terasort command on this file 

[kod30@edge jars]$time hadoop jar /opt/cloudera/parcels/CDH/jars/hadoop-examples.jar terasort /user/kode30/teragen /user/kode30/teragen
19/02/12 13:14:47 INFO terasort.TeraSort: starting
19/02/12 13:14:48 INFO input.FileInputFormat: Total input paths to process : 1
Spent 94ms computing base-splits.
Spent 2ms computing TeraScheduler splits.
Computing input splits took 96ms
Sampling 3 splits of 3
Making 1 from 99999 sampled records
Computing parititions took 360ms
Spent 458ms computing partitions.
19/02/12 13:14:48 INFO Configuration.deprecation: session.id is deprecated. Instead, use dfs.metrics.session-id
19/02/12 13:14:48 INFO jvm.JvmMetrics: Initializing JVM Metrics with processName=JobTracker, sessionId=
19/02/12 13:14:48 INFO mapreduce.JobSubmitter: number of splits:3
19/02/12 13:14:48 INFO mapreduce.JobSubmitter: Submitting tokens for job: job_local630942369_0001
19/02/12 13:14:49 INFO mapred.LocalDistributedCacheManager: Creating symlink: /tmp/hadoop-hdfs/mapred/local/1549977289082/_partition.lst <- /opt/cloudera/parcels/CDH-5.16.1-1.cdh5.16.1.p0.3/jars/_partition.lst
19/02/12 13:14:49 WARN fs.FileUtil: Command 'ln -s /tmp/hadoop-hdfs/mapred/local/1549977289082/_partition.lst /opt/cloudera/parcels/CDH-5.16.1-1.cdh5.16.1.p0.3/jars/_partition.lst' failed 1 with: ln: failed to create symbolic link ‘/opt/cloudera/parcels/CDH-5.16.1-1.cdh5.16.1.p0.3/jars/_partition.lst’: Permission denied

19/02/12 13:14:49 WARN mapred.LocalDistributedCacheManager: Failed to create symlink: /tmp/hadoop-hdfs/mapred/local/1549977289082/_partition.lst <- /opt/cloudera/parcels/CDH-5.16.1-1.cdh5.16.1.p0.3/jars/_partition.lst
19/02/12 13:14:49 INFO mapred.LocalDistributedCacheManager: Localized hdfs://CDH-HA/user/kode30/teragen/_partition.lst as file:/tmp/hadoop-hdfs/mapred/local/1549977289082/_partition.lst
19/02/12 13:14:49 INFO mapreduce.Job: The url to track the job: http://localhost:8080/
19/02/12 13:14:49 INFO mapreduce.Job: Running job: job_local630942369_0001
19/02/12 13:14:49 INFO mapred.LocalJobRunner: OutputCommitter set in config null
19/02/12 13:14:49 INFO output.FileOutputCommitter: File Output Committer Algorithm version is 1
19/02/12 13:14:49 INFO output.FileOutputCommitter: FileOutputCommitter skip cleanup _temporary folders under output directory:false, ignore cleanup failures: false
19/02/12 13:14:49 INFO mapred.LocalJobRunner: OutputCommitter is org.apache.hadoop.mapreduce.lib.output.FileOutputCommitter
19/02/12 13:14:49 INFO mapred.LocalJobRunner: Waiting for map tasks
19/02/12 13:14:49 INFO mapred.LocalJobRunner: Starting task: attempt_local630942369_0001_m_000000_0
19/02/12 13:14:49 INFO output.FileOutputCommitter: File Output Committer Algorithm version is 1
19/02/12 13:14:49 INFO output.FileOutputCommitter: FileOutputCommitter skip cleanup _temporary folders under output directory:false, ignore cleanup failures: false
19/02/12 13:14:49 INFO mapred.Task:  Using ResourceCalculatorProcessTree : [ ]
19/02/12 13:14:49 INFO mapred.MapTask: Processing split: hdfs://CDH-HA/user/kode30/teragen/part-m-00000:0+33554432
19/02/12 13:14:49 INFO mapred.MapTask: (EQUATOR) 0 kvi 26214396(104857584)
19/02/12 13:14:49 INFO mapred.MapTask: mapreduce.task.io.sort.mb: 100
19/02/12 13:14:49 INFO mapred.MapTask: soft limit at 83886080
19/02/12 13:14:49 INFO mapred.MapTask: bufstart = 0; bufvoid = 104857600
19/02/12 13:14:49 INFO mapred.MapTask: kvstart = 26214396; length = 6553600
19/02/12 13:14:49 INFO mapred.MapTask: Map output collector class = org.apache.hadoop.mapred.MapTask$MapOutputBuffer
19/02/12 13:14:49 INFO mapred.LocalJobRunner:
19/02/12 13:14:49 INFO mapred.MapTask: Starting flush of map output
19/02/12 13:14:49 INFO mapred.MapTask: Spilling map output
19/02/12 13:14:49 INFO mapred.MapTask: bufstart = 0; bufend = 34225590; bufvoid = 104857600
19/02/12 13:14:49 INFO mapred.MapTask: kvstart = 26214396(104857584); kvend = 24872220(99488880); length = 1342177/6553600
19/02/12 13:14:50 INFO mapreduce.Job: Job job_local630942369_0001 running in uber mode : false
19/02/12 13:14:50 INFO mapreduce.Job:  map 0% reduce 0%
19/02/12 13:14:50 INFO mapred.MapTask: Finished spill 0
19/02/12 13:14:50 INFO mapred.Task: Task:attempt_local630942369_0001_m_000000_0 is done. And is in the process of committing
19/02/12 13:14:50 INFO mapred.LocalJobRunner: map
19/02/12 13:14:50 INFO mapred.Task: Task 'attempt_local630942369_0001_m_000000_0' done.
19/02/12 13:14:50 INFO mapred.LocalJobRunner: Finishing task: attempt_local630942369_0001_m_000000_0
19/02/12 13:14:50 INFO mapred.LocalJobRunner: Starting task: attempt_local630942369_0001_m_000001_0
19/02/12 13:14:50 INFO output.FileOutputCommitter: File Output Committer Algorithm version is 1
19/02/12 13:14:50 INFO output.FileOutputCommitter: FileOutputCommitter skip cleanup _temporary folders under output directory:false, ignore cleanup failures: false
19/02/12 13:14:50 INFO mapred.Task:  Using ResourceCalculatorProcessTree : [ ]
19/02/12 13:14:50 INFO mapred.MapTask: Processing split: hdfs://CDH-HA/user/kode30/teragen/part-m-00000:33554432+33554432
19/02/12 13:14:50 INFO mapred.MapTask: (EQUATOR) 0 kvi 26214396(104857584)
19/02/12 13:14:50 INFO mapred.MapTask: mapreduce.task.io.sort.mb: 100
19/02/12 13:14:50 INFO mapred.MapTask: soft limit at 83886080
19/02/12 13:14:50 INFO mapred.MapTask: bufstart = 0; bufvoid = 104857600
19/02/12 13:14:50 INFO mapred.MapTask: kvstart = 26214396; length = 6553600
19/02/12 13:14:50 INFO mapred.MapTask: Map output collector class = org.apache.hadoop.mapred.MapTask$MapOutputBuffer
19/02/12 13:14:51 INFO mapred.LocalJobRunner:
19/02/12 13:14:51 INFO mapred.MapTask: Starting flush of map output
19/02/12 13:14:51 INFO mapred.MapTask: Spilling map output
19/02/12 13:14:51 INFO mapred.MapTask: bufstart = 0; bufend = 34225488; bufvoid = 104857600
19/02/12 13:14:51 INFO mapred.MapTask: kvstart = 26214396(104857584); kvend = 24872224(99488896); length = 1342173/6553600
19/02/12 13:14:51 INFO mapreduce.Job:  map 33% reduce 0%
19/02/12 13:14:51 INFO mapred.MapTask: Finished spill 0
19/02/12 13:14:51 INFO mapred.Task: Task:attempt_local630942369_0001_m_000001_0 is done. And is in the process of committing
19/02/12 13:14:51 INFO mapred.LocalJobRunner: map
19/02/12 13:14:51 INFO mapred.Task: Task 'attempt_local630942369_0001_m_000001_0' done.
19/02/12 13:14:51 INFO mapred.LocalJobRunner: Finishing task: attempt_local630942369_0001_m_000001_0
19/02/12 13:14:51 INFO mapred.LocalJobRunner: Starting task: attempt_local630942369_0001_m_000002_0
19/02/12 13:14:51 INFO output.FileOutputCommitter: File Output Committer Algorithm version is 1
19/02/12 13:14:51 INFO output.FileOutputCommitter: FileOutputCommitter skip cleanup _temporary folders under output directory:false, ignore cleanup failures: false
19/02/12 13:14:51 INFO mapred.Task:  Using ResourceCalculatorProcessTree : [ ]
19/02/12 13:14:51 INFO mapred.MapTask: Processing split: hdfs://CDH-HA/user/kode30/teragen/part-m-00000:67108864+32891136
19/02/12 13:14:51 INFO mapred.MapTask: (EQUATOR) 0 kvi 26214396(104857584)
19/02/12 13:14:51 INFO mapred.MapTask: mapreduce.task.io.sort.mb: 100
19/02/12 13:14:51 INFO mapred.MapTask: soft limit at 83886080
19/02/12 13:14:51 INFO mapred.MapTask: bufstart = 0; bufvoid = 104857600
19/02/12 13:14:51 INFO mapred.MapTask: kvstart = 26214396; length = 6553600
19/02/12 13:14:51 INFO mapred.MapTask: Map output collector class = org.apache.hadoop.mapred.MapTask$MapOutputBuffer
19/02/12 13:14:51 INFO mapred.LocalJobRunner:
19/02/12 13:14:51 INFO mapred.MapTask: Starting flush of map output
19/02/12 13:14:51 INFO mapred.MapTask: Spilling map output
19/02/12 13:14:51 INFO mapred.MapTask: bufstart = 0; bufend = 33548922; bufvoid = 104857600
19/02/12 13:14:51 INFO mapred.MapTask: kvstart = 26214396(104857584); kvend = 24898756(99595024); length = 1315641/6553600
19/02/12 13:14:52 INFO mapreduce.Job:  map 67% reduce 0%
19/02/12 13:14:52 INFO mapred.MapTask: Finished spill 0
19/02/12 13:14:52 INFO mapred.Task: Task:attempt_local630942369_0001_m_000002_0 is done. And is in the process of committing
19/02/12 13:14:52 INFO mapred.LocalJobRunner: map
19/02/12 13:14:52 INFO mapred.Task: Task 'attempt_local630942369_0001_m_000002_0' done.
19/02/12 13:14:52 INFO mapred.LocalJobRunner: Finishing task: attempt_local630942369_0001_m_000002_0
19/02/12 13:14:52 INFO mapred.LocalJobRunner: map task executor complete.
19/02/12 13:14:52 INFO mapred.LocalJobRunner: Waiting for reduce tasks
19/02/12 13:14:52 INFO mapred.LocalJobRunner: Starting task: attempt_local630942369_0001_r_000000_0
19/02/12 13:14:52 INFO output.FileOutputCommitter: File Output Committer Algorithm version is 1
19/02/12 13:14:52 INFO output.FileOutputCommitter: FileOutputCommitter skip cleanup _temporary folders under output directory:false, ignore cleanup failures: false
19/02/12 13:14:52 INFO mapred.Task:  Using ResourceCalculatorProcessTree : [ ]
19/02/12 13:14:52 INFO mapred.ReduceTask: Using ShuffleConsumerPlugin: org.apache.hadoop.mapreduce.task.reduce.Shuffle@b8b04e5
19/02/12 13:14:52 INFO reduce.MergeManagerImpl: MergerManager: memoryLimit=179830784, maxSingleShuffleLimit=44957696, mergeThreshold=118688320, ioSortFactor=10, memToMemMergeOutputsThreshold=10
19/02/12 13:14:52 INFO reduce.EventFetcher: attempt_local630942369_0001_r_000000_0 Thread started: EventFetcher for fetching Map Completion Events
19/02/12 13:14:52 INFO reduce.LocalFetcher: localfetcher#1 about to shuffle output of map attempt_local630942369_0001_m_000001_0 decomp: 34896578 len: 34896582 to MEMORY
19/02/12 13:14:52 INFO reduce.InMemoryMapOutput: Read 34896578 bytes from map-output for attempt_local630942369_0001_m_000001_0
19/02/12 13:14:52 INFO reduce.MergeManagerImpl: closeInMemoryFile -> map-output of size: 34896578, inMemoryMapOutputs.size() -> 1, commitMemory -> 0, usedMemory ->34896578
19/02/12 13:14:52 INFO reduce.LocalFetcher: localfetcher#1 about to shuffle output of map attempt_local630942369_0001_m_000002_0 decomp: 34206746 len: 34206750 to MEMORY
19/02/12 13:14:52 INFO reduce.InMemoryMapOutput: Read 34206746 bytes from map-output for attempt_local630942369_0001_m_000002_0
19/02/12 13:14:52 INFO reduce.MergeManagerImpl: closeInMemoryFile -> map-output of size: 34206746, inMemoryMapOutputs.size() -> 2, commitMemory -> 34896578, usedMemory ->69103324
19/02/12 13:14:52 INFO reduce.LocalFetcher: localfetcher#1 about to shuffle output of map attempt_local630942369_0001_m_000000_0 decomp: 34896682 len: 34896686 to MEMORY
19/02/12 13:14:52 INFO reduce.InMemoryMapOutput: Read 34896682 bytes from map-output for attempt_local630942369_0001_m_000000_0
19/02/12 13:14:52 INFO reduce.MergeManagerImpl: closeInMemoryFile -> map-output of size: 34896682, inMemoryMapOutputs.size() -> 3, commitMemory -> 69103324, usedMemory ->104000006
19/02/12 13:14:52 INFO reduce.EventFetcher: EventFetcher is interrupted.. Returning
19/02/12 13:14:52 INFO mapred.LocalJobRunner: 3 / 3 copied.
19/02/12 13:14:52 INFO reduce.MergeManagerImpl: finalMerge called with 3 in-memory map-outputs and 0 on-disk map-outputs
19/02/12 13:14:52 INFO mapred.Merger: Merging 3 sorted segments
19/02/12 13:14:52 INFO mapred.Merger: Down to the last merge-pass, with 3 segments left of total size: 103999967 bytes
19/02/12 13:14:53 INFO mapreduce.Job:  map 100% reduce 0%
19/02/12 13:14:53 INFO reduce.MergeManagerImpl: Merged 3 segments, 104000006 bytes to disk to satisfy reduce memory limit
19/02/12 13:14:53 INFO reduce.MergeManagerImpl: Merging 1 files, 104000006 bytes from disk
19/02/12 13:14:53 INFO reduce.MergeManagerImpl: Merging 0 segments, 0 bytes from memory into reduce
19/02/12 13:14:53 INFO mapred.Merger: Merging 1 sorted segments
19/02/12 13:14:53 INFO mapred.Merger: Down to the last merge-pass, with 1 segments left of total size: 103999989 bytes
19/02/12 13:14:53 INFO mapred.LocalJobRunner: 3 / 3 copied.
19/02/12 13:14:53 INFO Configuration.deprecation: mapred.skip.on is deprecated. Instead, use mapreduce.job.skiprecords
19/02/12 13:14:54 INFO mapred.Task: Task:attempt_local630942369_0001_r_000000_0 is done. And is in the process of committing
19/02/12 13:14:54 INFO mapred.LocalJobRunner: 3 / 3 copied.
19/02/12 13:14:54 INFO mapred.Task: Task attempt_local630942369_0001_r_000000_0 is allowed to commit now
19/02/12 13:14:54 INFO output.FileOutputCommitter: Saved output of task 'attempt_local630942369_0001_r_000000_0' to hdfs://CDH-HA/user/kode30/teragen/_temporary/0/task_local630942369_0001_r_000000
19/02/12 13:14:54 INFO mapred.LocalJobRunner: reduce > reduce
19/02/12 13:14:54 INFO mapred.Task: Task 'attempt_local630942369_0001_r_000000_0' done.
19/02/12 13:14:54 INFO mapred.LocalJobRunner: Finishing task: attempt_local630942369_0001_r_000000_0
19/02/12 13:14:54 INFO mapred.LocalJobRunner: reduce task executor complete.
19/02/12 13:14:55 INFO mapreduce.Job:  map 100% reduce 100%
19/02/12 13:14:55 INFO mapreduce.Job: Job job_local630942369_0001 completed successfully
19/02/12 13:14:55 INFO mapreduce.Job: Counters: 35
        File System Counters
                FILE: Number of bytes read=209109236
                FILE: Number of bytes written=419195280
                FILE: Number of read operations=0
                FILE: Number of large read operations=0
                FILE: Number of write operations=0
                HDFS: Number of bytes read=340663000
                HDFS: Number of bytes written=100000000
                HDFS: Number of read operations=93
                HDFS: Number of large read operations=0
                HDFS: Number of write operations=10
        Map-Reduce Framework
                Map input records=1000000
                Map output records=1000000
                Map output bytes=102000000
                Map output materialized bytes=104000018
                Input split bytes=333
                Combine input records=0
                Combine output records=0
                Reduce input groups=1000000
                Reduce shuffle bytes=104000018
                Reduce input records=1000000
                Reduce output records=1000000
                Spilled Records=2000000
                Shuffled Maps =3
                Failed Shuffles=0
                Merged Map outputs=3
                GC time elapsed (ms)=262
                Total committed heap usage (bytes)=979369984
        Shuffle Errors
                BAD_ID=0
                CONNECTION=0
                IO_ERROR=0
                WRONG_LENGTH=0
                WRONG_MAP=0
                WRONG_REDUCE=0
        File Input Format Counters
                Bytes Read=100000000
        File Output Format Counters
                Bytes Written=100000000
19/02/12 13:14:55 INFO terasort.TeraSort: done

real    0m8.994s
user    0m12.587s
sys     0m0.696s
