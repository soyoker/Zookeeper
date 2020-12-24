# Zookeeper

工作机制：（文件系统+通知机制）

Zookeeper从设计模式角度来理解：是一个基于观察者模式设计的分布式服务管理框架，它负责存储和管理大家都关心的数据，然后接受观察者的注册，一旦这些数据的状态发生变化，Zookeeper就将负责通知已经在Zookeeper上注册的那些观察者做出相应的反应。

zookeeper特点

Zookeeper由一个leader,多个Follower组成的集群

集群中只要有半数以上节点存货，集群就能正常服务

全局数据一致：每个Server保存一份相同的数据副本，Client无论连接到哪个Server，数据都是一致的。

更新请求顺序进行，来自同一个Client的更新请求按其发送顺序依次执行。

数据更新原子性，一次数据更新要么成功，要么失败。

实时性，在一定时间范围内，Client能读到最新数据。

数据结构：

ZooKeeper数据模型的结构与Unix文件系统很类似，整体上可以看作是一棵树，每个节点称做一个ZNode。每一个ZNode默认能够存储1MB的数据，每个ZNode都可以通过其路径唯一标识。

应用场景：

提供的服务包括：统一命名服务、统一配置管理、统一集群管理、服务器节点动态上下线、软负载均衡等。


### Zookeeper 安装部署

