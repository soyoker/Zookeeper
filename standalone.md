### Zookeeper 单节点安装部署

<!DOCTYPE html>
<!-- saved from url=(0016)http://localhost -->
<html>
  <head>
    <meta charset="utf-8"/>
    <meta http-equiv="X-UA-Compatible" content="IE=edge"/>
    <title>standalone</title>
    <style>
        body{
            margin: 0;
        }
        #content-info{
            width: auto;
            margin: 0 auto;
            text-align: center;
        }
        #author-info{
            white-space: nowrap;
            text-overflow: ellipsis;
            overflow: hidden;
        }
        #title{
            text-overflow: ellipsis;
            white-space: nowrap;
            overflow: hidden;
            padding-top: 10px;
            margin-bottom: 2px;
            font-size: 34px;
            color: #505050;
        }
        .text{
            white-space:nowrap;
            text-overflow: ellipsis;
            display: inline-block;
            margin-right: 20px;
            margin-bottom: 2px;
            font-size: 20px;
            color: #8c8c8c;
        }
        #navBar{
            width: auto;
            height: auto;
            position: fixed;
            right:0;
            bottom: 0;
            background-color: #f0f3f4;
            overflow-y: auto;
            text-align: center;
        }
        #svg-container{
            width: 100%;
            overflow-x: scroll;
            min-width: 0px;
            margin: 0 10px;
            overflow: visible;
            position: relative;
        }
        #nav-thumbs{
            overflow-y: scroll;
            padding: 0 5px;
        }
        .nav-thumb{
            position: relative;
            margin: 10px auto;
        }
        .nav-thumb >p{
            text-align: center;
            font-size: 12px;
            margin: 4px 0 0 0;
        }
        .nav-thumb >div{
            position: relative;
            display: inline-block;
            border: 1px solid #c6cfd5;
        }
        .nav-thumb img{
            display: block;
        }
        #main-content{
            bottom: 0;
            left: 0;
            right: 0;
            background-color: #fff;
            display: flex;
            height: auto;
            flex-flow: row wrap;
            text-align:center;
        }
        #svg-container >svg{
            overflow: visible;
            display: block;
            margin:5px auto;
            margin-bottom: 5px;
        }
        #copyright{
            bottom: 0;
            left: 50%;
            margin: 5px auto;
            font-size: 16px;
            color: #515151;
        }
        #copyright >a{
            text-decoration: none;
            color: #77C;
        }
        .number{
            position: absolute;
            top:0;
            left:0;
            border-top:22px solid #08a1ef;
            border-right: 22px solid transparent;
        }
        .pagenum{
            font-size: 12px;
            color: #fff;
            position: absolute;
            top: -23px;
            left: 2px;
        }
            #navBar::-webkit-scrollbar{
            width: 8px;
            background-color: #f5f5f5;
        }
            #navBar::-webkit-scrollbar-track{
            -webkit-box-shadow: inset 0 0 4px rgba(0,0,0,.3);
            border-radius: 8px;
            background-color: #fff;
        }
            #navBar::-webkit-scrollbar-thumb{
            border-radius: 8px;
            -webkit-box-shadow: inset 0 0 4px rgba(0,0,0,.3);
            background-color: #6b6b70;
        }
        #navBar::-webkit-scrollbar-thumb:hover{
            background-color: #4a4a4f;
        }
