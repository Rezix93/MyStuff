   ```bash
${SPARK_HOME}/bin/spark-submit \
   --verbose \
   --class org.apache.spark.examples.ml.JavaKMeansExample \
   --deploy-mode client \
   /opt/spark/examples/target/scala-2.12/jars/spark-examples_2.12-3.4.0.jar 1


${SPARK_HOME}/bin/spark-submit \
   --verbose \
   --class org.apache.spark.examples.ml.JavaKMeansExample \
   --master local[2] \
   /opt/spark/examples/target/scala-2.12/jars/spark-examples_2.12-3.4.0.jar 8

     ```

1: 
Exception in thread "main" java.lang.OutOfMemoryError: Java heap space
	at org.apache.spark.examples.ml.JavaKMeansExample.main(JavaKMeansExample.java:41)
	at java.base/jdk.internal.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at java.base/jdk.internal.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:62)
	at java.base/jdk.internal.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
	at java.base/java.lang.reflect.Method.invoke(Method.java:566)
	at org.apache.spark.deploy.JavaMainApplication.start(SparkApplication.scala:52)
	at org.apache.spark.deploy.SparkSubmit.org$apache$spark$deploy$SparkSubmit$$runMain(SparkSubmit.scala:1020)
	at org.apache.spark.deploy.SparkSubmit.doRunMain$1(SparkSubmit.scala:192)
	at org.apache.spark.deploy.SparkSubmit.submit(SparkSubmit.scala:215)
	at org.apache.spark.deploy.SparkSubmit.doSubmit(SparkSubmit.scala:91)
	at org.apache.spark.deploy.SparkSubmit$$anon$2.doSubmit(SparkSubmit.scala:1111)
	at org.apache.spark.deploy.SparkSubmit$.main(SparkSubmit.scala:1120)
	at org.apache.spark.deploy.SparkSubmit.main(SparkSubmit.scala)


----------------
2: No error
---------
3: java.lang.ArithmeticException: / by zero
-----
5: 
02:09:33.740 [Executor task launch worker for task 0.0 in stage 29.0 (TID 27)] ERROR org.apache.spark.executor.Executor - Exception in task 0.0 in stage 29.0 (TID 27) [] [ThreadID: 64] [ThreadName: Executor task launch worker for task 0.0 in stage 29.0 (TID 27)] [Caller: org.apache.spark.executor.Executoraller] [Class: org.apache.spark.internal.Logging] [Method: logError] [File: Logging.scala] [Line: 97]
org.apache.spark.SparkException: Intentional failure in stage
	at org.apache.spark.examples.ml.JavaKMeansExample.lambda$main$dc6d3fb3$1(JavaKMeansExample.java:92) ~[spark-examples_2.12-3.4.0.jar:3.4.0]
	at org.apache.spark.sql.Dataset.$anonfun$foreachPartition$2(Dataset.scala:3370) ~[spark-sql_2.12-3.4.0.jar:3.4.0]
	at org.apache.spark.sql.Dataset.$anonfun$foreachPartition$2$adapted(Dataset.scala:3370) ~[spark-sql_2.12-3.4.0.jar:3.4.0]
	at org.apache.spark.rdd.RDD.$anonfun$foreachPartition$2(RDD.scala:1027) ~[spark-core_2.12-3.4.0.jar:3.4.0]
	at org.apache.spark.rdd.RDD.$anonfun$foreachPartition$2$adapted(RDD.scala:1027) ~[spark-core_2.12-3.4.0.jar:3.4.0]
	at org.apache.spark.SparkContext.$anonfun$runJob$5(SparkContext.scala:2343) ~[spark-core_2.12-3.4.0.jar:3.4.0]
	at org.apache.spark.scheduler.ResultTask.runTask(ResultTask.scala:92) ~[spark-core_2.12-3.4.0.jar:3.4.0]
	at org.apache.spark.TaskContext.runTaskWithListeners(TaskContext.scala:161) ~[spark-core_2.12-3.4.0.jar:3.4.0]
	at org.apache.spark.scheduler.Task.run(Task.scala:139) ~[spark-core_2.12-3.4.0.jar:3.4.0]
	at org.apache.spark.executor.Executor$TaskRunner.$anonfun$run$3(Executor.scala:554) ~[spark-core_2.12-3.4.0.jar:3.4.0]
	at org.apache.spark.util.Utils$.tryWithSafeFinally(Utils.scala:1546) ~[spark-core_2.12-3.4.0.jar:3.4.0]
	at org.apache.spark.executor.Executor$TaskRunner.run(Executor.scala:557) ~[spark-core_2.12-3.4.0.jar:3.4.0]
	at java.util.concurrent.ThreadPoolExecutor.runWorker(ThreadPoolExecutor.java:1128) ~[?:?]
	at java.util.concurrent.ThreadPoolExecutor$Worker.run(ThreadPoolExecutor.java:628) ~[?:?]
	at java.lang.Thread.run(Thread.java:829) ~[?:?]
02:09:33.767 [task-result-getter-3] WARN org.apache.spark.scheduler.TaskSetManager - Lost task 0.0 in stage 29.0 (TID 27) (Rezghool.ht.home executor driver): org.apache.spark.SparkException: Intentional failure in stage
	at org.apache.spark.examples.ml.JavaKMeansExample.lambda$main$dc6d3fb3$1(JavaKMeansExample.java:92)
	at org.apache.spark.sql.Dataset.$anonfun$foreachPartition$2(Dataset.scala:3370)
	at org.apache.spark.sql.Dataset.$anonfun$foreachPartition$2$adapted(Dataset.scala:3370)
	at org.apache.spark.rdd.RDD.$anonfun$foreachPartition$2(RDD.scala:1027)
	at org.apache.spark.rdd.RDD.$anonfun$foreachPartition$2$adapted(RDD.scala:1027)
	at org.apache.spark.SparkContext.$anonfun$runJob$5(SparkContext.scala:2343)
	at org.apache.spark.scheduler.ResultTask.runTask(ResultTask.scala:92)
	at org.apache.spark.TaskContext.runTaskWithListeners(TaskContext.scala:161)
	at org.apache.spark.scheduler.Task.run(Task.scala:139)
	at org.apache.spark.executor.Executor$TaskRunner.$anonfun$run$3(Executor.scala:554)
	at org.apache.spark.util.Utils$.tryWithSafeFinally(Utils.scala:1546)
	at org.apache.spark.executor.Executor$TaskRunner.run(Executor.scala:557)
	at java.base/java.util.concurrent.ThreadPoolExecutor.runWorker(ThreadPoolExecutor.java:1128)
	at java.base/java.util.concurrent.ThreadPoolExecutor$Worker.run(ThreadPoolExecutor.java:628)
	at java.base/java.lang.Thread.run(Thread.java:829)
 [] [ThreadID: 103] [ThreadName: task-result-getter-3] [Caller: org.apache.spark.scheduler.TaskSetManageraller] [Class: org.apache.spark.internal.Logging] [Method: logWarning] [File: Logging.scala] [Line: 72]
