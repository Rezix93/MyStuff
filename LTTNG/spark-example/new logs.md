

## Before start
```bash
./build/mvn -DskipTests clean package -rf :spark-examples_2.12


pgrep -a lttng-sessiond
sudo lttng-sessiond --daemonize

cd /opt/spark/
 
./sbin/start-history-server.sh

PATH=$PATH:/usr/local/hadoop/sbin
bash start-dfs.sh
bash start-yarn.sh

bash stop-dfs.sh 
bash stop-yarn.sh

lttng view > output-lttng.log 2>&1
/usr/local/hadoop/bin/yarn node -list

standalone:

http://localhost:8080/
./sbin/start-master.sh

./sbin/start-worker.sh --cores 4 --memory 4g spark://Rezghool:7077


/usr/local/hadoop/bin/hdfs dfsadmin -report

^.*(SparkListenerTaskStart|SparkListenerTaskEnd|word3).*```

spark://4ae8a1ed6d6a:7077



## Enable everything


setting SPARK_WORKER_INSTANCES=2 means you want to run two Spark worker nodes (instances) on that particular machine.

in spark-env.sh
export HADOOP_CONF_DIR=$HADOOP_HOME/etc/hadoop
export YARN_CONF_DIR=$HADOOP_HOME/etc/hadoop
SPARK_WORKER_CORES=2
SPARK_WORKER_INSTANCES=3
      .set("spark.executor.instances", "4")

SPARK_WORKER_MEMORY=2g



```bash

--deploy-mode client \
--master local[*] \
--deploy-mode client \



./sbin/start-worker.sh spark://Rezghool:7077 --cores 2 --memory 4g
commmand jps : Use jps on master to see the instances given they all run on the same machine, e.g. localhost).
./sbin/stop-all.sh
--num-executors 7 \
--conf spark.executor.cores=4 \
  --conf spark.executor.instances=10 \


lttng create

lttng enable-event -l -a  --filter 'logger_name == "org.apache.spark.examples.MyCustomSparkListener"'

lttng start

${SPARK_HOME}/bin/spark-submit \
--verbose \
--class org.apache.spark.examples.ml.JavaKMeansExample \
--master spark://Rezghool:7077 \
 --conf spark.dynamicAllocation.enabled=true \
  --conf spark.shuffle.service.enabled=true \
/opt/spark/examples/target/scala-2.12/jars/spark-examples_2.12-3.4.0.jar 6

lttng stop



${SPARK_HOME}/bin/spark-submit \
--verbose \
  --class org.apache.spark.examples.SparkPi \
--deploy-mode client \
--num-executors 16 \
--conf spark.executor.cores=4 \
/opt/spark/examples/target/scala-2.12/jars/spark-examples_2.12-3.4.0.jar 1000


${SPARK_HOME}/bin/spark-submit \
  --class org.apache.spark.examples.graphx.AggregateMessagesExample \
--deploy-mode client \
--num-executors 16 \
--conf spark.executor.cores=4 \
/opt/spark/examples/target/original-spark-examples_2.12-3.4.0.jar


${SPARK_HOME}/bin/spark-submit \
--verbose \
--class org.apache.spark.examples.ml.JavaKMeansExample \
--deploy-mode client \
--num-executors 16 \
--conf spark.executor.cores=4 \
/opt/spark/examples/target/scala-2.12/jars/spark-examples_2.12-3.4.0.jar 1

```
The --conf spark.dynamicAllocation.enabled=true option in the spark-submit command enables Spark's dynamic allocation feature when running your application. Dynamic allocation allows Spark to automatically adjust the number of executors allocated for an application based on the workload, so it can scale up or down the executors dynamically to improve resource utilization and handle varying workloads more efficiently.

When dynamic allocation is enabled, Spark can add executors when there is a backlog of pending tasks and remove executors when they have been idle for a specified amount of time. This feature is particularly useful in shared Spark clusters where resource optimization is crucial.

To make dynamic allocation work effectively, you typically also need to enable the external shuffle service by setting spark.shuffle.service.enabled to true. This service keeps track of the shuffle files of executor tasks so that the data is not lost when executors are dynamically removed, allowing future executors to still access those shuffle files.

Here's a brief explanation of what these configurations do:

spark.dynamicAllocation.enabled=true: Enables dynamic allocation of executors.
spark.shuffle.service.enabled=true: Enables the external shuffle service, which is required for dynamic allocation to work properly because it allows shuffle data to persist beyond the lifespan of individual executors.


To install Yarn in a cluster, you typically need to have Hadoop installed, as Yarn (Yet Another Resource Negotiator) is part of the Hadoop ecosystem and serves as its cluster management component. Here’s a general guide to get you started with installing a Hadoop cluster with Yarn. This guide assumes you're working with Ubuntu or a similar Debian-based distribution.

### Step 1: Install Java

