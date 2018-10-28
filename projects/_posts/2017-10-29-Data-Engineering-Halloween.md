---
layout: post
title: "Data Engineering: HDFS"
date: 2017-10-29
---

Linnea and I explored stuff about Datanodes and HDFS Balancer.

We summarized our [progress](https://docs.google.com/presentation/d/1H7q11GCnL5IkiqnnAAaOmHJH8gfR188CL_uopxk-hVw/edit#slide=id.p) this week on Google Drive and presented it to the entire server team. 

We have also started a Google Doc shared with the entire team where we post diagnostic reports. The idea is to assemble a collection of common issues discovered and solved by the CDS Data Enginnering team members.

Examples of such include: 
```
Hadoop Start & Setup

Category: Hadoop Start
User: T. K. Daisy Leung
Date: 10/22/17

Missing namenode every time restart hadoop
Problem Description: Missing namenode every time restart hadoop, forcing me to reformat it every time
Current Configuration: JAVA 8.0 + hadoop 2.8.1 + mac OSX El Capitan
Logs: 
Screenshot of Error Message: 
Screenshot of Spark UI:
Solution (include links and resources used): 
Edit $HADOOP_INSTALL/etc/hdfs-site.xml and create the respective directories for Namenode and Datanode.

- Edit $HADOOP_INSTALL/etc/hdfs-site.xml
<?xml version="1.0" encoding="UTF-8"?>
<?xml-stylesheet type="text/xsl" href="configuration.xsl"?>

<configuration>
<property>
<name>dfs.name.dir</name>
<value>file:///Users/admin/Downloads/hadoop-2.8.1/hdfs/namenode</value>
</property>
<property>
<name>dfs.data.dir</name>
<value>file:///Users/admin/Downloads/hadoop-2.8.1/hdfs/datanode</value>
</property>
<property>
<name>dfs.replication</name>
<value>1</value>
</property>
</configuration>

admin@dhcp-ccc-5418:~/Downloads/hadoop-2.8.1$sbin/stop-all.sh
mkdir the respective directories first:
admin@dhcp-ccc-5418:~/Downloads/hadoop-2.8.1$ mkdir -p hdfs/namenode
admin@dhcp-ccc-5418:~/Downloads/hadoop-2.8.1$ mkdir -p hdfs/datanode
admin@MacBook-Air:~/Downloads/hadoop-2.8.1$ bin/hdfs namenode -format
admin@MacBook-Air:~/Downloads/hadoop-2.8.1$ sbin/start-all.sh 
dmin@MacBook-Air:~/Downloads/hadoop-2.8.1$ jps
admin@MacBook-Air:~/Downloads/hadoop-2.8.1$ sbin/stop-all.sh 
admin@MacBook-Air:~/Downloads/hadoop-2.8.1$ sbin/start-all.sh 
dmin@MacBook-Air:~/Downloads/hadoop-2.8.1$ jps

Time Spent on Issue (in hours): .5 
```
---
```

Hadoop connection failed
Problem Description: Hadoop connection failed
Current Configuration: Java 8.0 + Hadoop 2.8.1 + Mac El Capitan
Logs: 
admin@MacBook-Air:~/Downloads/hadoop-2.8.1$ bin/hadoop fs -ls /yelp
17/10/22 17:16:54 WARN util.NativeCodeLoader: Unable to load native-hadoop library for your platform... using builtin-java classes where applicable
17/10/22 17:16:55 WARN ipc.Client: Failed to connect to server: localhost/127.0.0.1:9000: try once and fail.
java.net.ConnectException: Connection refused
at sun.nio.ch.SocketChannelImpl.checkConnect(Native Method)
at sun.nio.ch.SocketChannelImpl.finishConnect(SocketChannelImpl.java:717)
at org.apache.hadoop.net.SocketIOWithTimeout.connect(SocketIOWithTimeout.java:206)
at org.apache.hadoop.net.NetUtils.connect(NetUtils.java:531)
at org.apache.hadoop.net.NetUtils.connect(NetUtils.java:495)
at org.apache.hadoop.ipc.Client$Connection.setupConnection(Client.java:681)
at org.apache.hadoop.ipc.Client$Connection.setupIOstreams(Client.java:777)
at org.apache.hadoop.ipc.Client$Connection.access$3500(Client.java:409)
at org.apache.hadoop.ipc.Client.getConnection(Client.java:1542)
at org.apache.hadoop.ipc.Client.call(Client.java:1373)
at org.apache.hadoop.ipc.Client.call(Client.java:1337)
at org.apache.hadoop.ipc.ProtobufRpcEngine$Invoker.invoke(ProtobufRpcEngine.java:227)
at org.apache.hadoop.ipc.ProtobufRpcEngine$Invoker.invoke(ProtobufRpcEngine.java:116)
at com.sun.proxy.$Proxy10.getFileInfo(Unknown Source)
at org.apache.hadoop.hdfs.protocolPB.ClientNamenodeProtocolTranslatorPB.getFileInfo(ClientNamenodeProtocolTranslatorPB.java:787)
at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:62)
at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
at java.lang.reflect.Method.invoke(Method.java:498)
at org.apache.hadoop.io.retry.RetryInvocationHandler.invokeMethod(RetryInvocationHandler.java:398)
at org.apache.hadoop.io.retry.RetryInvocationHandler$Call.invokeMethod(RetryInvocationHandler.java:163)
at org.apache.hadoop.io.retry.RetryInvocationHandler$Call.invoke(RetryInvocationHandler.java:155)
at org.apache.hadoop.io.retry.RetryInvocationHandler$Call.invokeOnce(RetryInvocationHandler.java:95)
at org.apache.hadoop.io.retry.RetryInvocationHandler.invoke(RetryInvocationHandler.java:335)
at com.sun.proxy.$Proxy11.getFileInfo(Unknown Source)
at org.apache.hadoop.hdfs.DFSClient.getFileInfo(DFSClient.java:1700)
at org.apache.hadoop.hdfs.DistributedFileSystem$27.doCall(DistributedFileSystem.java:1436)
at org.apache.hadoop.hdfs.DistributedFileSystem$27.doCall(DistributedFileSystem.java:1433)
at org.apache.hadoop.fs.FileSystemLinkResolver.resolve(FileSystemLinkResolver.java:81)
at org.apache.hadoop.hdfs.DistributedFileSystem.getFileStatus(DistributedFileSystem.java:1433)
at org.apache.hadoop.fs.Globber.getFileStatus(Globber.java:64)
at org.apache.hadoop.fs.Globber.doGlob(Globber.java:269)
at org.apache.hadoop.fs.Globber.glob(Globber.java:148)
at org.apache.hadoop.fs.FileSystem.globStatus(FileSystem.java:1685)
at org.apache.hadoop.fs.shell.PathData.expandAsGlob(PathData.java:326)
at org.apache.hadoop.fs.shell.Command.expandArgument(Command.java:235)
at org.apache.hadoop.fs.shell.Command.expandArguments(Command.java:218)
at org.apache.hadoop.fs.shell.FsCommand.processRawArguments(FsCommand.java:103)
at org.apache.hadoop.fs.shell.Command.run(Command.java:165)
at org.apache.hadoop.fs.FsShell.run(FsShell.java:315)
at org.apache.hadoop.util.ToolRunner.run(ToolRunner.java:76)
at org.apache.hadoop.util.ToolRunner.run(ToolRunner.java:90)
at org.apache.hadoop.fs.FsShell.main(FsShell.java:378)
ls: Call From dhcp-ccc-5418.eduroam.cornell.edu/10.128.21.42 to localhost:9000 failed on connection exception: java.net.ConnectException: Connection refused; For more details see:  http://wiki.apache.org/hadoop/ConnectionRefused

Error Message: 
ls: Call From dhcp-ccc-5418.eduroam.cornell.edu/10.128.21.42 to localhost:9000 failed on connection exception: java.net.ConnectException: Connection refused; For more details see:  http://wiki.apache.org/hadoop/ConnectionRefused

Screenshot of Spark UI:
Solution (include links and resources used): 
run "sbin/start-all.sh" before running "bin/hadoop fs"

Time Spent on Issue (in hours): .05
```
---
```
Pyspark import error
Category: Hadoop Start
User: T. K. Daisy Leung
Date: 10/22/17

                Getting errors suddenly about sc=SparkContext()
Problem Description: error when trying to set sc=SparkContext(), but notebook was working before..    
Current Configuration: JAVA 8.0 + hadoop 2.8.1 + mac OSX El Capitan + spark 2.2.0 (but installed with pip) 
Logs: 
Screenshot of Error Message: 

---------------------------------------------------------------------------
Exception                                 Traceback (most recent call last)
<ipython-input-2-bd8ed31b87ac> in <module>()
      2 from pyspark.sql.session import SparkSession
      3 try:
----> 4     sc = SparkContext()
      5 except ValueError:
      6     pass

/Users/admin/anaconda/lib/python2.7/site-packages/pyspark/context.pyc in __init__(self, master, appName, sparkHome, pyFiles, environment, batchSize, serializer, conf, gateway, jsc, profiler_cls)
    113         """
    114         self._callsite = first_spark_call() or CallSite(None, None, None)
--> 115         SparkContext._ensure_initialized(self, gateway=gateway, conf=conf)
    116         try:
    117             self._do_init(master, appName, sparkHome, pyFiles, environment, batchSize, serializer,

/Users/admin/anaconda/lib/python2.7/site-packages/pyspark/context.pyc in _ensure_initialized(cls, instance, gateway, conf)
    281         with SparkContext._lock:
    282             if not SparkContext._gateway:
--> 283                 SparkContext._gateway = gateway or launch_gateway(conf)
    284                 SparkContext._jvm = SparkContext._gateway.jvm
    285 

/Users/admin/anaconda/lib/python2.7/site-packages/pyspark/java_gateway.pyc in launch_gateway(conf)
     93                 callback_socket.close()
     94         if gateway_port is None:
---> 95             raise Exception("Java gateway process exited before sending the driver its port number")
     96 
     97         # In Windows, ensure the Java child processes do not linger after Python has exited.

Exception: Java gateway process exited before sending the driver its port number


Screenshot of Spark UI:
Solution (include links and resources used): 
Perhaps I have changed my .dotfiles in the meantime?? (I don’t remember that). Maybe: because I added “exec(open(os.path.join(spark_home, 'python/pyspark/shell.py')).read())” to my .ipython/profile_pyspark/
ipython_notebook_config.py

But seems like it’s working in the background. Will just use try and except to work around for the meantime.

try:
    sc = SparkContext()     
except:
    pass
# spark = SparkSession(sc)

In [1]:
Sc
Out[1]:
SparkContext
Spark UI
Version
v2.2.0
Master
yarn
AppName
PySparkShell


Time Spent on Issue (in hours): 0.05
```