02:09:33.769 [task-result-getter-3] ERROR org.apache.spark.scheduler.TaskSetManager - Task 0 in stage 29.0 failed 1 times; aborting job [] [ThreadID: 103] [ThreadName: task-result-getter-3] [Caller: org.apache.spark.scheduler.TaskSetManageraller] [Class: org.apache.spark.internal.Logging] [Method: logError] [File: Logging.scala] [Line: 76]
02:09:33.770 [task-result-getter-3] INFO org.apache.spark.scheduler.TaskSchedulerImpl - Removed TaskSet 29.0, whose tasks have all completed, from pool  [] [ThreadID: 103] [ThreadName: task-result-getter-3] [Caller: org.apache.spark.scheduler.TaskSchedulerImplaller] [Class: org.apache.spark.internal.Logging] [Method: logInfo] [File: Logging.scala] [Line: 60]
02:09:33.774 [dag-scheduler-event-loop] INFO org.apache.spark.scheduler.TaskSchedulerImpl - Cancelling stage 29 [] [ThreadID: 49] [ThreadName: dag-scheduler-event-loop] [Caller: org.apache.spark.scheduler.TaskSchedulerImplaller] [Class: org.apache.spark.internal.Logging] [Method: logInfo] [File: Logging.scala] [Line: 60]
02:09:33.775 [dag-scheduler-event-loop] INFO org.apache.spark.scheduler.TaskSchedulerImpl - Killing all running tasks in stage 29: Stage cancelled [] [ThreadID: 49] [ThreadName: dag-scheduler-event-loop] [Caller: org.apache.spark.scheduler.TaskSchedulerImplaller] [Class: org.apache.spark.internal.Logging] [Method: logInfo] [File: Logging.scala] [Line: 60]
02:09:33.776 [dag-scheduler-event-loop] INFO org.apache.spark.scheduler.DAGScheduler - ResultStage 29 (foreachPartition at JavaKMeansExample.java:90) failed in 0.074 s due to Job aborted due to stage failure: Task 0 in stage 29.0 failed 1 times, most recent failure: Lost task 0.0 in stage 29.0 (TID 27) (Rezghool.ht.home executor driver): org.apache.spark.SparkException: Intentional failure in stage
	at org.apache.spark.examples.ml.JavaKMeansExample.lambda$main$dc6d3fb3$1(JavaKMeansExample.java:92)
	at org.apache.spark.sql.Dataset.$anonfun$foreachPartition$2(Dataset.scala:3370)
	at org.apache.spark.sql.Dataset.$anonfun$foreachPartition$2$adapted(Dataset.scala:3370)
	at org.apache.spark.rdd.RDD.$anonfun$foreachPartition$2(RDD.scala:1027)
	at org.apache.spark.rdd.RDD.$anonfun$foreachPartition$2$adapted(RDD.scala:1027)
	at org.apache.spark.SparkContext.$anonfun$runJob$5(SparkContext.scala:2343)
	at org.apache.spark.scheduler.ResultTask.runTask(ResultTask.scala:92)
	at org.apache.spark.TaskContext.runTaskWithListeners(TaskContext.scala:161)
	at org.apache.spark.scheduler.Task.run(Task.scala:139)
	at org.apache.spark.executor.Executor$TaskRunner.$anonfun$run$3(Executor.scala:554)
	at org.apache.spark.util.Utils$.tryWithSafeFinally(Utils.scala:1546)
	at org.apache.spark.executor.Executor$TaskRunner.run(Executor.scala:557)
	at java.base/java.util.concurrent.ThreadPoolExecutor.runWorker(ThreadPoolExecutor.java:1128)
	at java.base/java.util.concurrent.ThreadPoolExecutor$Worker.run(ThreadPoolExecutor.java:628)
	at java.base/java.lang.Thread.run(Thread.java:829)

Driver stacktrace: [] [ThreadID: 49] [ThreadName: dag-scheduler-event-loop] [Caller: org.apache.spark.scheduler.DAGScheduleraller] [Class: org.apache.spark.internal.Logging] [Method: logInfo] [File: Logging.scala] [Line: 60]
02:09:33.779 [main] INFO org.apache.spark.scheduler.DAGScheduler - Job 19 failed: foreachPartition at JavaKMeansExample.java:90, took 0.079816 s [] [ThreadID: 1] [ThreadName: main] [Caller: org.apache.spark.scheduler.DAGScheduleraller] [Class: org.apache.spark.internal.Logging] [Method: logInfo] [File: Logging.scala] [Line: 60]
Exception in thread "main" org.apache.spark.SparkException: Job aborted due to stage failure: Task 0 in stage 29.0 failed 1 times, most recent failure: Lost task 0.0 in stage 29.0 (TID 27) (Rezghool.ht.home executor driver): org.apache.spark.SparkException: Intentional failure in stage
	at org.apache.spark.examples.ml.JavaKMeansExample.lambda$main$dc6d3fb3$1(JavaKMeansExample.java:92)
	at org.apache.spark.sql.Dataset.$anonfun$foreachPartition$2(Dataset.scala:3370)
	at org.apache.spark.sql.Dataset.$anonfun$foreachPartition$2$adapted(Dataset.scala:3370)
	at org.apache.spark.rdd.RDD.$anonfun$foreachPartition$2(RDD.scala:1027)
	at org.apache.spark.rdd.RDD.$anonfun$foreachPartition$2$adapted(RDD.scala:1027)
	at org.apache.spark.SparkContext.$anonfun$runJob$5(SparkContext.scala:2343)
	at org.apache.spark.scheduler.ResultTask.runTask(ResultTask.scala:92)
	at org.apache.spark.TaskContext.runTaskWithListeners(TaskContext.scala:161)
	at org.apache.spark.scheduler.Task.run(Task.scala:139)
	at org.apache.spark.executor.Executor$TaskRunner.$anonfun$run$3(Executor.scala:554)
	at org.apache.spark.util.Utils$.tryWithSafeFinally(Utils.scala:1546)
	at org.apache.spark.executor.Executor$TaskRunner.run(Executor.scala:557)
	at java.base/java.util.concurrent.ThreadPoolExecutor.runWorker(ThreadPoolExecutor.java:1128)
	at java.base/java.util.concurrent.ThreadPoolExecutor$Worker.run(ThreadPoolExecutor.java:628)
	at java.base/java.lang.Thread.run(Thread.java:829)

Driver stacktrace:
	at org.apache.spark.scheduler.DAGScheduler.failJobAndIndependentStages(DAGScheduler.scala:2785)
	at org.apache.spark.scheduler.DAGScheduler.$anonfun$abortStage$2(DAGScheduler.scala:2721)
	at org.apache.spark.scheduler.DAGScheduler.$anonfun$abortStage$2$adapted(DAGScheduler.scala:2720)
	at scala.collection.mutable.ResizableArray.foreach(ResizableArray.scala:62)
	at scala.collection.mutable.ResizableArray.foreach$(ResizableArray.scala:55)
	at scala.collection.mutable.ArrayBuffer.foreach(ArrayBuffer.scala:49)
	at org.apache.spark.scheduler.DAGScheduler.abortStage(DAGScheduler.scala:2720)
	at org.apache.spark.scheduler.DAGScheduler.$anonfun$handleTaskSetFailed$1(DAGScheduler.scala:1206)
	at org.apache.spark.scheduler.DAGScheduler.$anonfun$handleTaskSetFailed$1$adapted(DAGScheduler.scala:1206)
	at scala.Option.foreach(Option.scala:407)
	at org.apache.spark.scheduler.DAGScheduler.handleTaskSetFailed(DAGScheduler.scala:1206)
	at org.apache.spark.scheduler.DAGSchedulerEventProcessLoop.doOnReceive(DAGScheduler.scala:2984)
	at org.apache.spark.scheduler.DAGSchedulerEventProcessLoop.onReceive(DAGScheduler.scala:2923)
	at org.apache.spark.scheduler.DAGSchedulerEventProcessLoop.onReceive(DAGScheduler.scala:2912)
	at org.apache.spark.util.EventLoop$$anon$1.run(EventLoop.scala:49)
	at org.apache.spark.scheduler.DAGScheduler.runJob(DAGScheduler.scala:971)
	at org.apache.spark.SparkContext.runJob(SparkContext.scala:2288)
	at org.apache.spark.SparkContext.runJob(SparkContext.scala:2316)
	at org.apache.spark.SparkContext.runJob(SparkContext.scala:2343)
	at org.apache.spark.SparkContext.runJob(SparkContext.scala:2386)
	at org.apache.spark.rdd.RDD.$anonfun$foreachPartition$1(RDD.scala:1027)
	at org.apache.spark.rdd.RDDOperationScope$.withScope(RDDOperationScope.scala:151)
	at org.apache.spark.rdd.RDDOperationScope$.withScope(RDDOperationScope.scala:112)
	at org.apache.spark.rdd.RDD.withScope(RDD.scala:417)
	at org.apache.spark.rdd.RDD.foreachPartition(RDD.scala:1025)
	at org.apache.spark.sql.Dataset.$anonfun$foreachPartition$1(Dataset.scala:3359)
	at scala.runtime.java8.JFunction0$mcV$sp.apply(JFunction0$mcV$sp.java:23)
	at org.apache.spark.sql.Dataset.$anonfun$withNewRDDExecutionId$1(Dataset.scala:4154)
	at org.apache.spark.sql.execution.SQLExecution$.$anonfun$withNewExecutionId$6(SQLExecution.scala:118)
	at org.apache.spark.sql.execution.SQLExecution$.withSQLConfPropagated(SQLExecution.scala:195)
	at org.apache.spark.sql.execution.SQLExecution$.$anonfun$withNewExecutionId$1(SQLExecution.scala:103)
	at org.apache.spark.sql.SparkSession.withActive(SparkSession.scala:849)
	at org.apache.spark.sql.execution.SQLExecution$.withNewExecutionId(SQLExecution.scala:65)
	at org.apache.spark.sql.Dataset.withNewRDDExecutionId(Dataset.scala:4152)
	at org.apache.spark.sql.Dataset.foreachPartition(Dataset.scala:3359)
	at org.apache.spark.sql.Dataset.foreachPartition(Dataset.scala:3370)
	at org.apache.spark.examples.ml.JavaKMeansExample.main(JavaKMeansExample.java:90)
	at java.base/jdk.internal.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at java.base/jdk.internal.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:62)
	at java.base/jdk.internal.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
	at java.base/java.lang.reflect.Method.invoke(Method.java:566)
	at org.apache.spark.deploy.JavaMainApplication.start(SparkApplication.scala:52)
	at org.apache.spark.deploy.SparkSubmit.org$apache$spark$deploy$SparkSubmit$$runMain(SparkSubmit.scala:1020)
	at org.apache.spark.deploy.SparkSubmit.doRunMain$1(SparkSubmit.scala:192)
	at org.apache.spark.deploy.SparkSubmit.submit(SparkSubmit.scala:215)
	at org.apache.spark.deploy.SparkSubmit.doSubmit(SparkSubmit.scala:91)
	at org.apache.spark.deploy.SparkSubmit$$anon$2.doSubmit(SparkSubmit.scala:1111)
	at org.apache.spark.deploy.SparkSubmit$.main(SparkSubmit.scala:1120)
	at org.apache.spark.deploy.SparkSubmit.main(SparkSubmit.scala)