Yarn requires Java to be installed. You can install Java with the following command:

```bash
sudo apt-get update
sudo apt-get install openjdk-8-jdk
```

Check the Java installation by running:

```bash
java -version
```

### Step 2: Download and Install Hadoop

1. Download Hadoop from the official site: http://hadoop.apache.org/releases.html
2. Extract the Hadoop archive:

```bash
tar -xzvf hadoop-x.y.z.tar.gz
```

3. Move the extracted Hadoop directory to a suitable location:

```bash
sudo mv hadoop-x.y.z /usr/local/hadoop
```

### Step 3: Configure Hadoop and Yarn

You need to edit several configuration files in your Hadoop directory to set up Hadoop and Yarn. The main files are:

- `etc/hadoop/hadoop-env.sh`
- `etc/hadoop/core-site.xml`
- `etc/hadoop/hdfs-site.xml`
- `etc/hadoop/mapred-site.xml`
- `etc/hadoop/yarn-site.xml`

The specific configurations will depend on your cluster setup, network, and requirements. The Hadoop documentation provides detailed instructions for configuring these files: https://hadoop.apache.org/docs/stable/hadoop-project-dist/hadoop-common/ClusterSetup.html

### Step 4: Format the NameNode

Before starting your Hadoop cluster for the first time, you need to format the HDFS filesystem:

```bash
/usr/local/hadoop/bin/hdfs namenode -format
```

### Step 5: Start Hadoop and Yarn

You can start the Hadoop daemons with the following command:

```bash
/usr/local/hadoop/sbin/start-dfs.sh
/usr/local/hadoop/sbin/start-yarn.sh
```

### Step 6: Verify the Installation

Check if the Hadoop and Yarn daemons are running:

```bash
jps
```

You should see the NameNode, DataNode, ResourceManager, and NodeManager among the listed processes.

### Step 7: Access the Yarn and Hadoop Web UIs

- Yarn ResourceManager UI is usually available at http://your_master_node:8088
- Hadoop NameNode UI is usually available at http://your_master_node:9870

### Getting Yarn Nodes

To get the list of nodes managed by Yarn, use the following command:

```bash
/usr/local/hadoop/bin/yarn node -list
```

This guide provides a high-level overview of setting up a Hadoop cluster with Yarn. For a production environment, you'll need to carefully plan your cluster, considering factors like hardware specifications, network configurations, security, and backup strategies. Additionally, for multi-node setups, you would need to replicate some of the configuration steps on each node and ensure proper network connectivity between them.




Result: Successed
--num-executors 16 \
--conf spark.executor.cores=4 \

Result: failed
--num-executors 16 \
--conf spark.executor.cores=8 \



Result: failed
--num-executors 8 \
--conf spark.executor.cores=8 \


Result: failed
--num-executors 2 \
--conf spark.executor.cores=8 \



Cluster Manager allocates resources across the other applications. I think the issue is with bad optimized configuration. You need to configure Spark on the Dynamic Allocation. In this case Spark will analyze cluster resources and add changes to optimize work.

You can find all information about Spark resource allocation and how to configure it here: http://site.clairvoyantsoft.com/understanding-resource-allocation-configurations-spark-application/


#Attention: 
change java verison to 11 for spark 


The error message you're encountering from the YARN application state monitor indicates that the resource request for your Spark application exceeds the maximum allowed allocation in your YARN cluster. Specifically, the request for 8 virtual cores (vCores) per container is beyond the maximum allowed allocation of 4 vCores. The maximum allocation is determined by the YARN scheduler based on the resources of registered NodeManagers, which might be less than or equal to the configured maximum allocation.


## For adding a new graph to Trace compass:
### Core
/org.eclipse.tracecompass.incubator.spark_test1.core

/org.eclipse.tracecompass.incubator.spark_test1.core/src/org/eclipse/tracecompass/incubator/internal/spark_test1/core/analysis/SparkAnalysisModule.java
/org.eclipse.tracecompass.incubator.spark_test1.core/src/org/eclipse/tracecompass/incubator/internal/spark_test1/core/analysis/TaskXYDataProviderFactory.java




### Ui

/org.eclipse.tracecompass.incubator.spark_test1.ui

here add a new class for view and import the data provider from core

 in /org.eclipse.tracecompass.incubator.spark_test1.ui/META-INF/MANIFEST.MF add veiws then brows class org.eclipse.tracecompass.incubator.internal.spark_test1.ui.views.TaskPerExecutorView
 

### shuffleReadFetchWaitTime
The shuffleReadFetchWaitTime parameter in Spark measures the total time spent waiting for shuffle data to be fetched from remote locations. It is a critical metric for understanding the performance of shuffling operations in Spark applications, as longer wait times can indicate bottlenecks in network communication or issues with data distribution across the cluster. Optimizing this metric can lead to more efficient data processing by reducing idle time waiting for data.

