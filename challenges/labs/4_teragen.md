```
[ernest@ip-172-31-31-254 ~]$ time

real    0m0.000s
user    0m0.000s
sys     0m0.000s
```
```
[ernest@ip-172-31-31-254 ~]$ hadoop jar /opt/cloudera/parcels/CDH/lib/hadoop-mapreduce/hadoop-mapreduce-examples.jar teragen -Ddfs.block.size=32000000 -Dmapred.map.tasks=6 teragen512
teragen <num rows> <output dir>
```
```
[ernest@ip-172-31-31-254 ~]$ hadoop jar /opt/cloudera/parcels/CDH/lib/hadoop-mapreduce/hadoop-mapreduce-examples.jar teragen -Ddfs.block.size=32000000 -Dmapred.map.tasks=6 512000 teragen512
17/10/20 10:22:16 INFO client.RMProxy: Connecting to ResourceManager at ip-172-31-31-254.eu-central-1.compute.internal/172.31.31.254:8032
17/10/20 10:22:17 INFO terasort.TeraSort: Generating 512000 using 6
17/10/20 10:22:17 INFO mapreduce.JobSubmitter: number of splits:6
17/10/20 10:22:17 INFO Configuration.deprecation: dfs.block.size is deprecated. Instead, use dfs.blocksize
17/10/20 10:22:17 INFO Configuration.deprecation: mapred.map.tasks is deprecated. Instead, use mapreduce.job.maps
17/10/20 10:22:17 INFO mapreduce.JobSubmitter: Submitting tokens for job: job_1508491380053_0001
17/10/20 10:22:18 INFO impl.YarnClientImpl: Submitted application application_1508491380053_0001
17/10/20 10:22:18 INFO mapreduce.Job: The url to track the job: http://ip-172-31-31-254.eu-central-1.compute.internal:8088/proxy/application_1508491380053_0001/
17/10/20 10:22:18 INFO mapreduce.Job: Running job: job_1508491380053_0001
17/10/20 10:22:24 INFO mapreduce.Job: Job job_1508491380053_0001 running in uber mode : false
17/10/20 10:22:24 INFO mapreduce.Job:  map 0% reduce 0%
17/10/20 10:22:32 INFO mapreduce.Job:  map 33% reduce 0%
17/10/20 10:22:33 INFO mapreduce.Job:  map 50% reduce 0%
17/10/20 10:22:34 INFO mapreduce.Job:  map 83% reduce 0%
17/10/20 10:22:36 INFO mapreduce.Job:  map 100% reduce 0%
17/10/20 10:22:36 INFO mapreduce.Job: Job job_1508491380053_0001 completed successfully
17/10/20 10:22:36 INFO mapreduce.Job: Counters: 31
        File System Counters
                FILE: Number of bytes read=0
                FILE: Number of bytes written=741558
                FILE: Number of read operations=0
                FILE: Number of large read operations=0
                FILE: Number of write operations=0
                HDFS: Number of bytes read=507
                HDFS: Number of bytes written=51200000
                HDFS: Number of read operations=24
                HDFS: Number of large read operations=0
                HDFS: Number of write operations=12
        Job Counters
                Launched map tasks=6
                Other local map tasks=6
                Total time spent by all maps in occupied slots (ms)=35426
                Total time spent by all reduces in occupied slots (ms)=0
                Total time spent by all map tasks (ms)=35426
                Total vcore-seconds taken by all map tasks=35426
                Total megabyte-seconds taken by all map tasks=36276224
        Map-Reduce Framework
                Map input records=512000
                Map output records=512000
                Input split bytes=507
                Spilled Records=0
                Failed Shuffles=0
                Merged Map outputs=0
                GC time elapsed (ms)=962
                CPU time spent (ms)=8700
                Physical memory (bytes) snapshot=1085366272
                Virtual memory (bytes) snapshot=16736768000
                Total committed heap usage (bytes)=1179648000
        org.apache.hadoop.examples.terasort.TeraGen$Counters
                CHECKSUM=1100181995389654
        File Input Format Counters
                Bytes Read=0
        File Output Format Counters
                Bytes Written=51200000
```