Caused by: org.apache.spark.SparkException: Intentional failure in stage
	at org.apache.spark.examples.ml.JavaKMeansExample.lambda$main$dc6d3fb3$1(JavaKMeansExample.java:92)
	at org.apache.spark.sql.Dataset.$anonfun$foreachPartition$2(Dataset.scala:3370)
	at org.apache.spark.sql.Dataset.$anonfun$foreachPartition$2$adapted(Dataset.scala:3370)
	at org.apache.spark.rdd.RDD.$anonfun$foreachPartition$2(RDD.scala:1027)
	at org.apache.spark.rdd.RDD.$anonfun$foreachPartition$2$adapted(RDD.scala:1027)
	at org.apache.spark.SparkContext.$anonfun$runJob$5(SparkContext.scala:2343)
	at org.apache.spark.scheduler.ResultTask.runTask(ResultTask.scala:92)
	at org.apache.spark.TaskContext.runTaskWithListeners(TaskContext.scala:161)
	at org.apache.spark.scheduler.Task.run(Task.scala:139)
	at org.apache.spark.executor.Executor$TaskRunner.$anonfun$run$3(Executor.scala:554)
	at org.apache.spark.util.Utils$.tryWithSafeFinally(Utils.scala:1546)
	at org.apache.spark.executor.Executor$TaskRunner.run(Executor.scala:557)
	at java.base/java.util.concurrent.ThreadPoolExecutor.runWorker(ThreadPoolExecutor.java:1128)
	at java.base/java.util.concurrent.ThreadPoolExecutor$Worker.run(ThreadPoolExecutor.java:628)
	at java.base/java.lang.Thread.run(Thread.java:829)
02:09:33.907 [shutdown-hook-0] INFO org.apache.spark.SparkContext - Invoking stop() from shutdown hook [] [ThreadID: 277] [ThreadName: shutdown-hook-0] [Caller: org.apache.spark.SparkContextaller] [Class: org.apache.spark.internal.Logging] [Method: logInfo] [File: Logging.scala] [Line: 60]




-------------------
6: Exception in thread "main" java.lang.IllegalArgumentException: features does not exist. Available: 
	at org.apache.spark.sql.types.StructType.$anonfun$apply$1(StructType.scala:285)
	at scala.collection.immutable.Map$EmptyMap$.getOrElse(Map.scala:110)
	at org.apache.spark.sql.types.StructType.apply(StructType.scala:284)
	at org.apache.spark.ml.util.SchemaUtils$.checkColumnTypes(SchemaUtils.scala:59)
	at org.apache.spark.ml.util.SchemaUtils$.validateVectorCompatibleColumn(SchemaUtils.scala:205)
	at org.apache.spark.ml.clustering.KMeansParams.validateAndTransformSchema(KMeans.scala:121)
	at org.apache.spark.ml.clustering.KMeansParams.validateAndTransformSchema$(KMeans.scala:120)
	at org.apache.spark.ml.clustering.KMeansModel.validateAndTransformSchema(KMeans.scala:132)
	at org.apache.spark.ml.clustering.KMeansModel.transformSchema(KMeans.scala:168)
	at org.apache.spark.ml.PipelineStage.transformSchema(Pipeline.scala:71)
	at org.apache.spark.ml.clustering.KMeansModel.transform(KMeans.scala:157)
	at org.apache.spark.examples.ml.JavaKMeansExample.main(JavaKMeansExample.java:133)
	at java.base/jdk.internal.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at java.base/jdk.internal.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:62)
	at java.base/jdk.internal.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
	at java.base/java.lang.reflect.Method.invoke(Method.java:566)
	at org.apache.spark.deploy.JavaMainApplication.start(SparkApplication.scala:52)
	at org.apache.spark.deploy.SparkSubmit.org$apache$spark$deploy$SparkSubmit$$runMain(SparkSubmit.scala:1020)
	at org.apache.spark.deploy.SparkSubmit.doRunMain$1(SparkSubmit.scala:192)
	at org.apache.spark.deploy.SparkSubmit.submit(SparkSubmit.scala:215)
	at org.apache.spark.deploy.SparkSubmit.doSubmit(SparkSubmit.scala:91)
	at org.apache.spark.deploy.SparkSubmit$$anon$2.doSubmit(SparkSubmit.scala:1111)
	at org.apache.spark.deploy.SparkSubmit$.main(SparkSubmit.scala:1120)
	at org.apache.spark.deploy.SparkSubmit.main(SparkSubmit.scala)
02:25:38.194 [shutdown-hook-0] INFO org.apache.spark.SparkContext - Invoking stop() from shutdown hook [] [ThreadID: 276] [ThreadName: shutdown-hook-0] [Caller: org.apache.spark.SparkContextaller] [Class: org.apache.spark.internal.Logging] [Method: logInfo] [File: Logging.scala] [Line: 60]

-----------------------------------------
change 6 and 7 : 

The error you're encountering (java.lang.IllegalArgumentException: features does not exist) is due to the transformation applied to the dataset after the KMeans model fitting. The map transformation in the code is altering the structure of the dataset, which is causing an issue when the transform method of the KMeans model is called later.

In Spark MLlib, when you fit a model (like KMeans), the model expects the input dataset for prediction (or transformation) to have the same schema as the dataset used for training. The map operation in your code is changing the schema of the dataset, leading to this error.

To fix this, you need to ensure that the schema of the dataset remains consistent after any transformation. Here's a revised version of the code that addresses this issue:

Dataset<Row> transformedDataset = dataset.map((MapFunction<Row, Row>) row -> {
        // Allocate a large amount of memory (this could lead to OutOfMemoryError)
        byte[] largeArray = new byte[1000 * 1000 * 1000]; // 1GB
        return row;
    }, Encoders.bean(Row.class));




    
-----------------------------
new 6,7 : no error 
------------------
8:

nternal.Logging] [Method: logInfo] [File: Logging.scala] [Line: 60]
05:16:40.315 [dag-scheduler-event-loop] INFO org.apache.spark.scheduler.DAGScheduler - ResultStage 35 (foreachPartition at JavaKMeansExample.java:138) failed in 0.073 s due to Job aborted due to stage failure: Task 0 in stage 35.0 failed 1 times, most recent failure: Lost task 0.0 in stage 35.0 (TID 64) (Rezghool.ht.home executor driver): java.lang.NegativeArraySizeException: -727379968
	at org.apache.spark.examples.ml.JavaKMeansExample.lambda$main$dc6d3fb3$2(JavaKMeansExample.java:140)
	at org.apache.spark.sql.Dataset.$anonfun$foreachPartition$2(Dataset.scala:3370)
	at org.apache.spark.sql.Dataset.$anonfun$foreachPartition$2$adapted(Dataset.scala:3370)
	at org.apache.spark.rdd.RDD.$anonfun$foreachPartition$2(RDD.scala:1027)
	at org.apache.spark.rdd.RDD.$anonfun$foreachPartition$2$adapted(RDD.scala:1027)
	at org.apache.spark.SparkContext.$anonfun$runJob$5(SparkContext.scala:2343)
	at org.apache.spark.scheduler.ResultTask.runTask(ResultTask.scala:92)
	at org.apache.spark.TaskContext.runTaskWithListeners(TaskContext.scala:161)
	at org.apache.spark.scheduler.Task.run(Task.scala:139)
	at org.apache.spark.executor.Executor$TaskRunner.$anonfun$run$3(Executor.scala:554)
	at org.apache.spark.util.Utils$.tryWithSafeFinally(Utils.scala:1546)
	at org.apache.spark.executor.Executor$TaskRunner.run(Executor.scala:557)
	at java.base/java.util.concurrent.ThreadPoolExecutor.runWorker(ThreadPoolExecutor.java:1128)
	at java.base/java.util.concurrent.ThreadPoolExecutor$Worker.run(ThreadPoolExecutor.java:628)
	at java.base/java.lang.Thread.run(Thread.java:829)

Driver stacktrace: [] [ThreadID: 49] [ThreadName: dag-scheduler-event-loop] [Caller: org.apache.spark.scheduler.DAGScheduleraller] [Class: org.apache.spark.internal.Logging] [Method: logInfo] [File: Logging.scala] [Line: 60]
05:16:40.317 [main] INFO org.apache.spark.scheduler.DAGScheduler - Job 22 failed: foreachPartition at JavaKMeansExample.java:138, took 0.078794 s [] [ThreadID: 1] [ThreadName: main] [Caller: org.apache.spark.scheduler.DAGScheduleraller] [Class: org.apache.spark.internal.Logging] [Method: logInfo] [File: Logging.scala] [Line: 60]
05:16:40.318 [task-result-getter-1] WARN org.apache.spark.scheduler.TaskSetManager - Lost task 1.0 in stage 35.0 (TID 65) (Rezghool.ht.home executor driver): TaskKilled (Stage cancelled) [] [ThreadID: 71] [ThreadName: task-result-getter-1] [Caller: org.apache.spark.scheduler.TaskSetManageraller] [Class: org.apache.spark.internal.Logging] [Method: logWarning] [File: Logging.scala] [Line: 72]
05:16:40.318 [task-result-getter-1] INFO org.apache.spark.scheduler.TaskSchedulerImpl - Removed TaskSet 35.0, whose tasks have all completed, from pool  [] [ThreadID: 71] [ThreadName: task-result-getter-1] [Caller: org.apache.spark.scheduler.TaskSchedulerImplaller] [Class: org.apache.spark.internal.Logging] [Method: logInfo] [File: Logging.scala] [Line: 60]
Exception in thread "main" org.apache.spark.SparkException: Job aborted due to stage failure: Task 0 in stage 35.0 failed 1 times, most recent failure: Lost task 0.0 in stage 35.0 (TID 64) (Rezghool.ht.home executor driver): java.lang.NegativeArraySizeException: -727379968
	at org.apache.spark.examples.ml.JavaKMeansExample.lambda$main$dc6d3fb3$2(JavaKMeansExample.java:140)
	at org.apache.spark.sql.Dataset.$anonfun$foreachPartition$2(Dataset.scala:3370)
	at org.apache.spark.sql.Dataset.$anonfun$foreachPartition$2$adapted(Dataset.scala:3370)
	at org.apache.spark.rdd.RDD.$anonfun$foreachPartition$2(RDD.scala:1027)
	at org.apache.spark.rdd.RDD.$anonfun$foreachPartition$2$adapted(RDD.scala:1027)
	at org.apache.spark.SparkContext.$anonfun$runJob$5(SparkContext.scala:2343)
	at org.apache.spark.scheduler.ResultTask.runTask(ResultTask.scala:92)
	at org.apache.spark.TaskContext.runTaskWithListeners(TaskContext.scala:161)
	at org.apache.spark.scheduler.Task.run(Task.scala:139)
	at org.apache.spark.executor.Executor$TaskRunner.$anonfun$run$3(Executor.scala:554)
	at org.apache.spark.util.Utils$.tryWithSafeFinally(Utils.scala:1546)
	at org.apache.spark.executor.Executor$TaskRunner.run(Executor.scala:557)
	at java.base/java.util.concurrent.ThreadPoolExecutor.runWorker(ThreadPoolExecutor.java:1128)
	at java.base/java.util.concurrent.ThreadPoolExecutor$Worker.run(ThreadPoolExecutor.java:628)
	at java.base/java.lang.Thread.run(Thread.java:829)

Driver stacktrace:
	at org.apache.spark.scheduler.DAGScheduler.failJobAndIndependentStages(DAGScheduler.scala:2785)
	at org.apache.spark.scheduler.DAGScheduler.$anonfun$abortStage$2(DAGScheduler.scala:2721)
	at org.apache.spark.scheduler.DAGScheduler.$anonfun$abortStage$2$adapted(DAGScheduler.scala:2720)
	at scala.collection.mutable.ResizableArray.foreach(ResizableArray.scala:62)
	at scala.collection.mutable.ResizableArray.foreach$(ResizableArray.scala:55)
	at scala.collection.mutable.ArrayBuffer.foreach(ArrayBuffer.scala:49)
	at org.apache.spark.scheduler.DAGScheduler.abortStage(DAGScheduler.scala:2720)
	at org.apache.spark.scheduler.DAGScheduler.$anonfun$handleTaskSetFailed$1(DAGScheduler.scala:1206)
	at org.apache.spark.scheduler.DAGScheduler.$anonfun$handleTaskSetFailed$1$adapted(DAGScheduler.scala:1206)
	at scala.Option.foreach(Option.scala:407)
	at org.apache.spark.scheduler.DAGScheduler.handleTaskSetFailed(DAGScheduler.scala:1206)
	at org.apache.spark.scheduler.DAGSchedulerEventProcessLoop.doOnReceive(DAGScheduler.scala:2984)
	at org.apache.spark.scheduler.DAGSchedulerEventProcessLoop.onReceive(DAGScheduler.scala:2923)
	at org.apache.spark.scheduler.DAGSchedulerEventProcessLoop.onReceive(DAGScheduler.scala:2912)
	at org.apache.spark.util.EventLoop$$anon$1.run(EventLoop.scala:49)
	at org.apache.spark.scheduler.DAGScheduler.runJob(DAGScheduler.scala:971)
	at org.apache.spark.SparkContext.runJob(SparkContext.scala:2288)
	at org.apache.spark.SparkContext.runJob(SparkContext.scala:2316)
	at org.apache.spark.SparkContext.runJob(SparkContext.scala:2343)
	at org.apache.spark.SparkContext.runJob(SparkContext.scala:2386)
	at org.apache.spark.rdd.RDD.$anonfun$foreachPartition$1(RDD.scala:1027)
	at org.apache.spark.rdd.RDDOperationScope$.withScope(RDDOperationScope.scala:151)
	at org.apache.spark.rdd.RDDOperationScope$.withScope(RDDOperationScope.scala:112)
	at org.apache.spark.rdd.RDD.withScope(RDD.scala:417)
	at org.apache.spark.rdd.RDD.foreachPartition(RDD.scala:1025)
	at org.apache.spark.sql.Dataset.$anonfun$foreachPartition$1(Dataset.scala:3359)
	at scala.runtime.java8.JFunction0$mcV$sp.apply(JFunction0$mcV$sp.java:23)
	at org.apache.spark.sql.Dataset.$anonfun$withNewRDDExecutionId$1(Dataset.scala:4154)
	at org.apache.spark.sql.execution.SQLExecution$.$anonfun$withNewExecutionId$6(SQLExecution.scala:118)
	at org.apache.spark.sql.execution.SQLExecution$.withSQLConfPropagated(SQLExecution.scala:195)
	at org.apache.spark.sql.execution.SQLExecution$.$anonfun$withNewExecutionId$1(SQLExecution.scala:103)
	at org.apache.spark.sql.SparkSession.withActive(SparkSession.scala:849)
	at org.apache.spark.sql.execution.SQLExecution$.withNewExecutionId(SQLExecution.scala:65)
	at org.apache.spark.sql.Dataset.withNewRDDExecutionId(Dataset.scala:4152)
	at org.apache.spark.sql.Dataset.foreachPartition(Dataset.scala:3359)
	at org.apache.spark.sql.Dataset.foreachPartition(Dataset.scala:3370)
	at org.apache.spark.examples.ml.JavaKMeansExample.main(JavaKMeansExample.java:138)
	at java.base/jdk.internal.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at java.base/jdk.internal.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:62)
	at java.base/jdk.internal.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
	at java.base/java.lang.reflect.Method.invoke(Method.java:566)
	at org.apache.spark.deploy.JavaMainApplication.start(SparkApplication.scala:52)
	at org.apache.spark.deploy.SparkSubmit.org$apache$spark$deploy$SparkSubmit$$runMain(SparkSubmit.scala:1020)
	at org.apache.spark.deploy.SparkSubmit.doRunMain$1(SparkSubmit.scala:192)
	at org.apache.spark.deploy.SparkSubmit.submit(SparkSubmit.scala:215)
	at org.apache.spark.deploy.SparkSubmit.doSubmit(SparkSubmit.scala:91)
	at org.apache.spark.deploy.SparkSubmit$$anon$2.doSubmit(SparkSubmit.scala:1111)
	at org.apache.spark.deploy.SparkSubmit$.main(SparkSubmit.scala:1120)
	at org.apache.spark.deploy.SparkSubmit.main(SparkSubmit.scala)