### broadcast
In Spark, a "broadcast" refers to the process of distributing a read-only variable to all nodes in the cluster to optimize the efficiency of joins and data processing. The log message indicates that a broadcast variable (identified by "broadcast 61") was created, likely to share data across tasks without requiring shuffle operations, thus reducing network I/O and improving job execution time. This operation is managed by Spark's DAGScheduler and is a key optimization technique for distributed computing in Spark.

### Shuffle data
Shuffle data in Apache Spark refers to the data that needs to be transferred across different nodes in a cluster for completing operations that involve grouping or aggregating data across partitions. This happens, for example, during operations like reduceByKey or groupBy. The shuffle process is a key phase in distributed computations, where data is redistributed across the cluster so that each node can work on the data it needs to process. The efficiency of shuffling can significantly affect the performance of Spark applications due to network and disk I/O involved.

### executorRunTime vs taskDuration
executorRunTime measures the total time the executor spent running the task, including both computation time and reading from/writing to HDFS or other storage systems. taskDuration, on the other hand, is the total time from when the task was launched until it completed, which includes not only the executorRunTime but also time spent scheduling the task, fetching shuffle data if necessary, and any other overhead before and after execution. Essentially, taskDuration encompasses executorRunTime along with all other overheads involved in task execution.

### executorDeserializeCPU
`executorDeserializeCPU` measures the CPU time taken specifically for deserializing task data on the executor before the task can actually start running its computation. It's a part of the overhead before the actual execution (`executorRunTime`) begins and is not included in the `executorRunTime`. Therefore, `executorDeserializeCPU` contributes to the `taskDuration` by adding to the pre-execution overhead. In summary, `taskDuration` includes all phases of a task's lifecycle, including deserialization (`executorDeserializeCPU`), execution (`executorRunTime`), and any other overheads, making it a comprehensive measure of task time.


### jvmGCTime
jvmGCTime refers to the amount of time the Java Virtual Machine (JVM) spent performing garbage collection (GC) during the execution of a task. Garbage collection is the process of identifying and disposing of objects that are no longer needed by the application, which helps in managing memory more efficiently. High jvmGCTime values can indicate that the task involved heavy object creation and disposal, potentially impacting performance by increasing overall task execution time.


### executorCPUTime
`executorCPUTime` measures the total CPU time consumed by the executor for running the task. This includes the time spent on executing the task's code and any other CPU-bound operations it performs. It's a measure of the actual CPU resources consumed by the task, distinct from wall-clock time (`executorRunTime`), which includes idle waits. Monitoring `executorCPUTime` can help in understanding the computational complexity of the tasks and optimizing resource utilization.



### executorRunTime vs executorCPUTime
`executorRunTime` measures the total time taken by a task from start to finish, including both computation time and waiting time for resources or data. It's the wall-clock time for task execution. `executorCPUTime`, on the other hand, measures only the CPU time consumed by the task for computation, excluding any I/O waiting time, data shuffle time, or time spent waiting for other resources. It provides a measure of how much CPU work the task did, offering insights into the task's computational efficiency.


### resultSerializationTime vs executorDeserializeTime

`resultSerializationTime` measures the time taken to serialize the result of a task before sending it back to the driver, indicating how long it takes to prepare the result for transmission over the network. `executorDeserializeTime`, in contrast, tracks the time spent to deserialize the task data at the executor side before the task execution begins. Essentially, `resultSerializationTime` is about converting task output to a network-transmittable form, while `executorDeserializeTime` is about converting received data into a form that the executor can process for task execution.

### so executorDeserializeTime is not part of executorRunTime?
Yes, `executorDeserializeTime` is a separate metric that measures the time taken to deserialize task data before execution can begin on the executor. It does not directly contribute to `executorRunTime`, which measures the actual running time of the task execution itself. The deserialization time is part of the overhead incurred before the task's computation starts, while the execution time is focused solely on the computation part of the task.

### Why taskDuration > executorRunTime
The `executorRunTime` from Spark metrics and the task duration reported by the Spark listener may differ due to various factors involved in task execution. The `executorRunTime` specifically measures the time spent executing the task code on the executor, excluding overheads like scheduling delays, data serialization/deserialization, and network I/O. In contrast, task duration from the Spark listener includes all overheads, from the moment the task was scheduled to its completion, hence offering a more comprehensive view of the task's lifecycle. This broader scope is why task duration can be longer than `executorRunTime`.


#### noted: 
In your 1 stage DAG you are simply creating the RDD with the collection and in the second RDD, you shuffle the RDD using partitionBy so your data is shuffled over the cluster. So due to shuffling the data your process is slow for the 2nd stage.

Difference between ShuffledRDD, MapPartitionsRDD and ParallelCollectionRDD:

