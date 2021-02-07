### 1.大数据分析的作用  
(1)分析公司内部流程历史数据得到用户偏好，向用户推荐产品和服务  
(2)分析交易流量，欺诈检测  
(3)优化流程   
### 2.为了实现数据分析，需要聚集->处理->分析数据的流程，但是大规模的数据集使得单台pc处理很困难  
### 3.需要掌握的工具箱  
存储数据-hadoop分布式文件系统：HDFS,拥有1000个节点的HDFS文件系统，每天大约10个节点会崩溃,但是数据仍然是安全的，
因为文件以chunk或block的形式存储在不同的节点上  
处理数据-mapReduce，需要知道把一个给定的计算任务转换成一些mapreduce的job链  
很多不同的框架使用mapreduce计算模式，spark通过在内存中计算大大降低了计算时间  
### 4.课程目标
(1)学会设计分布式文件系统  
(2)学会通过cli使用HDFS  
(3)用python写hadoop的mapreduce应用  
(4)将一个任务转换为mapreduce job链  
(5)对于内存计算,了解RDD(resilient distributed dataset),并且直到在spark中如何使用它  
data engineer   reponsibility:collecting,storing,processing,delivering data  
