# hadoop-for-winx64
由于hadoop部署在win上比unix麻烦得多，特意部署好这个版本，下载后稍微配置环境变量就可运行（基于Hadoop3.0.3版本）

------

注：

若检出/提交时提示`warning: LF will be replaced by CRLF`，则执行以下指令关闭自动替换：
git config --global core.autocrlf false

若检出/提交时报错`Filename too long`，则执行以下指令允许长文件名：
git config --global core.longpaths true

------


此Hadoop是参考 [《hadoop2.7.2 window win7 基础环境搭建》](https://blog.csdn.net/fly_leopard/article/details/51250443)进行搭建的，
搭建的是单机版。

由于windows下的hadopp缺少`hadoop.dll`和`winutils.exe`导致无法运行，
且这两个版本还要找到匹配版本号、编译平台的Hadoop才能用，因此这里就一次性先做好，放到一起，省得麻烦

------

使用方法：

1. clone项目到本地，例如检出到 `D:\workspace\Github\hadoop-for-winx64`
2. 确认本地JDK环境（建议使用1.8）
3. 修改系统环境变量： 
<br/>  增加环境变量 HADOOP_HOME，设置值为检出目录 `D:\workspace\Github\hadoop-for-winx64`
<br/>  把 %HADOOP_HOME%/bin; 添加到 Path 变量
<br/>  由于 HADOOP_HOME 不能识别环境变量路径的空格，而默认情况下 JAVA_HOME 路径都是在 C:\Program Files\Java\jdk1.8.0_77（只是举例）
<br/>  Program Files 是有空格的，因此需要修改 JAVA_HOME ，用特殊字符模糊匹配： C:\Progra~1\Java\jdk1.8.0_77
4. 默认已配置好hadoop单机版的配置，若需要修改可切到 `./etc/hadoop` 目录修改相关的4个配置文件：`core-site.xml`、`hdfs-site.xml`、`mapred-site.xml`、`yarn-site.xml`，
其实主要修改`hdfs-site.xml`就可以了，指定一下 namenode 和 datanode 的目录位置（注意为了兼容unix系统，路径不需要配置磁盘号，默认磁盘好就是hadoop所在的磁盘，但是必须配置绝对路径）。
5. 切到 `./bin` 目录 , 在dos下执行 `hadoop version`  若打印版本号则安装成功
6. 切到 `./bin` 目录 , 在dos下执行 `hdfs namenode -format`  对HDFS系统初始化
7. 以后需要启动时，切到`./sbin` 目录 , 在dos下执行 `start-dfs` 即可
8. 打开浏览器 `http://127.0.0.1:9870`  （端口号是在启动日志中打印的， 并不是`core-site.xml`所配置的9000端口）可进入管理页
9. 注意：hadoop启动时会启动了一堆守护进程和服务端口，如果不想下次无法启动，就不能简单关掉dos框就认为服务终止了。
<br/>  正确的做法是切到`./sbin` 目录 , 在dos下执行 `stop-all` 命令。