#### ShuffledRDD : 
ShuffledRDD is created while the data is shuffled over the cluster. If you use any transformation(e.g. join,groupBy,repartition, etc.) which shuffles your data it will create a shuffledRDD.

#### MapPartitionsRDD :
MapPartitionsRDD will be created when you use mapPartition transformation.

#### ParallelCollectionRDD :
ParallelCollectionRDD is created when you create the RDD with the collection object.

### General
executorRunTime measures the total time a task spends running on the executor, including computation and reading from or writing to HDFS or other storage systems. executorDeserializeTime, on the other hand, measures the time taken to deserialize the task data sent from the driver to the executor before the task can begin execution. While executorRunTime encompasses the core computation and I/O time, executorDeserializeTime is specifically about the overhead before the actual computation starts.
jvmGCTime refers to the amount of time the Java Virtual Machine (JVM) spent performing garbage collection (GC) during the execution of a task. Garbage collection is the process of identifying and disposing of objects that are no longer needed by the application, which helps in managing memory more efficiently. High jvmGCTime values can indicate that the task involved heavy object creation and disposal, potentially impacting performance by increasing overall task execution time.


#### Example: 

#### From task metric
shuffleReadFetchWaitTime=0;

shuffleWriteBytesWrtietime=0;

jvmGCTime=249; 

executorDeserializeCPUTime=709177696;

executorDeserializeTime=1844;

executorCPUTime=3060031425;

executorRunTime=7172; 

resultSerializationTime=1;


#### From task Info           
gettingResultTime=0;

taskDuration=9227;



These metrics provide detailed insights into the performance and behavior of a Spark task:

- `shuffleReadFetchWaitTime`: Time spent waiting for shuffle data, indicative of network or IO bottlenecks in shuffle operations. Here, no time was spent waiting, suggesting efficient shuffle data retrieval.
- `shuffleWriteBytesWrtietime` & `gettingResultTime`: These show the time to write shuffle data and retrieve results, respectively. Both are zero, indicating no significant shuffle write time or delay in getting results.
- `jvmGCTime`: Time the JVM spent in garbage collection during this task, which can impact task performance.
- `executorDeserializeTime` & `executorDeserializeCPUTime`: These represent the time and CPU time spent on deserializing task data on the executor, impacting task startup time.
- `executorCPUTime`: Total CPU time consumed by the task, reflecting the actual CPU resources used.
- `executorRunTime`: The execution time of the task within the executor, excluding JVM GC time or any overhead introduced by Spark's execution engine.
- `taskDuration`: Total duration of the task from start to end, including all overheads and processing time.
- `launchTime` & `taskEndTime`: Timestamps marking the start and end of the task execution.
- `resultSerializationTime`: Time taken to serialize the task's result before sending it back to the driver.

`taskDuration` is the overall time from the task's start to its completion, potentially including time spent waiting for resources or other overheads not directly related to computation. It's usually the broadest measure of task time, encompassing all other time metrics.


cpuRate = executorCpuTime / executorRunTime
serRate = resultSerializationTime / executorRunTime
gcRate = jvmGCTime / executorRunTime
shuffleFetchRate = shuffleReadFetchWaitTime / executorRunTime
shuffleWriteRate = shufflesWrtietime / executorRunTime


### TASK STATUS:

Each task in Spark represents a unit of work sent to the executor. Spark tasks themselves do not inherently have states like "map," "reduce," or "group by" because these are transformations or actions applied on RDDs (Resilient Distributed Datasets) or DataFrames


Apache Spark provides a rich set of transformations, which are operations on RDDs (Resilient Distributed Datasets) that return a new RDD. These transformations are lazily evaluated, meaning they are not executed immediately but rather wait until an action is performed. Here's a comprehensive list of the core transformations available in Spark:

