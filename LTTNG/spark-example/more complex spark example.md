

Why does Spark job fail with "Exit code: 52"

```bash
pgrep -a lttng-sessiond

cd /opt/spark/
 
./sbin/start-history-server.sh

PATH=$PATH:/usr/local/hadoop/sbin
bash start-dfs.sh
bash start-yarn.sh


./build/mvn -DskipTests clean package -rf :spark-examples_2.12

cd /opt/spark/
./build/mvn -DskipTests clean package


lttng view > output-lttng.log 2>&1
  ```

https://sparkbyexamples.com/spark/different-types-of-issues-while-running-spark-projects/#out-of-memory-exceptions


   ```bash


${SPARK_HOME}/bin/spark-submit \
   --verbose \
   --class org.apache.spark.examples.ml.JavaKMeansExample \
   --deploy-mode client \
   /opt/spark/examples/target/scala-2.12/jars/spark-examples_2.12-3.4.0.jar 8


${SPARK_HOME}/bin/spark-submit \
   --verbose \
   --class org.apache.spark.examples.ml.JavaKMeansExample \
   --master local[2] \
   /opt/spark/examples/target/scala-2.12/jars/spark-examples_2.12-3.4.0.jar 1



  bin/run-example --files ${jaas_path}/kafka_jaas.conf,${keytab_path}/kafka.service.keytab \
       --driver-java-options "-Djava.security.auth.login.config=${path}/kafka_driver_jaas.conf" \
       --conf \
       "spark.executor.extraJavaOptions=-Djava.security.auth.login.config=./kafka_jaas.conf" \
       --master yarn
       streaming.JavaDirectKerberizedKafkaWordCount broker1-host:port,broker2-host:port \
       consumer-group topic1,topic2


${SPARK_HOME}/bin/spark-submit \
   --verbose \
   --class org.apache.spark.examples.streaming.JavaNetworkWordCount \
   --master local[2] \
   /opt/spark/examples/target/scala-2.12/jars/spark-examples_2.12-3.4.0.jar \
localhost 9999




${SPARK_HOME}/bin/spark-submit \
   --verbose \
   --class org.apache.spark.examples.ml.JavaModelSelectionViaCrossValidationExample \
   --deploy-mode client \
   /opt/spark/examples/target/scala-2.12/jars/spark-examples_2.12-3.4.0.jar





   ${SPARK_HOME}/bin/spark-submit \
   --verbose \
   --class org.apache.spark.examples.ml.JavaPowerIterationClusteringExample \
   --deploy-mode client \
   /opt/spark/examples/target/scala-2.12/jars/spark-examples_2.12-3.4.0.jar

   ```


   ```bash
     ${SPARK_HOME}/bin/spark-submit \
   --verbose \
   --class org.apache.spark.examples.JavaPageRank2 \
  --conf spark.task.maxFailures=2 \
spark.blacklist.enabled=true \
   --master local[2] \
   /opt/spark/examples/target/scala-2.12/jars/spark-examples_2.12-3.4.0.jar \
   500 100 10
   ```


   ```bash
    ${SPARK_HOME}/bin/spark-submit \
   --verbose \
   --class org.apache.spark.examples.JavaPageRank2 \
	--deploy-mode client \
  --conf spark.blacklist.enabled=true \
   /opt/spark/examples/target/scala-2.12/jars/spark-examples_2.12-3.4.0.jar \
   500 40 100

   ```

  ```bash

pgrep -a lttng-sessiond


PATH=$PATH:/usr/local/hadoop/sbin
start-all.sh
bash start-dfs.sh
bash start-yarn.sh


export HDFS_NAMENODE_USER="hadoop"
export HDFS_DATANODE_USER="hadoop"
export HDFS_SECONDARYNAMENODE_USER="hadoop"
export YARN_RESOURCEMANAGER_USER="hadoop"
export YARN_NODEMANAGER_USER="hadoop"


build/mvn -Pyarn -Phadoop-3.3 -Dhadoop.version=3.3.6 -DskipTests clean package

ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABgQC9W6rd58oEaCxE4bgJRpBpEVPoXQhw973FS2/KmYSAr4jA6tOTUvMT5BPlWpul>

cat ~/.ssh/id_rsa.pub >> ~/.ssh/authorized_keys




 ${SPARK_HOME}/bin/spark-submit \
   --verbose \
   --class org.apache.spark.examples.JavaPageRank2 \
--deploy-mode cluster \
   /opt/spark/examples/target/scala-2.12/jars/spark-examples_2.12-3.4.0.jar \
   1000 10


message from yarn:
 client token: N/A
	 diagnostics: AM container is launched, waiting for AM container to Register with RM
	 ApplicationMaster host: N/A
	 ApplicationMaster RPC port: -1
	 queue: default
	 start time: 1700702961969
	 final status: UNDEFINED
	 tracking URL: http://Rezghool:8088/proxy/application_1700702951711_0001/

	 user: rezghool [] [ThreadID: 1] [ThreadName: main] [Caller: org.apache.spark.deploy.yarn.Clientaller] [Class: org.apache.spark.internal.Logging] [Method: logInfo] [File: Logging.scala] [Line: 60]
20:29:24.079 [main] INFO org.apache.spark.deploy.yarn.Client - Application report for application_1700702951711_0001 (state: ACCEPTED) [] [ThreadID: 1] [ThreadName: main] [Caller: org.apache.spark.deploy.yarn.Clientaller] [Class: or


spark-submit \
--class org.apache.spark.examples.SparkPi \
--master yarn \
--deploy-mode cluster \
--driver-memory 4g \
--executor-memory 2g \
--executor-cores 1 \
/opt/spark/examples/target/scala-2.12/jars/spark-examples_2.12-3.4.0.jar 1



spark-submit --deploy-mode client --class org.apache.spark.examples.SparkPi /opt/spark/examples/target/scala-2.12/jars/spark-examples_2.12-3.4.0.jar 10

https://sparkbyexamples.com/spark/spark-setup-on-hadoop-yarn/

https://sparkbyexamples.com/spark/spark-web-ui-understanding/


${SPARK_HOME}/bin/spark-submit \
--class org.apache.spark.examples.JavaPageRank \
--master yarn \
--deploy-mode cluster \
/opt/spark/examples/target/scala-2.12/jars/spark-examples_2.12-3.4.0.jar \
/home/rezghool/research/spark_example/input2.txt 3

     ${SPARK_HOME}/bin/spark-submit \
  --class org.apache.spark.examples.SparkPi \
    --master yarn \
    --deploy-mode client \
    --driver-memory 4g \
    --executor-memory 2g \
    --executor-cores 1 \
    --queue thequeue \
  /opt/spark/examples/target/scala-2.12/jars/spark-examples_2.12-3.4.0.jar 10

curl -sS https://dl.yarnpkg.com/debian/pubkey.gpg | sudo apt-key add - and echo "deb https://dl.yarnpkg.com/debian/ stable main" | sudo tee /etc/apt/sources.list.d/yarn.list


   ```

   ```bash
     ${SPARK_HOME}/bin/spark-submit \
   --verbose \
   --class org.apache.spark.examples.JavaPageRank2 \
   --master local[2] \
   /opt/spark/examples/target/scala-2.12/jars/spark-examples_2.12-3.4.0.jar \
   1000 10
   ```


