1.Start HDFS daemons ：%HADOOP_HOME%\sbin\start-dfs.cmd
2.Step 9 - Start YARN daemons：%HADOOP_HOME%\sbin\start-yarn.cmd
HDFS Namenode information UI：http://localhost:9870/dfshealth.html#tab-overview
HDFS Datanode information UI：http://localhost:9864/datanode.html
YARN resource manager UI：http://localhost:8088
3. Shutdown YARN & HDFS daemons：
%HADOOP_HOME%\sbin\stop-yarn.cmd
%HADOOP_HOME%\sbin\stop-dfs.cmd