### Narrow Transformations (No Shuffle Required)
- **`map(func)`**: Returns a new RDD by applying a function to each element.
- **`filter(func)`**: Returns a new RDD containing only the elements that satisfy a predicate.
- **`flatMap(func)`**: Similar to `map`, but each input item can be mapped to 0 or more output items.
- **`mapPartitions(func)`**: Similar to `map`, but runs separately on each partition (block) of the RDD.
- **`mapPartitionsWithIndex(func)`**: Similar to `mapPartitions`, but also provides a function with an index of the partition.
- **`sample(withReplacement, fraction, seed)`**: Sample a fraction of the data, with or without replacement.
- **`union(otherDataset)`**: Returns a new RDD containing elements from the source dataset and the other dataset.
- **`intersection(otherDataset)`**	Return a new RDD that contains the intersection of elements in the source dataset and the argument.
- 
### Wide Transformations (Shuffle Required)
- **`groupBy(func)`**: Groups the elements of the RDD according to a specified function.
- **`reduceByKey(func)`**: When called on a dataset of `(K, V)` pairs, returns a dataset of `(K, V)` pairs where the values for each key are aggregated using the given reduce function.
- **`aggregateByKey(zeroValue)(seqOp, combOp)`**: Aggregate the values of each key, using given combine functions and a neutral "zero value".
- **`sortByKey(ascending=True)`**: When called on an RDD of `(K, V)` pairs, returns an RDD sorted by the keys.
- **`join(otherDataset)`**: When called on datasets of `(K, V)` and `(K, W)` pairs, returns a dataset of `(K, (V, W))` pairs with all pairs of elements for each key.
- **`cogroup(otherDataset)`**: When called on datasets of `(K, V)` and `(K, W)`, groups data from both datasets by key.
- **`cartesian(otherDataset)`**: When called on datasets of types T and U, returns a dataset of `(T, U)` pairs (all pairs of elements).
- **`distinct()`**: Returns a new dataset that contains the distinct elements of the source dataset.
- **`repartition(numPartitions)`**: Reshuffle the data in the RDD randomly to create either more or fewer partitions and balance it across them.
- **`coalesce(numPartitions)`**: Decrease the number of partitions in the RDD to a specified number.
- **`flatMapValues(func)`**: Pass each value in the key-value pair RDD through a `flatMap` function without changing the keys; this also similarly applies for `mapValues`.

This list covers the core transformations. Spark also provides additional transformations for specialized use cases, including operations on pair RDDs (key-value pairs) and double RDDs (RDDs with numerical data), as well as transformations specific to DataFrames and Datasets in Spark SQL.


### Stages:
A stage represents a group of tasks that can be executed together without shuffling data across the partitions. Stages are the result of shuffling operations. Each stage contains a sequence of transformations that can be performed on partitions without needing data from other partitions.
Stages are separated by transformations that require a shuffle of data, such as groupBy or reduceByKey.

### Jobs:
A job is triggered by an action. It represents the entire computation required to produce the result for the action. A job consists of one or more stages.

### Tasks:
A task is a unit of work that is sent to an executor. Each stage is composed of tasks, where each task corresponds to a combination of data and computation on that data. A task is Spark's smallest unit of work and is executed on a single executor.
In summary, transformations define a set of instructions to be applied to data, which are organized into stages for efficiency. Stages are grouped into jobs when an action is called, and jobs are broken down into tasks that are distributed across the Spark cluster for execution.

### Categorization
RDD Actions: More low-level operations for working directly with distributed data. These actions are fundamental for RDD manipulation.
DataFrame Actions: Higher-level operations that allow for more complex computations and aggregations, often with optimized execution plans.

Apache Spark actions are operations that trigger computation over RDDs, DataFrames, and Datasets to return results to the driver program or write to storage. Actions are the point at which Spark starts executing the code in a cluster to return results or save data. Here's a list of commonly used actions in Spark:

### RDD Actions
- **collect()**: Returns all the elements of the dataset as an array at the driver program.
- **count()**: Returns the number of elements in the dataset.
- **first()**: Returns the first element of the dataset.
- **take(n)**: Returns an array with the first n elements of the dataset.
- **reduce(func)**: Aggregates the elements of the dataset using a function `func` (which takes two arguments and returns one).
- **aggregate(zerovalue, seqOp, combOp)**: Returns a more general form of aggregation than `reduce()`. The zero value is used for initialization, `seqOp` for aggregation within a partition, and `combOp` to combine the results from different partitions.
- **foreach(func)**: Applies a function `func` to all elements of the dataset.
- **saveAsTextFile(path)**: Writes the dataset to a text file at the specified path.
- **countByKey()**: (For RDDs of type `(K, V)`) Returns a hashmap of keys and their counts.
- **collectAsMap()**: (For RDDs of type `(K, V)`) Returns the dataset as a map.
- **takeSample(withReplacement, num, seed)**: Return an array with a random sample of `num` elements of the dataset.
- **countByValue()**: Returns the count of each unique value in the RDD as a map of (value, count).
- **fold(zeroValue)(func)**: Aggregate the elements of each partition and then the results for all partitions.
- **top(n)**: Returns the top n elements from an RDD.
- **count()**: Returns the number of rows in the DataFrame.
 - **foreachPartition**: is an action because it causes the execution of the RDD transformations that have been defined up to that point in the program. It does not return a new RDD (like transformations do) but instead applies a function to each partition of the RDD to perform side effects (e.g., writing to external storage).


### DataFrame and Dataset Actions
- **show()**: Displays the top rows of the DataFrame in a tabular form.
- **count()**: Returns the number of rows in the DataFrame or Dataset.
- **collect()**: Collects the rows of the DataFrame or Dataset and returns them as an array of Rows to the driver program.
- **take(n)**: Returns the first n rows as an array.
- **first()** and **head()**: Return the first row.
- **save()**: Saves the content of the DataFrame to a data source.
- **write()**: Returns a `DataFrameWriter` object for configuring and executing write operations supported by the format.
- **foreach(func)**: Applies a function `func` to each Row.
- **reduce(func)**: Reduces the elements of this Dataset using the specified binary function. (Available in Datasets)
- **agg(exprs)**: Aggregates on the entire DataFrame without groups. (Available in DataFrames)
- **write()**: Actions that output data to storage systems like DFS, HDFS, etc.
- **agg()**: Aggregates on the entire DataFrame with a collection of aggregation functions like count(), sum(), etc.