## Which cluster type should I choose for Spark?
Standalone - meaning Spark will manage its own cluster
YARN - using Hadoop's YARN resource manager
Mesos - Apache's dedicated resource manager project
I think I should try Standalone first. In the future, I need to build a large cluster (hundreds of instances).


Start with a standalone cluster if this is a new deployment.
Standalone mode is the easiest to set up and will provide almost all the same features as the other cluster managers if you are only running Spark.

If you would like to run Spark alongside other applications, or to use richer resource scheduling capabilities (e.g. queues), both YARN and Mesos provide these features.
Of these, YARN will likely be preinstalled in many Hadoop distributions.

One advantage of Mesos over both YARN and standalone mode is its fine-grained sharing option, which lets interactive applications such as the Spark shell scale down their CPU allocation between commands.
This makes it attractive in environments where multiple users are running interactive shells.

In all cases, it is best to run Spark on the same nodes as HDFS for fast access to storage.
You can install Mesos or the standalone cluster manager on the same nodes manually, or most Hadoop distributions already install YARN and HDFS together.
  

## Example more complecated
To make the `JavaPageRank` example more complex and potentially introduce an issue that can be observed in the Spark UI, we can modify the code to process a larger dataset or perform more computationally intensive operations. One common way to induce issues in Spark applications is to increase the amount of data being shuffled or to perform operations that are memory-intensive.