Caused by: java.lang.NegativeArraySizeException: -727379968
	at org.apache.spark.examples.ml.JavaKMeansExample.lambda$main$dc6d3fb3$2(JavaKMeansExample.java:140)
	at org.apache.spark.sql.Dataset.$anonfun$foreachPartition$2(Dataset.scala:3370)
	at org.apache.spark.sql.Dataset.$anonfun$foreachPartition$2$adapted(Dataset.scala:3370)
	at org.apache.spark.rdd.RDD.$anonfun$foreachPartition$2(RDD.scala:1027)
	at org.apache.spark.rdd.RDD.$anonfun$foreachPartition$2$adapted(RDD.scala:1027)
	at org.apache.spark.SparkContext.$anonfun$runJob$5(SparkContext.scala:2343)
	at org.apache.spark.scheduler.ResultTask.runTask(ResultTask.scala:92)
	at org.apache.spark.TaskContext.runTaskWithListeners(TaskContext.scala:161)
	at org.apache.spark.scheduler.Task.run(Task.scala:139)
	at org.apache.spark.executor.Executor$TaskRunner.$anonfun$run$3(Executor.scala:554)
	at org.apache.spark.util.Utils$.tryWithSafeFinally(Utils.scala:1546)
	at org.apache.spark.executor.Executor$TaskRunner.run(Executor.scala:557)
	at java.base/java.util.concurrent.ThreadPoolExecutor.runWorker(ThreadPoolExecutor.java:1128)
	at java.base/java.util.concurrent.ThreadPoolExecutor$Worker.run(ThreadPoolExecutor.java:628)
	at java.base/java.lang.Thread.run(Thread.java:829)
05:16:40.441 [shutdown-hook-0] INFO org.apache.spark.SparkContext - Invoking stop() from shutdown hook [] [ThreadID: 281] [ThreadName: shutdown-hook-0] [Caller: org.apache.spark.SparkContextaller] [Class: org.apache.spark.internal.Logging] [Method: logInfo] [File: Logging.scala] [Line: 60]
05:16:40.441 [shutdown-hook-0] INFO org.apache.spark.SparkContext - SparkContext is stopping with exitCode 0. [] [ThreadID: 281] [ThreadName: shutdown-hook-0] [Caller: org.apache.spark.SparkContextaller] [Class: org.apache.spark.internal.Logging] [Method: logInfo] [File: Logging.scala] [Line: 60]
05:16:40.448 [shutdown-hook-0] INFO org.sparkproject.jetty.server.AbstractConnector - Stopped Spark@4c5228e7{HTTP/1.1, (http/1.1)}{0.0.0.0:4040} [] [ThreadID: 281] [ThreadName: shutdown-hook-0] [Caller: org.sparkproject.jetty.server.AbstractConnectoraller] [Class: org.sparkproject.jetty.server.AbstractConnector] [Method: doStop] [File: AbstractConnector.java] [Line: 383]
--------------------
9: ok
-----------
10: ok
--------------------
foreachPartition Code Snippet:

This snippet uses foreachPartition to iterate over each partition of the dataset. The memory allocation (byte[] largeArray = new byte[10000 * 10000 * 10000];) is attempted within the foreachPartition function.
The foreachPartition action is executed on the executors. If the memory allocation fails (e.g., due to an OutOfMemoryError), it will cause the executor process to fail. This failure can lead to task failure and potentially the failure of the entire job, depending on Spark's fault tolerance mechanisms.
The size of the array you're trying to allocate (10000 * 10000 * 10000) is extremely large and likely to exceed the available heap space, leading to an OutOfMemoryError.
map Code Snippet:

This snippet uses map to transform each row of the dataset. The memory allocation is attempted within the map function.
The map transformation is lazily evaluated in Spark. This means that Spark will not perform the transformation until an action (like collect, count, save, etc.) is called on the resulting dataset.
If the memory allocation within the map function is too large and causes an OutOfMemoryError, it will similarly cause the executor to fail when the action is executed.
However, if no action is called on mappedPredictions, or if the dataset is small enough that the memory allocation does not exceed the available heap space for each transformation, you might not see an error immediately.

------------------------
10:
java.lang.NegativeArraySizeException: -727379968
	at org.apache.spark.examples.ml.JavaKMeansExample$1.call(JavaKMeansExample.java:179) ~[spark-examples_2.12-3.4.0.jar:3.4.0]
	at org.apache.spark.examples.ml.JavaKMeansExample$1.call(JavaKMeansExample.java:175) ~[spark-examples_2.12-3.4.0.jar:3.4.0]
	at org.apache.spark.sql.catalyst.expressions.GeneratedClass$GeneratedIteratorForCodegenStage1.mapelements_doConsume_0$(Unknown Source) ~[?:?]
	at org.apache.spark.sql.catalyst.expressions.GeneratedClass$GeneratedIteratorForCodegenStage1.deserializetoobject_doConsume_0$(Unknown Source) ~[?:?]
	at org.apache.spark.sql.catalyst.expressions.GeneratedClass$GeneratedIteratorForCodegenStage1.processNext(Unknown Source) ~[?:?]
	at org.apache.spark.sql.execution.BufferedRowIterator.hasNext(BufferedRowIterator.java:43) ~[spark-sql_2.12-3.4.0.jar:3.4.0]
	at org.apache.spark.sql.execution.WholeStageCodegenExec$$anon$1.hasNext(WholeStageCodegenExec.scala:760) ~[spark-sql_2.12-3.4.0.jar:3.4.0]
	at org.apache.spark.sql.execution.SparkPlan.$anonfun$getByteArrayRdd$1(SparkPlan.scala:388) ~[spark-sql_2.12-3.4.0.jar:3.4.0]
	at org.apache.spark.rdd.RDD.$anonfun$mapPartitionsInternal$2(RDD.scala:906) ~[spark-core_2.12-3.4.0.jar:3.4.0]
	at org.apache.spark.rdd.RDD.$anonfun$mapPartitionsInternal$2$adapted(RDD.scala:906) ~[spark-core_2.12-3.4.0.jar:3.4.0]
	at org.apache.spark.rdd.MapPartitionsRDD.compute(MapPartitionsRDD.scala:52) ~[spark-core_2.12-3.4.0.jar:3.4.0]
	at org.apache.spark.rdd.RDD.computeOrReadCheckpoint(RDD.scala:376) ~[spark-core_2.12-3.4.0.jar:3.4.0]
	at org.apache.spark.rdd.RDD.iterator(RDD.scala:340) ~[spark-core_2.12-3.4.0.jar:3.4.0]
	at org.apache.spark.scheduler.ResultTask.runTask(ResultTask.scala:92) ~[spark-core_2.12-3.4.0.jar:3.4.0]
	at org.apache.spark.TaskContext.runTaskWithListeners(TaskContext.scala:161) ~[spark-core_2.12-3.4.0.jar:3.4.0]
	at org.apache.spark.scheduler.Task.run(Task.scala:139) ~[spark-core_2.12-3.4.0.jar:3.4.0]
	at org.apache.spark.executor.Executor$TaskRunner.$anonfun$run$3(Executor.scala:554) ~[spark-core_2.12-3.4.0.jar:3.4.0]
	at org.apache.spark.util.Utils$.tryWithSafeFinally(Utils.scala:1546) ~[spark-core_2.12-3.4.0.jar:3.4.0]
	at org.apache.spark.executor.Executor$TaskRunner.run(Executor.scala:557) ~[spark-core_2.12-3.4.0.jar:3.4.0]
	at java.util.concurrent.ThreadPoolExecutor.runWorker(ThreadPoolExecutor.java:1128) ~[?:?]
	at java.util.concurrent.ThreadPoolExecutor$Worker.run(ThreadPoolExecutor.java:628) ~[?:?]
	at java.lang.Thread.run(Thread.java:829) ~[?:?]