</style>
  </head>
  <body>
    <div id="main-area">
      <div id="main-content">
        <div id="svg-container"><svg preserveAspectRadio="xMinYMin meet" xmlns:ev="http://www.w3.org/2001/xml-events" width="971" id="page0" ed:hSpacing="30" height="420" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns="http://www.w3.org/2000/svg" ed:name="单机" viewBox="0 0 971 420" xmlns:ed="https://www.edrawsoft.cn/xml/2017/SVGExtensions/" ed:vSpacing="30">
    <style type="text/css"><![CDATA[
g[ed\:togtopicid],g[ed\:hyperlink],g[ed\:comment],g[ed\:note] {cursor:pointer;}
g[id] {-moz-user-select: none;-ms-user-select: none;user-select: none;}
svg text::selection,svg tspan::selection{background-color: #4285f4;color: #ffffff;fill: #ffffff;}
.st15 {fill:#000000;font-family:Consolas,Courier New,monospace}
.st14 {fill:#008000;font-family:Consolas,Courier New,monospace}
.st13 {fill:#303030;font-family:微软雅黑;font-size:10pt}
.st12 {fill:#303030;font-family:微软雅黑;font-size:14pt;font-weight:bold}
.st11 {fill:#ffffff;font-family:微软雅黑;font-size:18pt;font-weight:bold}
]]></style>
    <defs/>
    <rect width="971" fill="#ffffff" height="420" x="0" y="0"/>
    <path stroke-linejoin="round" ed:tosuperid="102" transform="matrix(1,0,0,1,197.84,163.38)" stroke-width="3" fill="none" id="103" stroke-linecap="round" stroke="#454545" d="M-23.8,38.9C-10.4,-7.9,27.6,-70.4,79.3,-70.4" ed:parentid="101"/>
    <path stroke-linejoin="round" ed:tosuperid="104" transform="matrix(1,0,0,1,197.84,246.88)" stroke-width="3" fill="none" id="105" stroke-linecap="round" stroke="#454545" d="M13.6,-0.4C27.5,6.6,50.5,13.1,79.3,13.1" ed:parentid="101"/>
    <path stroke-linejoin="round" ed:tosuperid="106" transform="matrix(1,0,0,1,197.84,304.13)" stroke-width="3" fill="none" id="107" stroke-linecap="round" stroke="#454545" d="M-23.8,-38.9C-10.4,7.9,27.6,70.4,79.3,70.4" ed:parentid="101"/>
    <path stroke-linejoin="round" ed:tosuperid="108" transform="matrix(1,0,0,1,414.72,76.75)" fill="none" id="109" stroke-linecap="round" stroke="#454545" d="M-21.6,16.3L-10.6,16.3C5.7,-16.3,5.7,-16.3,21.6,-16.3" ed:parentid="102"/>
    <path stroke-linejoin="round" ed:tosuperid="110" transform="matrix(1,0,0,1,414.72,109.25)" fill="none" id="111" stroke-linecap="round" stroke="#454545" d="M-10.6,-16.3C5.7,16.3,5.7,16.3,21.6,16.3" ed:parentid="102"/>
    <path stroke-linejoin="round" ed:tosuperid="114" transform="matrix(1,0,0,1,414.72,230)" fill="none" id="115" stroke-linecap="round" stroke="#454545" d="M-21.6,30L-10.6,30C5.7,-30,5.7,-30,21.6,-30" ed:parentid="104"/>
    <path stroke-linejoin="round" ed:tosuperid="116" transform="matrix(1,0,0,1,414.72,290)" fill="none" id="117" stroke-linecap="round" stroke="#454545" d="M-10.6,-30C5.7,30,5.7,30,21.6,30" ed:parentid="104"/>
    <g ed:layout="map" transform="matrix(1,0,0,1,23,202.25)" id="101" ed:topictype="mainidea" ed:width="191.12" ed:height="63">
        <path stroke-linejoin="round" fill="#00af54" stroke-width="3" stroke="#00af54" d="M31.5,0L159.6,0C177,0,191.1,14.1,191.1,31.5C191.1,48.9,177,63,159.6,63L31.5,63C14.1,63,0,48.9,0,31.5C0,14.1,14.1,0,31.5,0z"/>
        <text class="st11">
            <tspan style="white-space:pre" x="26" y="39.5">standalone</tspan>
        </text>
    </g>
    <g ed:layout="rightmap" transform="matrix(1,0,0,1,277.12,71.5)" id="102" ed:width="116" ed:height="43" ed:parentid="101">
        <path stroke-linejoin="round" fill="#ffffff" stroke-width="2" stroke="#454545" d="M4,0L112,0C114.7,0,116,1.3,116,4L116,39C116,41.7,114.7,43,112,43L4,43C1.3,43,0,41.7,0,39L0,4C0,1.3,1.3,0,4,0z"/>
        <text class="st12">
            <tspan style="white-space:pre" x="18" y="27">环境准备</tspan>
        </text>
    </g>
    <g ed:layout="rightmap" transform="matrix(1,0,0,1,277.12,238.5)" id="104" ed:width="116" ed:height="43" ed:parentid="101">
        <path stroke-linejoin="round" fill="#ffffff" stroke-width="2" stroke="#454545" d="M4,0L112,0C114.7,0,116,1.3,116,4L116,39C116,41.7,114.7,43,112,43L4,43C1.3,43,0,41.7,0,39L0,4C0,1.3,1.3,0,4,0z"/>
        <text class="st12">
            <tspan style="white-space:pre" x="18" y="27">安装准备</tspan>
        </text>
    </g>
    <g ed:layout="rightmap" transform="matrix(1,0,0,1,277.12,353)" id="106" ed:width="116" ed:height="43" ed:parentid="101">
        <path stroke-linejoin="round" fill="#ffffff" stroke-width="2" stroke="#454545" d="M4,0L112,0C114.7,0,116,1.3,116,4L116,39C116,41.7,114.7,43,112,43L4,43C1.3,43,0,41.7,0,39L0,4C0,1.3,1.3,0,4,0z"/>
        <text class="st12">
            <tspan style="white-space:pre" x="18" y="27">程序启动</tspan>
        </text>
    </g>
    <g ed:layout="rightmap" transform="matrix(1,0,0,1,436.32,19)" id="108" ed:width="282" ed:height="41.5" ed:parentid="102">
        <path fill="#ffffff" d="M0,0L282,0L282,41.5L0,41.5L0,0z"/>
        <path stroke-linejoin="round" fill="none" stroke="#454545" d="M0,41.5L282,41.5"/>
        <text class="st13">
            <tspan style="white-space:pre" x="8" y="16.1">openjdk 环境</tspan>
            <tspan class="st14" style="white-space:pre" x="8" y="33.1">yum install java-1.8.0-openjdk -y</tspan>
        </text>
    </g>
    <g ed:layout="rightmap" transform="matrix(1,0,0,1,436.32,67)" id="110" ed:width="514" ed:height="58.5" ed:parentid="102">
        <path fill="#ffffff" d="M0,0L514,0L514,58.5L0,58.5L0,0z"/>
        <path stroke-linejoin="round" fill="none" stroke="#454545" d="M0,58.5L514,58.5"/>
        <text class="st13">
            <tspan style="white-space:pre" x="8" y="16.1">zookeeper 下载</tspan>
            <tspan class="st14" style="white-space:pre" x="8" y="33.1">wget https://downloads.apache.org/zookeeper/zookeeper-3.6.2/</tspan>
            <tspan class="st14" style="white-space:pre" x="8" y="50.1">apache-zookeeper-3.6.2-bin.tar.gz</tspan>
        </text>
    </g>
    <g ed:layout="rightmap" transform="matrix(1,0,0,1,436.32,158.5)" id="114" ed:width="458" ed:height="41.5" ed:parentid="104">
        <path fill="#ffffff" d="M0,0L458,0L458,41.5L0,41.5L0,0z"/>
        <path stroke-linejoin="round" fill="none" stroke="#454545" d="M0,41.5L458,41.5"/>
        <text class="st13">
            <tspan style="white-space:pre" x="8" y="16.1">创建 zoo.cfg 配置</tspan>
            <tspan class="st14" style="white-space:pre" x="8" y="33.1">mv zookeeper/conf/zoo_sample.cfg zookeeper/conf/zoo.cfg</tspan>
        </text>
    </g>
    <g ed:layout="rightmap" transform="matrix(1,0,0,1,436.32,206.5)" id="116" ed:width="314" ed:height="113.5" ed:parentid="104">
        <path fill="#ffffff" d="M0,0L314,0L314,113.5L0,113.5L0,0z"/>
        <path stroke-linejoin="round" fill="none" stroke="#454545" d="M0,113.5L314,113.5"/>
        <text class="st13">
            <tspan style="white-space:pre" x="8" y="16.1">修改 dataDir 数据目录</tspan>
            <tspan class="st14" style="white-space:pre" x="8" y="33.1">mkdir zookeeper/data</tspan>
            <tspan class="st14" style="white-space:pre" x="8" y="50.1">vim /zookeeper/conf/zoo.cfg</tspan>
            <tspan style="white-space:pre" x="8" y="69.1">...</tspan>
            <tspan class="st15" style="white-space:pre" x="8" y="86.1">dataDir=/usr/local/bin/zookeeper/data</tspan>
            <tspan style="white-space:pre" x="8" y="105.1">...</tspan>
        </text>
    </g>
</svg>
</div>
      </div>
    </div>
  </body>
</html>


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
