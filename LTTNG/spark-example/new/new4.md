% number of execution is fixed by spark
% for example if memory and cpu of woker is 4
% and you set 1 for cpu and memory of each executor you will 4 executor per worker

mvn clean compile

lttng enable-event --log4j jello && \

```
http://localhost:9870/dfshealth.html#tab-datanode
http://localhost:8088/cluster
http://localhost:8042/node



mvn install:install-file \
-Dfile=/usr/local/share/java/lttng-ust-agent-log4j-1.0.0.jar \
-DgroupId=org.lttng.ust.agent \
-DartifactId=lttng-ust-agent-log4j \
-Dversion=1.0.0 \
-Dpackaging=jar

mvn install:install-file \
-Dfile=/usr/local/share/java/lttng-ust-agent-log4j2-1.0.0.jar \
-DgroupId=org.lttng.ust.agent \
-DartifactId=lttng-ust-agent-log4j2 \
-Dversion=2.1.0 \
-Dpackaging=jar

./build/mvn -Pyarn -Phadoop-3 -Dhadoop.version=3.3.4 -DskipTests clean package -rf :spark-examples_2.12

PATH=$PATH:/usr/local/hadoop/sbin
start-all.sh
bash start-dfs.sh
bash start-yarn.sh


 ``` 


```
%FROM openjdk:11-jdk
%ARG SPARK_VERSION=3.4.0
%ARG HADOOP_VERSION=3.4.0
%lttng (LTTng Trace Control) 2.14.0-pre - O-Beer - v2.12.0-%rc1-1647-gc91ccadee
%Version: 2023-12 (4.30.0)
%Eclipse Public License - v 2.0
%apache spark Using Scala version 2.12.17, OpenJDK 64-Bit Server VM, 11.0.22
```