### Actions Common to Both
Some actions like count() and collect() are common to both RDDs and DataFrames but are executed differently under the hood due to the different nature of RDDs and DataFrames. DataFrames have optimizations through Catalyst optimizer and Tungsten execution engine.

Spark's transformations and actions are lazy and eager, respectively. Transformations define a new computation and are not executed until an action is called. Actions trigger the execution of the computation defined by a series of transformations and return results or write to storage.


#### Capturing Actions
Actions in Spark trigger the computation of RDDs, DataFrames, or Datasets. These actions are easier to capture because they result in a job submission to the cluster. You can log details about actions using the following event listeners in your custom Spark listener:

#### onJobStart: 
This method is called when a job starts. An action triggers a job in Spark. By implementing this method, you can log the action that initiated the job. The SparkListenerJobStart event provides details such as the job ID, stage info, and submission time, which can indirectly give you information about the action.

#### onJobEnd: 
This method is called when a job ends. It provides information such as the job result, which can help you determine the outcome of the action.

### Capturing Transformations
Since transformations are lazy and do not cause any computation by themselves, they are not directly observable through Spark listeners. However, you can infer the presence of certain transformations indirectly through stage and task submissions:

##### onStageSubmitted and onStageCompleted:
These methods are called when stages are submitted and completed, respectively. Each stage in Spark corresponds to a set of transformations that are grouped together for execution. By logging these events, you can infer that a series of transformations were executed as part of a stage. However, the specific transformations are not directly provided.

##### onTaskStart and onTaskEnd:
Tasks are the smallest units of work in Spark, executed within stages. By logging task start and end events, you can get details at a finer granularity about the computation performed as part of a stage. The task info might give clues about the transformations, especially if you customize the task description to include transformation details programmatically.


This JSON snippet represents the completion event of a Spark stage, as recorded by Spark's event logging mechanism. It provides a wealth of information about the stage, including its ID, name, the tasks it comprised, and performance metrics. Here's a breakdown of some key components and what you can infer regarding the different states of a Spark task:

1. **Stage Info**: Contains details about the stage, such as:
   - **Stage ID** and **Stage Attempt ID**: Unique identifiers for the stage and its attempt number, respectively.
   - **Stage Name**: The operation leading to this stage's creation, often indicative of the RDD action or transformation that triggered it (e.g., "reduce at MLUtils.scala:94").
   - **Number of Tasks**: The total tasks in this stage, which directly relates to the parallelism level of this stage.

2. **RDD Info**: Provides details on the RDDs involved in this stage, including their lineage (parent IDs), storage levels, and partitioning info. Each RDD's name and scope can hint at the transformations applied (e.g., map, Scan text, DeserializeToObject).

3. **Parent IDs**: Lists the parent stages of this stage, if any, indicating the DAG (Directed Acyclic Graph) dependencies among stages.

4. **Details**: A stack trace of the method calls leading to this stage's execution, offering a detailed view of the operations performed.

5. **Submission Time** and **Completion Time**: Timestamps marking the start and end of the stage, useful for performance analysis and identifying bottlenecks.

6. **Accumulables**: Key performance metrics gathered during stage execution, such as:
   - Executor de/serialization times and CPU times, offering insight into the computational overhead.
   - JVM GC time, indicating the impact of garbage collection on stage execution.
   - Input metrics (bytes and records read), showing data processing volumes.
   
### Inferring Task States

From the information available in such a log snippet, you can infer several states of Spark tasks within the stage:

- **Pending**: Before the stage's "Submission Time", tasks are in the queue waiting to be scheduled.
- **Running**: Between "Submission Time" and "Completion Time", tasks are being executed.
- **Completed**: After the "Completion Time", tasks have finished execution.


However, this specific log snippet doesn't directly provide task-level states like "map", "reduce", "group by", etc., as these are part of the stage's broader computation context. To link tasks to such states, you'd typically refer to the stage name, RDD lineage, and operations listed in "Details" and "RDD Info".

### Analyzing Task Operations

To analyze what operations (transformations and actions) are running within your custom Spark listener logs, you would:

1. **Parse the Stage Name**: It often contains the operation triggering the stage.
2. **Examine RDD Info**: The "Name" and "Scope" can provide clues about the transformations applied.
3. **Look at "Details"**: The stack trace might reveal higher-level actions or transformations not evident from the stage name or RDD info alone.