#### 单机节点：
-   环境准备（安装openjdk，下载zookeeper软件包）
```bash
# 从yum仓库查找openjdk
[root@VM-0-13-centos zookeeper]#yum search java | grep jdk
```
```bash
ldapjdk-javadoc.noarch : Javadoc for ldapjdk
java-1.6.0-openjdk.x86_64 : OpenJDK Runtime Environment
java-1.6.0-openjdk-demo.x86_64 : OpenJDK Demos
java-1.6.0-openjdk-devel.x86_64 : OpenJDK Development Environment
java-1.6.0-openjdk-javadoc.x86_64 : OpenJDK API Documentation
java-1.6.0-openjdk-src.x86_64 : OpenJDK Source Bundle
java-1.7.0-openjdk.x86_64 : OpenJDK Runtime Environment
java-1.7.0-openjdk-accessibility.x86_64 : OpenJDK accessibility connector
java-1.7.0-openjdk-demo.x86_64 : OpenJDK Demos
java-1.7.0-openjdk-devel.x86_64 : OpenJDK Development Environment
java-1.7.0-openjdk-headless.x86_64 : The OpenJDK runtime environment without
java-1.7.0-openjdk-javadoc.noarch : OpenJDK API Documentation
java-1.7.0-openjdk-src.x86_64 : OpenJDK Source Bundle
java-1.8.0-openjdk.i686 : OpenJDK Runtime Environment 8
java-1.8.0-openjdk.x86_64 : OpenJDK Runtime Environment 8
java-1.8.0-openjdk-accessibility.i686 : OpenJDK accessibility connector
java-1.8.0-openjdk-accessibility.x86_64 : OpenJDK accessibility connector
java-1.8.0-openjdk-demo.i686 : OpenJDK Demos 8
java-1.8.0-openjdk-demo.x86_64 : OpenJDK Demos 8
java-1.8.0-openjdk-devel.i686 : OpenJDK Development Environment 8
java-1.8.0-openjdk-devel.x86_64 : OpenJDK Development Environment 8
java-1.8.0-openjdk-headless.i686 : OpenJDK Headless Runtime Environment 8
java-1.8.0-openjdk-headless.x86_64 : OpenJDK Headless Runtime Environment 8
java-1.8.0-openjdk-javadoc.noarch : OpenJDK 8 API documentation
java-1.8.0-openjdk-javadoc-zip.noarch : OpenJDK 8 API documentation compressed
java-1.8.0-openjdk-src.i686 : OpenJDK Source Bundle 8
java-1.8.0-openjdk-src.x86_64 : OpenJDK Source Bundle 8
...
```
```bash
# 安装openjdk
[root@VM-0-13-centos zookeeper]#yum install java-1.8.0-openjdk -y
```
```bash
Installed:
...
  java-1.8.0-openjdk.x86_64 1:1.8.0.275.b01-0.el7_9
...                                        

Complete!
```
```bash
# 验证openjdk安装
[root@VM-0-13-centos ~]# java -version
```
```bash
openjdk version "1.8.0_275"
OpenJDK Runtime Environment (build 1.8.0_275-b01)
OpenJDK 64-Bit Server VM (build 25.275-b01, mixed mode)
```
```bash
 # 下载zookeeper软件包
[root@VM-0-13-centos ~]# wget https://downloads.apache.org/zookeeper/zookeeper-3.6.2/apache-zookeeper-3.6.2-bin.tar.gz
```
```bash
# 解压zookeeper
[root@VM-0-13-centos ~]# tar -zxvf apache-zookeeper-3.6.2-bin.tar.gz
```
```bash
# 将zookeeper移动至 /usr/local/bin 统一管理
[root@VM-0-13-centos ~]# mv apache-zookeeper-3.6.2-bin /usr/local/bin/zookeeper 
```
```bash
# 切换目录至 /usr/local/bin
[root@VM-0-13-centos bin]# cd /usr/local/bin/
```
```bash
# 备份 zookeeper 初始配置文件
[root@VM-0-13-centos bin]# cp zookeeper/conf/zoo_sample.cfg zookeeper/conf/zoo_sample.cfg.bak
```
```bash
# 创建 zookeeper 配置文件
[root@VM-0-13-centos bin]# mv zookeeper/conf/zoo_sample.cfg zookeeper/conf/zoo.cfg
```
```bash
# 新建 zookeeper 数据目录
[root@VM-0-13-centos bin]# mkdir zookeeper/data
```
```bash
# 修改 zookeeper 配置中的 dataDir 至 /usr/local/bin/zookeeper/data
[root@VM-0-13-centos bin]# vim /zookeeper/conf/zoo.cfg
```
```bash

#tickTime: zookeeper中使用的基本时间单位, 毫秒值.
# The number of milliseconds of each tick
tickTime=2000

# ZooKeeper 集群模式下包含多个zk进程，其中一个进程为 leader ，余下的进程为 follower。
# 当 follower 最初与 leader 建立连接时，它们之间会传输相当多的数据，尤其是 follower 的数据落后 leader 很多。
# initLimit 参数配置初始化连接时, follower 和 leader 之间的最长心跳时间。
# The number of ticks that the initial 
# synchronization phase can take
initLimit=10

# 配置 follower 和 leader 之间发送消息，请求和应答的最大时间长度。
# The number of ticks that can pass between 
# sending a request and getting an acknowledgement
syncLimit=5

# zookeeper 数据目录
# the directory where the snapshot is stored.
# do not use /tmp for storage, /tmp here is just 
# example sakes.
dataDir=/usr/local/bin/zookeeper/data

# zookeeper 服务默认使用的端口号
# the port at which the clients will connect
clientPort=2181
# the maximum number of client connections.
# increase this if you need to handle more clients
#maxClientCnxns=60
#
# Be sure to read the maintenance section of the 
# administrator guide before turning on autopurge.
#
# http://zookeeper.apache.org/doc/current/zookeeperAdmin.html#sc_maintenance
#
# The number of snapshots to retain in dataDir
#autopurge.snapRetainCount=3
# Purge task interval in hours
# Set to "0" to disable auto purge feature
#autopurge.purgeInterval=1

## Metrics Providers
#
# https://prometheus.io Metrics Exporter
#metricsProvider.className=org.apache.zookeeper.metrics.prometheus.PrometheusMetricsProvider
#metricsProvider.httpPort=7000
#metricsProvider.exportJvmInfo=true
```
```bash
# 启动 zookeeper
[root@VM-0-13-centos bin]# zookeeper/bin/zkServer.sh start
# zookeeper/bin/zkServer.sh start-foreground 前台启动，用于查看实时 log
```
```bash
/usr/bin/java
ZooKeeper JMX enabled by default
Using config: /usr/local/bin/zookeeper/bin/../conf/zoo.cfg
Starting zookeeper ... STARTED
```
```bash

```
```bash
# 查看 zookeeper 运行状态
[root@VM-0-13-centos bin]# zookeeper/bin/zkServer.sh status
```
```bash
/usr/bin/java
ZooKeeper JMX enabled by default
Using config: /usr/local/bin/zookeeper/bin/../conf/zoo.cfg
Client port found: 2181. Client address: localhost. Client SSL: false.
Mode: standalone
```
