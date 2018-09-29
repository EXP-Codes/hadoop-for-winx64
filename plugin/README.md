此插件是配套给Eclipse用的，官方下载地址为：[https://github.com/winghc/hadoop2x-eclipse-plugin](https://github.com/winghc/hadoop2x-eclipse-plugin)

使用方法参考：[《Hadoop-Eclipse-Plugin 安装》](https://blog.csdn.net/ichimaru_gin_/article/details/78997576)

注意：这个插件前身命为`hadoop-eclipse-kepler-plugin-x.x.x.jar`，现已更名为 `hadoop-eclipse-plugin-x.x.x.jar`

------

把插件放到Eclipse的plugins文件夹下就可以了，

重启eclipse，可以通过 Window -> Show View -> Other 找到 Map/Reduce

需要在 Window -> Perference -> Hadoop Map/Reduce 配置Hadoop 的安装路径 

------

插件连接HDFS的配置方法参见 
[《使用Eclipse插件连接配置Mapreduce说明与教程(hadoop-eclipse-plugin 2.6)》](https://blog.csdn.net/huitoukest/article/details/50922256)
[《基于 Eclipse 的 MapReduce 开发环境搭建》](https://www.cnblogs.com/vincentzh/p/6055850.html)


配套pom坐标:
```xml
<dependency>
  <groupId>org.apache.hadoop</groupId>
  <artifactId>hadoop-common</artifactId>
  <version>3.0.0</version>
  <type>pom</type>
</dependency>

<dependency>
  <groupId>org.apache.hadoop</groupId>
  <artifactId>hadoop-mapreduce-client-core</artifactId>
  <version>3.0.0</version>
  <type>pom</type>
</dependency>
```