Here's a modified version of the `JavaPageRank` example with changes that are likely to make it more complex and resource-intensive:

### Modifications

1. **Increase the Number of Iterations**: More iterations of the PageRank algorithm will increase the computational workload.
   
2. **Artificially Inflate the Data**: We'll create additional links artificially to increase the size of the dataset being processed.

3. **Reduce the Level of Parallelism**: By repartitioning the data to a smaller number of partitions, we can increase the amount of data processed by each task, which might lead to resource constraints like out-of-memory errors.

### Modified JavaPageRank Code

```java
// ... [Previous imports and class declarations]

public final class JavaPageRank {
    private static final Pattern SPACES = Pattern.compile("\\s+");
    
    // ... [Previous methods]

    public static void main(String[] args) throws Exception {
        // ... [Existing argument checks and SparkSession creation]

        spark.sparkContext().addSparkListener(new MyCustomSparkListener());

        // ... [Existing code to load and process input file]

        // Artificially inflate the data and reduce the level of parallelism
        links = links.flatMapToPair(s -> {
            List<Tuple2<String, Iterable<String>>> newLinks = new ArrayList<>();
            newLinks.add(s);
            // Duplicate each link 10 times to increase dataset size
            for (int i = 0; i < 10; i++) {
                newLinks.add(new Tuple2<>(s._1 + "_copy" + i, s._2));
            }
            return newLinks.iterator();
        }).repartition(10); // Reduce the number of partitions

        // Initialize ranks
        JavaPairRDD<String, Double> ranks = links.mapValues(rs -> 1.0);

        // Increase the number of iterations to 20
        for (int current = 0; current < 20; current++) {
            // ... [Existing PageRank calculation logic]
        }

        // ... [Existing code to collect and print output]

        spark.stop();
    }
}
```

### Running the Modified Application

1. **Compile and Package**: After modifying the code, recompile and package your Spark application.

2. **Run with Limited Resources**: When running the application with `spark-submit`, you can specify limited resources to exacerbate potential issues. For example, use a small amount of memory for the executor:


3. **Monitor in Spark UI**: Once running, open the Spark UI (usually at `http://localhost:4040`). Look for signs of resource bottlenecks, such as task failures, executor loss, or excessive garbage collection time.

### Observation and Analysis

- In the Spark UI, observe the stages and tasks for signs of issues. 
- Check the event timeline and executor tabs for insights into resource usage and potential causes of any observed problems.

By making these changes, the `JavaPageRank` application will be more likely to encounter issues such as running out of memory, especially if run with constrained resources. Monitoring the application in the Spark UI will provide valuable insights into how Spark behaves under stress and how resource-related issues manifest.



https://community.cloudera.com/t5/Community-Articles/Configuring-spark-task-maxFailures-amp-spark-blacklist-task/ta-p/335235


Spark uses the blacklist mechanism to enhance the scheduler’s ability to track failures. When a task fails on an executor, the blacklist module tracks the executor and host which has failed to execute the task. Beyond a threshold, the scheduler won't be able to schedule any more tasks on that node. If spark.blacklist.enabled is set to true, we need to always set the value of spark.blacklist.task.maxTaskAttemptsPerNode to greater than spark.task.maxFailures, else the Spark job will fail with the following error message:

ERROR util.Utils: Uncaught exception in thread main
java.lang.IllegalArgumentException: spark.blacklist.task.maxTaskAttemptsPerNode ( = 2) was >= spark.task.maxFailures ( = 2 ). Though blacklisting is enabled, with this configuration, Spark will not be robust to one bad node. Decrease spark.blacklist.task.maxTaskAttemptsPerNode, increase spark.task.maxFailures, or disable blacklisting with spark.blacklist.enabled.




spark-submit --class org.apache.spark.examples.SparkPi \
--master yarn --deploy-mode client --conf spark.blacklist.enabled=true \
--conf spark.task.maxFailures=3 \
--conf spark.blacklist.task.maxTaskAttemptsPerNode=2 \
   /opt/spark/examples/target/scala-2.12/jars/spark-examples_2.12-3.4.0.jar 10



In example above, if set mater to some master of standalone (or yarn) cluster, make jar-file, and run it via spark-submit, behavior will be as expected: some tasks will be failed, but re-submited. If the application has some singleton (object in Scala), it will be keep own state across failed tasks.


