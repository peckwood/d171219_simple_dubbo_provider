### Features

1. Simple Dubbo provider containing the interfaces
2. Simple Dubbo consumer

### Steps

1. set up ZooKeeper, ZooKeeper is the registry part of Dubbo
   1. 参照[网上教程](http://blog.csdn.net/u013142781/article/details/50395650), 本地PDF为1_Zookeeper注册中心的搭建.pdf
   2. download ZooKeeper
   3. create data directory
      1. in the guide, it is set to `ZooKeeperDir/dataTemp`
   4. create configuration file `ZooKeeperDir/conf/zoo.cfg` by copy/paste `zoo_sample.cfg`
   5. set up configuration
      1. Set dataDir, for example `D:\\programs\\zookeeper-3.4.11\\dataTemp`
      2. note the client port is set to `2181` by default
   6. start ZooKeeper
      1. start `D:\programs\zookeeper-3.4.11\bin\zkServer.cmd` in cmd
2. set up Dubbo Admin
   1. 参照[网上教程](http://blog.csdn.net/u013142781/article/details/50396621), 本地PDF为2_dubbo-admin管理平台搭建.pdf
   2. download Dubbo(souce code) from its official website
   3. use maven to package dubbo-admin to a war `mvn package -Dmaven.skip.test=true`
   4. didn't change tomcat's port to 8090 as the guide said
   5. deploy it on tomcat
   6. start tomcat
   7. tomcat will extract the war file, and you will see `dubbo.properties` file inside `WEB-INF`, which contains 
      1. default registry address `zookeeper://127.0.0.1:2181`
      2. login user and password `root/root`
3. create Dubbo Provider and Consumer
   1. 参照本地3_Dubbo分布式服务框架入门（附工程）.md或[网上教程](https://www.kancloud.cn/digest/javaframe/125576)


### Start order

1. ZooKeeper
2. Dubbo Admin (by starting the tomcat whose webapp folder contains its war)
3. provider
4. consumer