16:49:24.793 [Executor task launch worker for task 1.0 in stage 35.0 (TID 65)] ERROR org.apache.spark.executor.Executor - Exception in task 1.0 in stage 35.0 (TID 65) [] [ThreadID: 64] [ThreadName: Executor task launch worker for task 1.0 in stage 35.0 (TID 65)] [Caller: org.apache.spark.executor.Executoraller] [Class: org.apache.spark.internal.Logging] [Method: logError] [File: Logging.scala] [Line: 97]
java.lang.NegativeArraySizeException: -727379968
	at org.apache.spark.examples.ml.JavaKMeansExample$1.call(JavaKMeansExample.java:179) ~[spark-examples_2.12-3.4.0.jar:3.4.0]
	at org.apache.spark.examples.ml.JavaKMeansExample$1.call(JavaKMeansExample.java:175) ~[spark-examples_2.12-3.4.0.jar:3.4.0]
	at org.apache.spark.sql.catalyst.expressions.GeneratedClass$GeneratedIteratorForCodegenStage1.mapelements_doConsume_0$(Unknown Source) ~[?:?]
	at org.apache.spark.sql.catalyst.expressions.GeneratedClass$GeneratedIteratorForCodegenStage1.deserializetoobject_doConsume_0$(Unknown Source) ~[?:?]
	at org.apache.spark.sql.catalyst.expressions.GeneratedClass$GeneratedIteratorForCodegenStage1.processNext(Unknown Source) ~[?:?]
	at org.apache.spark.sql.execution.BufferedRowIterator.hasNext(BufferedRowIterator.java:43) ~[spark-sql_2.12-3.4.0.jar:3.4.0]
	at org.apache.spark.sql.execution.WholeStageCodegenExec$$anon$1.hasNext(WholeStageCodegenExec.scala:760) ~[spark-sql_2.12-3.4.0.jar:3.4.0]
	at org.apache.spark.sql.execution.SparkPlan.$anonfun$getByteArrayRdd$1(SparkPlan.scala:388) ~[spark-sql_2.12-3.4.0.jar:3.4.0]
	at org.apache.spark.rdd.RDD.$anonfun$mapPartitionsInternal$2(RDD.scala:906) ~[spark-core_2.12-3.4.0.jar:3.4.0]
	at org.apache.spark.rdd.RDD.$anonfun$mapPartitionsInternal$2$adapted(RDD.scala:906) ~[spark-core_2.12-3.4.0.jar:3.4.0]
	at org.apache.spark.rdd.MapPartitionsRDD.compute(MapPartitionsRDD.scala:52) ~[spark-core_2.12-3.4.0.jar:3.4.0]
	at org.apache.spark.rdd.RDD.computeOrReadCheckpoint(RDD.scala:376) ~[spark-core_2.12-3.4.0.jar:3.4.0]
	at org.apache.spark.rdd.RDD.iterator(RDD.scala:340) ~[spark-core_2.12-3.4.0.jar:3.4.0]
	at org.apache.spark.scheduler.ResultTask.runTask(ResultTask.scala:92) ~[spark-core_2.12-3.4.0.jar:3.4.0]
	at org.apache.spark.TaskContext.runTaskWithListeners(TaskContext.scala:161) ~[spark-core_2.12-3.4.0.jar:3.4.0]
	at org.apache.spark.scheduler.Task.run(Task.scala:139) ~[spark-core_2.12-3.4.0.jar:3.4.0]
	at org.apache.spark.executor.Executor$TaskRunner.$anonfun$run$3(Executor.scala:554) ~[spark-core_2.12-3.4.0.jar:3.4.0]
	at org.apache.spark.util.Utils$.tryWithSafeFinally(Utils.scala:1546) ~[spark-core_2.12-3.4.0.jar:3.4.0]
	at org.apache.spark.executor.Executor$TaskRunner.run(Executor.scala:557) ~[spark-core_2.12-3.4.0.jar:3.4.0]
	at java.util.concurrent.ThreadPoolExecutor.runWorker(ThreadPoolExecutor.java:1128) ~[?:?]
	at java.util.concurrent.ThreadPoolExecutor$Worker.run(ThreadPoolExecutor.java:628) ~[?:?]
	at java.lang.Thread.run(Thread.java:829) ~[?:?]
16:49:24.826 [task-result-getter-1] WARN org.apache.spark.scheduler.TaskSetManager - Lost task 0.0 in stage 35.0 (TID 64) (10.200.16.49 executor driver): java.lang.NegativeArraySizeException: -727379968
	at org.apache.spark.examples.ml.JavaKMeansExample$1.call(JavaKMeansExample.java:179)
	at org.apache.spark.examples.ml.JavaKMeansExample$1.call(JavaKMeansExample.java:175)
	at org.apache.spark.sql.catalyst.expressions.GeneratedClass$GeneratedIteratorForCodegenStage1.mapelements_doConsume_0$(Unknown Source)
	at org.apache.spark.sql.catalyst.expressions.GeneratedClass$GeneratedIteratorForCodegenStage1.deserializetoobject_doConsume_0$(Unknown Source)
	at org.apache.spark.sql.catalyst.expressions.GeneratedClass$GeneratedIteratorForCodegenStage1.processNext(Unknown Source)
	at org.apache.spark.sql.execution.BufferedRowIterator.hasNext(BufferedRowIterator.java:43)
	at org.apache.spark.sql.execution.WholeStageCodegenExec$$anon$1.hasNext(WholeStageCodegenExec.scala:760)
	at org.apache.spark.sql.execution.SparkPlan.$anonfun$getByteArrayRdd$1(SparkPlan.scala:388)
	at org.apache.spark.rdd.RDD.$anonfun$mapPartitionsInternal$2(RDD.scala:906)
	at org.apache.spark.rdd.RDD.$anonfun$mapPartitionsInternal$2$adapted(RDD.scala:906)
	at org.apache.spark.rdd.MapPartitionsRDD.compute(MapPartitionsRDD.scala:52)
	at org.apache.spark.rdd.RDD.computeOrReadCheckpoint(RDD.scala:376)
	at org.apache.spark.rdd.RDD.iterator(RDD.scala:340)
	at org.apache.spark.scheduler.ResultTask.runTask(ResultTask.scala:92)
	at org.apache.spark.TaskContext.runTaskWithListeners(TaskContext.scala:161)
	at org.apache.spark.scheduler.Task.run(Task.scala:139)
	at org.apache.spark.executor.Executor$TaskRunner.$anonfun$run$3(Executor.scala:554)
	at org.apache.spark.util.Utils$.tryWithSafeFinally(Utils.scala:1546)
	at org.apache.spark.executor.Executor$TaskRunner.run(Executor.scala:557)
	at java.base/java.util.concurrent.ThreadPoolExecutor.runWorker(ThreadPoolExecutor.java:1128)
	at java.base/java.util.concurrent.ThreadPoolExecutor$Worker.run(ThreadPoolExecutor.java:628)
	at java.base/java.lang.Thread.run(Thread.java:829)
 [] [ThreadID: 70] [ThreadName: task-result-getter-1] [Caller: org.apache.spark.scheduler.TaskSetManageraller] [Class: org.apache.spark.internal.Logging] [Method: logWarning] [File: Logging.scala] [Line: 72]
