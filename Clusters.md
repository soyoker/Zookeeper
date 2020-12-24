### Zookeeper 集群安装部署

```bash
# 从yum仓库查找openjdk
[root@VM-0-13-centos zookeeper]#yum search java | grep jdk
```

```bash
# 安装openjdk
[root@VM-0-13-centos zookeeper]#yum install java-1.8.0-openjdk -y
```

```bash
# 验证openjdk安装
[root@VM-0-13-centos ~]# java -version
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

# 集群模式下所有主机使用相同配置
# 2888原子广播端口，3888选举端口
server.1=Server1IP:2888:3888
server.2=Server2IP:2888:3888
server.3=Server3IP:2888:3888
```

```bash
# 设置 Server1 的服务器 ID
[root@VM-0-13-centos zookeeper]# echo 1 > data/myid
```

```bash
# 设置 Server2 的服务器 ID
[root@VM-0-14-centos zookeeper]# echo 2 > data/myid
```

```bash
# 设置 Server3 的服务器 ID
[root@VM-0-15-centos zookeeper]# echo 3 > data/myid
```

```bash
# 分别启动三台服务器上的 zookeeper
[root@VM-0-13-centos bin]# zookeeper/bin/zkServer.sh start
# zookeeper/bin/zkServer.sh start-foreground 前台启动，用于查看实时 log

/usr/bin/java
ZooKeeper JMX enabled by default
Using config: /usr/local/bin/zookeeper/bin/../conf/zoo.cfg
Starting zookeeper ... STARTED
```