This approach helps in identifying the computational work being performed and linking it to task and stage metrics for performance analysis.


The concept of an RDD, or Resilient Distributed Dataset, is foundational to Apache Spark, serving as its primary data abstraction. RDDs represent a collection of items distributed across many nodes in the cluster that can be manipulated in parallel. They offer a way to perform read-only, partitioned transformations of data across a distributed computing environment. Let's break down the key characteristics and capabilities of RDDs for a clearer understanding:

### 1. Resilient
- **Fault-tolerant**: RDDs have built-in fault tolerance. They can rebuild lost data on failure using lineage, a record of how the RDD was constructed from other datasets (by transformations like map, filter, etc.).

### 2. Distributed
- **Distributed Data**: The dataset is distributed across multiple nodes in a cluster, allowing for parallel operations on the data. This distribution enables Spark to perform large-scale computations efficiently.

### 3. Dataset
- **Immutable Collection**: RDDs are immutable, meaning once you create an RDD, you cannot change it. However, you can transform its data by applying transformations (e.g., map, filter) to create new RDDs.

### Key Features of RDDs:
- **Immutability and Partitioning**: Immutability helps with consistency in computations, while partitioning allows data to be processed in parallel.
- **Lazy Evaluation**: Transformations on RDDs are lazily evaluated, meaning computation on RDDs only happens when an action (e.g., count, collect) is called. This design helps optimize the overall data processing pipeline.
- **Persistence**: Users can persist or cache RDDs in memory or on disk across operations, optimizing the performance of computations that reuse the RDD data.
- **Parallel Operations**: Operations on RDDs can automatically run in parallel, with Spark handling the distribution of data and the scheduling of tasks.

### Creating RDDs
RDDs can be created through:
- Loading an external dataset.
- Distributing a collection of objects (e.g., a list or set in your driver program).

### Transformations and Actions
- **Transformations** create a new RDD from an existing one, such as `map`, `filter`, `reduceByKey`.
- **Actions** trigger the execution of the computation, such as `count`, `collect`, `saveAsTextFile`.

From the given JSON snippet of a SparkListenerStageCompleted event, we can deduce the transformations but not the actions directly. Actions in Spark trigger the computation and are usually at the end of a chain of transformations; they're not part of the stage info directly but are implied by the stage's execution. Here's an analysis based on the provided stage info:


### Example
Here's a simple example to illustrate creating an RDD and performing operations:

```scala
val sc = new SparkContext(...) // SparkContext initialization

// Creating an RDD from a list
val data = Array(1, 2, 3, 4, 5)
val rdd = sc.parallelize(data)

// Transformation: doubling the numbers
val doubledRdd = rdd.map(x => x * 2)

// Action: collecting the results
val result = doubledRdd.collect() // This returns Array(2, 4, 6, 8, 10)
```

In this example, `sc.parallelize` creates an RDD from a local Scala collection. The `map` operation is a transformation that creates a new RDD, and `collect` is an action that triggers the computation and returns the result to the driver program.
Creating an RDD (Resilient Distributed Dataset) in Apache Spark can be done in several ways, each suitable for different scenarios. Here are the primary methods for creating RDDs:

### 1. Parallelizing an Existing Collection
This method involves distributing an existing collection of objects (e.g., an array or a list in Scala/Python) across the cluster.

**Scala Example:**
```scala
val data = Array(1, 2, 3, 4, 5)
val rdd = sparkContext.parallelize(data)
```

**Python Example:**
```python
data = [1, 2, 3, 4, 5]
rdd = sparkContext.parallelize(data)
```

### 2. Reading Data from External Storage
RDDs can be created by loading data from external storage systems like HDFS, S3, HBase, or files from a local filesystem.

**Scala Example:**
```scala
val rddFromFile = sparkContext.textFile("hdfs://path/to/file.txt")
```

**Python Example:**
```python
rdd_from_file = sparkContext.textFile("hdfs://path/to/file.txt")
```

### 3. Transforming an Existing RDD
New RDDs can also be created by applying transformations (e.g., `map`, `filter`, `reduceByKey`) to an existing RDD.

**Scala Example:**
```scala
val originalRDD = sparkContext.parallelize(Array(1, 2, 3))
val newRDD = originalRDD.map(x => x * 2)
```

**Python Example:**
```python
original_rdd = sparkContext.parallelize([1, 2, 3])
new_rdd = original_rdd.map(lambda x: x * 2)
```

### 4. From Data Sources Using DataFrames or Datasets API
While technically this creates a DataFrame or Dataset, you can convert these to RDDs. This method is common when working with structured data sources.

**Scala Example:**
```scala
val df = sparkSession.read.json("path/to/jsonfile.json")
val rddFromDF = df.rdd
```

**Python Example:**
```python
df = sparkSession.read.json("path/to/jsonfile.json")
rdd_from_df = df.rdd
```