16:49:24.827 [task-result-getter-1] ERROR org.apache.spark.scheduler.TaskSetManager - Task 0 in stage 35.0 failed 1 times; aborting job [] [ThreadID: 70] [ThreadName: task-result-getter-1] [Caller: org.apache.spark.scheduler.TaskSetManageraller] [Class: org.apache.spark.internal.Logging] [Method: logError] [File: Logging.scala] [Line: 76]
16:49:24.829 [task-result-getter-1] INFO org.apache.spark.scheduler.TaskSchedulerImpl - Removed TaskSet 35.0, whose tasks have all completed, from pool  [] [ThreadID: 70] [ThreadName: task-result-getter-1] [Caller: org.apache.spark.scheduler.TaskSchedulerImplaller] [Class: org.apache.spark.internal.Logging] [Method: logInfo] [File: Logging.scala] [Line: 60]
16:49:24.830 [task-result-getter-0] INFO org.apache.spark.scheduler.TaskSetManager - Lost task 1.0 in stage 35.0 (TID 65) on 10.200.16.49, executor driver: java.lang.NegativeArraySizeException (-727379968) [duplicate 1] [] [ThreadID: 69] [ThreadName: task-result-getter-0] [Caller: org.apache.spark.scheduler.TaskSetManageraller] [Class: org.apache.spark.internal.Logging] [Method: logInfo] [File: Logging.scala] [Line: 60]
16:49:24.830 [task-result-getter-0] INFO org.apache.spark.scheduler.TaskSchedulerImpl - Removed TaskSet 35.0, whose tasks have all completed, from pool  [] [ThreadID: 69] [ThreadName: task-result-getter-0] [Caller: org.apache.spark.scheduler.TaskSchedulerImplaller] [Class: org.apache.spark.internal.Logging] [Method: logInfo] [File: Logging.scala] [Line: 60]
16:49:24.831 [dag-scheduler-event-loop] INFO org.apache.spark.scheduler.TaskSchedulerImpl - Cancelling stage 35 [] [ThreadID: 49] [ThreadName: dag-scheduler-event-loop] [Caller: org.apache.spark.scheduler.TaskSchedulerImplaller] [Class: org.apache.spark.internal.Logging] [Method: logInfo] [File: Logging.scala] [Line: 60]
16:49:24.831 [dag-scheduler-event-loop] INFO org.apache.spark.scheduler.TaskSchedulerImpl - Killing all running tasks in stage 35: Stage cancelled [] [ThreadID: 49] [ThreadName: dag-scheduler-event-loop] [Caller: org.apache.spark.scheduler.TaskSchedulerImplaller] [Class: org.apache.spark.internal.Logging] [Method: logInfo] [File: Logging.scala] [Line: 60]
16:49:24.832 [dag-scheduler-event-loop] INFO org.apache.spark.scheduler.DAGScheduler - ResultStage 35 (collect at JavaKMeansExample.java:185) failed in 0.101 s due to Job aborted due to stage failure: Task 0 in stage 35.0 failed 1 times, most recent failure: Lost task 0.0 in stage 35.0 (TID 64) (10.200.16.49 executor driver): java.lang.NegativeArraySizeException: -727379968
	at org.apache.spark.examples.ml.JavaKMeansExample$1.call(JavaKMeansExample.java:179)
	at org.apache.spark.examples.ml.JavaKMeansExample$1.call(JavaKMeansExample.java:175)
	at org.apache.spark.sql.catalyst.expressions.GeneratedClass$GeneratedIteratorForCodegenStage1.mapelements_doConsume_0$(Unknown Source)
	at org.apache.spark.sql.catalyst.expressions.GeneratedClass$GeneratedIteratorForCodegenStage1.deserializetoobject_doConsume_0$(Unknown Source)
	at org.apache.spark.sql.catalyst.expressions.GeneratedClass$GeneratedIteratorForCodegenStage1.processNext(Unknown Source)
	at org.apache.spark.sql.execution.BufferedRowIterator.hasNext(BufferedRowIterator.java:43)
	at org.apache.spark.sql.execution.WholeStageCodegenExec$$anon$1.hasNext(WholeStageCodegenExec.scala:760)
	at org.apache.spark.sql.execution.SparkPlan.$anonfun$getByteArrayRdd$1(SparkPlan.scala:388)
	at org.apache.spark.rdd.RDD.$anonfun$mapPartitionsInternal$2(RDD.scala:906)
	at org.apache.spark.rdd.RDD.$anonfun$mapPartitionsInternal$2$adapted(RDD.scala:906)
	at org.apache.spark.rdd.MapPartitionsRDD.compute(MapPartitionsRDD.scala:52)
	at org.apache.spark.rdd.RDD.computeOrReadCheckpoint(RDD.scala:376)
	at org.apache.spark.rdd.RDD.iterator(RDD.scala:340)
	at org.apache.spark.scheduler.ResultTask.runTask(ResultTask.scala:92)
	at org.apache.spark.TaskContext.runTaskWithListeners(TaskContext.scala:161)
	at org.apache.spark.scheduler.Task.run(Task.scala:139)
	at org.apache.spark.executor.Executor$TaskRunner.$anonfun$run$3(Executor.scala:554)
	at org.apache.spark.util.Utils$.tryWithSafeFinally(Utils.scala:1546)
	at org.apache.spark.executor.Executor$TaskRunner.run(Executor.scala:557)
	at java.base/java.util.concurrent.ThreadPoolExecutor.runWorker(ThreadPoolExecutor.java:1128)
	at java.base/java.util.concurrent.ThreadPoolExecutor$Worker.run(ThreadPoolExecutor.java:628)
	at java.base/java.lang.Thread.run(Thread.java:829)

Driver stacktrace: [] [ThreadID: 49] [ThreadName: dag-scheduler-event-loop] [Caller: org.apache.spark.scheduler.DAGScheduleraller] [Class: org.apache.spark.internal.Logging] [Method: logInfo] [File: Logging.scala] [Line: 60]
16:49:24.835 [main] INFO org.apache.spark.scheduler.DAGScheduler - Job 22 failed: collect at JavaKMeansExample.java:185, took 0.106645 s [] [ThreadID: 1] [ThreadName: main] [Caller: org.apache.spark.scheduler.DAGScheduleraller] [Class: org.apache.spark.internal.Logging] [Method: logInfo] [File: Logging.scala] [Line: 60]
Exception in thread "main" org.apache.spark.SparkException: Job aborted due to stage failure: Task 0 in stage 35.0 failed 1 times, most recent failure: Lost task 0.0 in stage 35.0 (TID 64) (10.200.16.49 executor driver): java.lang.NegativeArraySizeException: -727379968
	at org.apache.spark.examples.ml.JavaKMeansExample$1.call(JavaKMeansExample.java:179)
	at org.apache.spark.examples.ml.JavaKMeansExample$1.call(JavaKMeansExample.java:175)
	at org.apache.spark.sql.catalyst.expressions.GeneratedClass$GeneratedIteratorForCodegenStage1.mapelements_doConsume_0$(Unknown Source)
	at org.apache.spark.sql.catalyst.expressions.GeneratedClass$GeneratedIteratorForCodegenStage1.deserializetoobject_doConsume_0$(Unknown Source)
	at org.apache.spark.sql.catalyst.expressions.GeneratedClass$GeneratedIteratorForCodegenStage1.processNext(Unknown Source)
	at org.apache.spark.sql.execution.BufferedRowIterator.hasNext(BufferedRowIterator.java:43)
	at org.apache.spark.sql.execution.WholeStageCodegenExec$$anon$1.hasNext(WholeStageCodegenExec.scala:760)
	at org.apache.spark.sql.execution.SparkPlan.$anonfun$getByteArrayRdd$1(SparkPlan.scala:388)
	at org.apache.spark.rdd.RDD.$anonfun$mapPartitionsInternal$2(RDD.scala:906)
	at org.apache.spark.rdd.RDD.$anonfun$mapPartitionsInternal$2$adapted(RDD.scala:906)
	at org.apache.spark.rdd.MapPartitionsRDD.compute(MapPartitionsRDD.scala:52)
	at org.apache.spark.rdd.RDD.computeOrReadCheckpoint(RDD.scala:376)
	at org.apache.spark.rdd.RDD.iterator(RDD.scala:340)
	at org.apache.spark.scheduler.ResultTask.runTask(ResultTask.scala:92)
	at org.apache.spark.TaskContext.runTaskWithListeners(TaskContext.scala:161)
	at org.apache.spark.scheduler.Task.run(Task.scala:139)
	at org.apache.spark.executor.Executor$TaskRunner.$anonfun$run$3(Executor.scala:554)
	at org.apache.spark.util.Utils$.tryWithSafeFinally(Utils.scala:1546)
	at org.apache.spark.executor.Executor$TaskRunner.run(Executor.scala:557)
	at java.base/java.util.concurrent.ThreadPoolExecutor.runWorker(ThreadPoolExecutor.java:1128)
	at java.base/java.util.concurrent.ThreadPoolExecutor$Worker.run(ThreadPoolExecutor.java:628)
	at java.base/java.lang.Thread.run(Thread.java:829)