Good for underatanding exceture

https://stackoverflow.com/questions/32621990/what-are-workers-executors-cores-in-spark-standalone-cluster?rq=2


![image](https://github.com/Rezix93/MyStuff/assets/80580733/53092463-8d7e-49b9-9bc0-97a8601d8bdd)

Spark uses a master/slave architecture. As you can see in the figure, it has one central coordinator (Driver) that communicates with many distributed workers (executors). The driver and each of the executors run in their own Java processes.

DRIVER

The driver is the process where the main method runs. First it converts the user program into tasks and after that it schedules the tasks on the executors.

EXECUTORS

Executors are worker nodes' processes in charge of running individual tasks in a given Spark job. They are launched at the beginning of a Spark application and typically run for the entire lifetime of an application. Once they have run the task they send the results to the driver. They also provide in-memory storage for RDDs that are cached by user programs through Block Manager.

APPLICATION EXECUTION FLOW

With this in mind, when you submit an application to the cluster with spark-submit this is what happens internally:

A standalone application starts and instantiates a SparkContext instance (and it is only then when you can call the application a driver).
The driver program ask for resources to the cluster manager to launch executors.
The cluster manager launches executors.
The driver process runs through the user application. Depending on the actions and transformations over RDDs task are sent to executors.
Executors run the tasks and save the results.
If any worker crashes, its tasks will be sent to different executors to be processed again. In the book "Learning Spark: Lightning-Fast Big Data Analysis" they talk about Spark and Fault Tolerance:
Spark automatically deals with failed or slow machines by re-executing failed or slow tasks. For example, if the node running a partition of a map() operation crashes, Spark will rerun it on another node; and even if the node does not crash but is simply much slower than other nodes, Spark can preemptively launch a “speculative” copy of the task on another node, and take its result if that finishes.

With SparkContext.stop() from the driver or if the main method exits/crashes all the executors will be terminated and the cluster resources will be released by the cluster manager.
YOUR QUESTIONS

When executors are started they register themselves with the driver and from so on they communicate directly. The workers are in charge of communicating the cluster manager the availability of their resources.

In a YARN cluster you can do that with --num-executors. In a standalone cluster you will get one executor per worker unless you play with spark.executor.cores and a worker has enough cores to hold more than one executor. (As @JacekLaskowski pointed out, --num-executors is no longer in use in YARN https://github.com/apache/spark/commit/16b6d18613e150c7038c613992d80a7828413e66)

You can assign the number of cores per executor with --executor-cores

--total-executor-cores is the max number of executor cores per application

As Sean Owen said in this thread: "there's not a good reason to run more than one worker per machine". You would have many JVM sitting in one machine for instance.

UPDATE

I haven't been able to test this scenarios, but according to documentation:

EXAMPLE 1: Spark will greedily acquire as many cores and executors as are offered by the scheduler. So in the end you will get 5 executors with 8 cores each.

EXAMPLE 2 to 5: Spark won't be able to allocate as many cores as requested in a single worker, hence no executors will be launch.


![image](https://github.com/Rezix93/MyStuff/assets/80580733/977547c7-c185-4321-9c8b-84519e02884c)


Why should we consider using Hadoop and Spark together?
Most people think of Spark as a replacement for Hadoop, but instead of replacing Hadoop, we can consider Spark as a binding technology for Hadoop. However, Spark can run separately from Hadoop, where it can run on a standalone cluster. Meanwhile, Spark used on top of Hadoop can leverage its storage and cluster management.

Though Spark does not provide its own storage system, it can take advantage of Hadoop for that. Through this, we can make a powerful production environment using Hadoop capabilities. Spark can also use YARN Resource Manager for easy resource management. Spark can easily handle task scheduling across a cluster.

Apache Spark can use the disaster recovery capabilities of Hadoop as well. We can leverage Hadoop with Spark to receive better cluster administration and data management. Spark together with Hadoop provides better data security.

Spark Machine Learning provides capabilities that are not properly utilized in Hadoop MapReduce. Using a fast computation engine like Spark, these Machine Learning algorithms can now execute faster since they can be executed in memory. In MapReduce programs, on the other hand, the data gets moved in and out of the disks between different stages of the processing pipeline.

Next, in this Spark tutorial, we will check out some market leaders who have implemented Spark and Hadoop together.