### 5. From Other RDDs Using Pair RDD Functions
Pair RDDs are a special type of RDDs to work with key-value pairs. They are created by mapping an existing RDD to key-value pairs.

**Scala Example:**
```scala
val listRdd = sparkContext.parallelize(List("Dog", "Cat", "Rabbit"))
val pairRdd = listRdd.map(a => (a, a.length))
```

**Python Example:**
```python
list_rdd = sparkContext.parallelize(["Dog", "Cat", "Rabbit"])
pair_rdd = list_rdd.map(lambda a: (a, len(a)))
```

## Determine the actions
To determine the actions and transformations directly from Spark listener logs, you generally need to look at the stage's purpose (often indicated by the stage name or the terminal operation like reduce, collect, count, etc.) and the lineage of RDDs involved in that stage, which tells you the transformations applied.


These methods form the basis of RDD creation in Spark, providing a flexible approach to distribute and manipulate data across a cluster for parallel processing.
Understanding RDDs is crucial for effective programming with Apache Spark, as they are the backbone of Spark's distributed data processing capabilities.

# New challenge: 
## Waitng time for tasks
## Pending time for tasks
## Diffrent state of task in running (map, reduce, groupby)



# DEscribe Dagsceduler graph: 
https://stackoverflow.com/questions/40590028/what-do-the-blue-blocks-in-spark-stage-dag-visualisation-ui-mean
Each blue box is the steps of Apache Spark job.

You are asking about the WholeStageCodegen this stuff is:

Whole-Stage Code Generation (aka WholeStageCodegen or WholeStageCodegenExec) fuses multiple operators (as a subtree of plans that support codegen) together into a single Java function that is aimed at improving execution performance. It collapses a query into a single optimized function that eliminates virtual function calls and leverages CPU registers for intermediate data.

You can see details here SPARK-12795

The exchange means the Shuffle Exchange between jobs in more details:

ShuffleExchange is a unary physical operator. It corresponds to Repartition (with shuffle enabled) and RepartitionByExpression logical operators (as translated in BasicOperators strategy).

All this information you can get in your code using the explain command

Each step shows you what your dataframe is going to do, this is good to find if your logic is right. If you want more details about Spark UI I suggest you to see this presentation of Spark Summit and read this article about the execution planning.

These information will show you much more about your doubt.


#### Complex example: 

As an example, the Alternating Least Squares (ALS) implementation in MLlib computes an approximate product of two factor matrices iteratively. This involves a series of map, join, groupByKey operations under the hood.



So, I experimented with the Spark Standalone cluster myself a bit, and this is what I noticed.

My intuition that muliple executors can be run inside a worker, by tuning executor cores was indeed correct. Let us say, your worker has 16 cores. Now if you specify 8 cores for executors, Spark would run 2 executors per worker.

How many executors run inside a worker also depend upon the executor memory you specify. For example, if worker memory is 24 GB, and you want to run 2 executors per worker, you cannot specify executor memory to be more than 12 GB.

A worker's memory can be limited when starting a slave by specifing the value for optional parameter--memory or by changing the value of SPARK_WORKER_MEMORY. Same with the number of cores (--cores/SPARK_WORKER_CORES).

If you want to be able to run multiple jobs on the Standalone Spark cluster, you could use the spark.cores.max configuration property while doing spark-submit. For example, like this.

spark-submit <other parameters> --conf="spark.cores.max=16" <other parameters>
So, if your Standalone Spark Cluster allows 64 cores in total, and you give only 16 cores to your program, other Spark jobs could use the remaining 48 cores.

Here's a brief overview:

Local Mode (--master local): Spark runs both the driver and executors in the same JVM process. This mode is intended for development and testing, allowing you to run Spark jobs quickly without needing a cluster. You can optionally specify the number of threads for Spark to use by specifying local[N], where N is the number of threads. local[*] uses as many threads as the number of processors available to the JVM.

Deploy Mode (--deploy-mode): This setting determines where the Spark driver program runs when you're using a cluster manager. It has two options:

Client Mode (--deploy-mode client): The driver runs on the machine that was used to submit the application. In client mode, the output of the application is sent to the console. It's useful for interactive and debugging purposes.
Cluster Mode (--deploy-mode cluster): The driver runs on a node in the cluster. In cluster mode, the cluster manager is responsible for the allocation of system resources.
So, when you specify --master local and also use --deploy-mode client, the --deploy-mode option is essentially ignored because local mode does not involve a cluster manager to negotiate resources. Your application just runs in a single JVM on your local machine. The concept of client vs. cluster mode is relevant only when you are using a cluster manager like YARN, Mesos, Standalone, or Kubernetes to manage the allocation of resources across the cluster.

In summary, specifying --master local is sufficient for running Spark in local mode, and the application will run on your local machine with resources (CPU, memory) determined by your local machine's capacity and any specific configurations you provide.