Driver stacktrace:
	at org.apache.spark.scheduler.DAGScheduler.failJobAndIndependentStages(DAGScheduler.scala:2785)
	at org.apache.spark.scheduler.DAGScheduler.$anonfun$abortStage$2(DAGScheduler.scala:2721)
	at org.apache.spark.scheduler.DAGScheduler.$anonfun$abortStage$2$adapted(DAGScheduler.scala:2720)
	at scala.collection.mutable.ResizableArray.foreach(ResizableArray.scala:62)
	at scala.collection.mutable.ResizableArray.foreach$(ResizableArray.scala:55)
	at scala.collection.mutable.ArrayBuffer.foreach(ArrayBuffer.scala:49)
	at org.apache.spark.scheduler.DAGScheduler.abortStage(DAGScheduler.scala:2720)
	at org.apache.spark.scheduler.DAGScheduler.$anonfun$handleTaskSetFailed$1(DAGScheduler.scala:1206)
	at org.apache.spark.scheduler.DAGScheduler.$anonfun$handleTaskSetFailed$1$adapted(DAGScheduler.scala:1206)
	at scala.Option.foreach(Option.scala:407)
	at org.apache.spark.scheduler.DAGScheduler.handleTaskSetFailed(DAGScheduler.scala:1206)
	at org.apache.spark.scheduler.DAGSchedulerEventProcessLoop.doOnReceive(DAGScheduler.scala:2984)
	at org.apache.spark.scheduler.DAGSchedulerEventProcessLoop.onReceive(DAGScheduler.scala:2923)
	at org.apache.spark.scheduler.DAGSchedulerEventProcessLoop.onReceive(DAGScheduler.scala:2912)
	at org.apache.spark.util.EventLoop$$anon$1.run(EventLoop.scala:49)
	at org.apache.spark.scheduler.DAGScheduler.runJob(DAGScheduler.scala:971)
	at org.apache.spark.SparkContext.runJob(SparkContext.scala:2288)
	at org.apache.spark.SparkContext.runJob(SparkContext.scala:2316)
	at org.apache.spark.SparkContext.runJob(SparkContext.scala:2343)
	at org.apache.spark.SparkContext.runJob(SparkContext.scala:2386)
	at org.apache.spark.rdd.RDD.$anonfun$collect$1(RDD.scala:1037)
	at org.apache.spark.rdd.RDDOperationScope$.withScope(RDDOperationScope.scala:151)
	at org.apache.spark.rdd.RDDOperationScope$.withScope(RDDOperationScope.scala:112)
	at org.apache.spark.rdd.RDD.withScope(RDD.scala:417)
	at org.apache.spark.rdd.RDD.collect(RDD.scala:1036)
	at org.apache.spark.sql.execution.SparkPlan.executeCollect(SparkPlan.scala:448)
	at org.apache.spark.sql.Dataset.collectFromPlan(Dataset.scala:4177)
	at org.apache.spark.sql.Dataset.$anonfun$collect$1(Dataset.scala:3418)
	at org.apache.spark.sql.Dataset.$anonfun$withAction$2(Dataset.scala:4167)
	at org.apache.spark.sql.execution.QueryExecution$.withInternalError(QueryExecution.scala:526)
	at org.apache.spark.sql.Dataset.$anonfun$withAction$1(Dataset.scala:4165)
	at org.apache.spark.sql.execution.SQLExecution$.$anonfun$withNewExecutionId$6(SQLExecution.scala:118)
	at org.apache.spark.sql.execution.SQLExecution$.withSQLConfPropagated(SQLExecution.scala:195)
	at org.apache.spark.sql.execution.SQLExecution$.$anonfun$withNewExecutionId$1(SQLExecution.scala:103)
	at org.apache.spark.sql.SparkSession.withActive(SparkSession.scala:849)
	at org.apache.spark.sql.execution.SQLExecution$.withNewExecutionId(SQLExecution.scala:65)
	at org.apache.spark.sql.Dataset.withAction(Dataset.scala:4165)
	at org.apache.spark.sql.Dataset.collect(Dataset.scala:3418)
	at org.apache.spark.examples.ml.JavaKMeansExample.main(JavaKMeansExample.java:185)
	at java.base/jdk.internal.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at java.base/jdk.internal.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:62)
	at java.base/jdk.internal.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
	at java.base/java.lang.reflect.Method.invoke(Method.java:566)
	at org.apache.spark.deploy.JavaMainApplication.start(SparkApplication.scala:52)
	at org.apache.spark.deploy.SparkSubmit.org$apache$spark$deploy$SparkSubmit$$runMain(SparkSubmit.scala:1020)
	at org.apache.spark.deploy.SparkSubmit.doRunMain$1(SparkSubmit.scala:192)
	at org.apache.spark.deploy.SparkSubmit.submit(SparkSubmit.scala:215)
	at org.apache.spark.deploy.SparkSubmit.doSubmit(SparkSubmit.scala:91)
	at org.apache.spark.deploy.SparkSubmit$$anon$2.doSubmit(SparkSubmit.scala:1111)
	at org.apache.spark.deploy.SparkSubmit$.main(SparkSubmit.scala:1120)
	at org.apache.spark.deploy.SparkSubmit.main(SparkSubmit.scala)
Caused by: java.lang.NegativeArraySizeException: -727379968
	at org.apache.spark.examples.ml.JavaKMeansExample$1.call(JavaKMeansExample.java:179)
	at org.apache.spark.examples.ml.JavaKMeansExample$1.call(JavaKMeansExample.java:175)
	at org.apache.spark.sql.catalyst.expressions.GeneratedClass$GeneratedIteratorForCodegenStage1.mapelements_doConsume_0$(Unknown Source)
	at org.apache.spark.sql.catalyst.expressions.GeneratedClass$GeneratedIteratorForCodegenStage1.deserializetoobject_doConsume_0$(Unknown Source)
	at org.apache.spark.sql.catalyst.expressions.GeneratedClass$GeneratedIteratorForCodegenStage1.processNext(Unknown Source)
	at org.apache.spark.sql.execution.BufferedRowIterator.hasNext(BufferedRowIterator.java:43)
	at org.apache.spark.sql.execution.WholeStageCodegenExec$$anon$1.hasNext(WholeStageCodegenExec.scala:760)
	at org.apache.spark.sql.execution.SparkPlan.$anonfun$getByteArrayRdd$1(SparkPlan.scala:388)
	at org.apache.spark.rdd.RDD.$anonfun$mapPartitionsInternal$2(RDD.scala:906)
	at org.apache.spark.rdd.RDD.$anonfun$mapPartitionsInternal$2$adapted(RDD.scala:906)
	at org.apache.spark.rdd.MapPartitionsRDD.compute(MapPartitionsRDD.scala:52)
	at org.apache.spark.rdd.RDD.computeOrReadCheckpoint(RDD.scala:376)
	at org.apache.spark.rdd.RDD.iterator(RDD.scala:340)
	at org.apache.spark.scheduler.ResultTask.runTask(ResultTask.scala:92)
	at org.apache.spark.TaskContext.runTaskWithListeners(TaskContext.scala:161)
	at org.apache.spark.scheduler.Task.run(Task.scala:139)
	at org.apache.spark.executor.Executor$TaskRunner.$anonfun$run$3(Executor.scala:554)
	at org.apache.spark.util.Utils$.tryWithSafeFinally(Utils.scala:1546)
	at org.apache.spark.executor.Executor$TaskRunner.run(Executor.scala:557)
	at java.base/java.util.concurrent.ThreadPoolExecutor.runWorker(ThreadPoolExecutor.java:1128)
	at java.base/java.util.concurrent.ThreadPoolExecutor$Worker.run(ThreadPoolExecutor.java:628)
	at java.base/java.lang.Thread.run(Thread.java:829)
16:49:24.964 [shutdown-hook-0] INFO org.apache.spark.SparkContext - Invoking st
