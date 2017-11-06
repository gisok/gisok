# 从最简单的Mini开始配置自己的centos
---

- [X] postgresql 9.5
- [x] apache
- [x] JDK 9.0.1
- [x] tomcat
- [x] GeoServer
- [x] postgis


## 安装最小CentOS

    root password: atx165
    user: gisok pw: atx165

## 网络连接

172.30.17.129

[网络教程1](http://simonhu.blog.51cto.com/196416/1588971)
[网络教程2](http://blog.csdn.net/sfeng95/article/details/62239539)

## 安装postgresql

[最好的安装教程是官方教程](http://www.postgresonline.com/journal/archives/362-An-almost-idiots-guide-to-install-PostgreSQL-9.5,-PostGIS-2.2-and-pgRouting-2.1.0-with-Yum.html)
[网络教程1](http://blog.csdn.net/shanzhizi/article/details/46484481)
[网络教程1](http://blog.csdn.net/lk10207160511/article/details/50359549)

1. 切换用户
    su

1. 安装PostgreSQL的
    
    rpm install http://yum.postgresql.org/9.5/redhat/rhel-7-x86_64/pgdg-redhat95-9.5-2.noarch.rpm -y

1. 验证是否安装成功
```
    rpm -aq| grep postgres      
```
1. 安装服务和扩展
    yum install postgresql95-server postgresql95-contrib -y

1. 切换
    su postgres

1. 初始化数据库
    initdb

1.  启动数据库服务

* 另一个思路

yum install http://yum.postgresql.org/9.4/redhat/rhel-6-x86_64/pgdg-redhat94-9.4-1.noarch.rpm
yum install postgresql94-server postgresql94-contrib
service postgresql-9.4 initdb
chkconfig postgresql-9.4 on

## 安装PostGis

[教程](http://www.cnblogs.com/flywuya/p/5460997.html)

    - yum install proj.x86_64
    - yum install geos.x86_64
    - yum install libxml2.x86_64
    - yum install json-c.x86_64
    - rpm -ivh http://dl.fedoraproject.org/pub/epel/7/x86_64/e/epel-release-7-5.noarch.rpm   ??

GDAL 装不上。yum 后边 使用 --skip-broken 能执行，但是装不上23个依赖项
ogr
postgis
pgrouting

[编译安装GDAL教程](https://zhuanlan.zhihu.com/p/29417899)

GCC 版本 5.5 6.4 7.2 到底使用哪一个？

从[GDAL管网](http://trac.osgeo.org/gdal/wiki/DownloadSource)下载 gdal 2.2.2 [最新版的代码](http://download.osgeo.org/gdal/2.2.2/gdal-2.2.2.tar.gz)


## 安装Apache

1. 查看httpd包是否可用

    yum list | grep httpd

1. 安装Apache

    yum install httpd

1. 配置ServerName
    
    vi /etc/httpd/conf/httpd.conf   
    如果没有域名，则：ServerName localhost:80

1. 启动
    
    httpd

1. 停止
    
    httpd -k stop

1. 设置开机自动启动：
    
    chkconfig httpd on

1. 安装目录介绍
    
    Apache默认将网站的根目录指向/var/www/html 目录
    默认的主配置文件是/etc/httpd/conf/httpd.conf
    配置存储在的/etc/httpd/conf.d/目录

## 安装Apache二

* 安装 httpd.
    [root@linuxprobe ~]# yum -y install httpd
* 删除默认欢迎页面
    [root@linuxprobe ~]# rm -f /etc/httpd/conf.d/welcome.conf
* 配置httpd，将服务器名称替换为您自己的环境
    [root@linuxprobe ~]# vi /etc/httpd/conf/httpd.conf
    line 86: 改变管理员的邮箱地址
    ServerAdmin root@linuxprobe.org
    line 95: 改变域名信息
    ServerName www.linuxprobe.org:80
    line 151: none变成All
    AllowOverride All
    line 164: 添加只能使用目录名称访问的文件名
    DirectoryIndex index.html index.cgi index.php
    add follows to the end
    server's response header（安全性）
    ServerTokens Prod
    keepalive is ON
    KeepAlive On

* [root@linuxprobe ~]# systemctl start httpd
* [root@linuxprobe ~]# systemctl enable httpd

* 如果Firewalld正在运行，请允许HTTP服务。，HTTP使用80 / TCP
    [root@linuxprobe ~]# firewall-cmd --add-service=http --permanent
    success
    [root@linuxprobe ~]# firewall-cmd --reload
    success
* 创建一个HTML测试页，并使用Web浏览器从客户端PC访问它。如果显示以下页面，是正确的
    
    [root@linuxprobe ~]# vi /var/www/html/index.html
 
## 命令行下载网络资源

1. 安装ftp客户端
    sudo yum install ftp -y

2. wget 
    
    yum install wget -y

3.  unzip

    yum install unzip -y

## windows 和 centos虚拟机传输文件

1. ssh

2. 安装 putty 

    [A](http://www.linuxidc.com/Linux/2016-08/133991.htm)
    [B](http://junight.blog.51cto.com/10828785/1708146/)

3. pscp 传输文件到centos

```
    pscp.exe d:/sharedir/tt.txt gisok@172.30.17.129:/home/gisok
```
注意 不要拷贝到没有权限的目录

4. [在Linux虚拟机和物理机之间共享文件夹](https://jingyan.baidu.com/article/fb48e8be3a8e7e6e622e14e3.html)

## 安装 JDK

[教程1](http://blog.csdn.net/lk10207160511/article/details/50359565)
[教程2](http://blog.csdn.net/czmchen/article/details/41047187)
[教程3](http://blog.csdn.net/evan_chen_1/article/details/55097252)

* 安装
    rpm -ivh jdk.....rpm

* 验证安装
执行以下操作，查看信息是否正常：
    [root@localhost ~]# java
    [root@localhost ~]# javac
    [root@localhost ~]# java -version

* 修改系统环境变量文件

    vi + /etc/profile

向文件里面追加以下内容：

    JAVA_HOME=/usr/java/jdk1.8.0_25
    JRE_HOME=/usr/java/jdk1.8.0_25/jre
    PATH=$PATH:$JAVA_HOME/bin:$JRE_HOME/bin
    CLASSPATH=.:$JAVA_HOME/lib/dt.jar:$JAVA_HOME/lib/tools.jar:$JRE_HOME/lib
    export JAVA_HOME JRE_HOME PATH CLASSPATH


## 安装 Tomcat

###  Tomcat 支持的Java 版本和兼容性总结

Apache - java - tomcat 版本配合
最新最全的Tomcat 支持的Java版本对照，即兼容性一览表：

| Servlet Spec  |  JSP Spec  |  EL Spec  |   WebSocket Spec | Apache Tomcat  version |  Actual release revision  |   Support Java Versions |
| --- | --- | --- | --- | --- | --- | --- |
| 4.0 |  TBD (2.4?) |TBD (3.1?) | TBD (1.2?) | 9.0.x | None | 8 and later|
 | 3.1 |  2.3  |  3.0   |  1.1  |  8.0.x |  8.0.15 | 7 and later|
 | 3.0 |   2.2 |   2.2  |  1.1  |  7.0.x | 7.0.57 |6 and later (WebSocket 1.1 | requires 7 or later)|
 | 2.5  |  2.1 |   2.1  |   N/A  |   6.0.x  | 6.0.43 | 5 and later|
 |2.4   |  2.0 |  N/A   |  N/A  |   5.5.x (archived)  |  5.5.36 (archived)   | 1.4 and later |
 |2.3   | 1.2  |  N/A   |  N/A |  4.1.x (archived) | 4.1.40 (archived) | 1.3 and later |
 |2.2   |  1.1 |   N/A   |  N/A | 3.3.x (archived) | 3.3.2 (archived)  |  1.1 and later |

###  下载压缩包

[下载页面](https://tomcat.apache.org/download-80.cgi)

下载8.5的tar.gz,[文件链接](http://mirrors.tuna.tsinghua.edu.cn/apache/tomcat/tomcat-8/v8.5.23/bin/apache-tomcat-8.5.23.tar.gz)

    wget http://mirrors.tuna.tsinghua.edu.cn/apache/tomcat/tomcat-8/v8.5.23/bin/apache-tomcat-8.5.23.tar.gz

### 安装教程

[安装教程1](http://blog.csdn.net/uq_jin/article/details/51356799)
[安装教程2](http://blog.csdn.net/czmchen/article/details/41047455)
[安装教程3](http://www.cnblogs.com/hapday/p/5616830.html) 这个最好，没有 配置成系统服务

### 安装tomcat 

    [root@localhost ~]# cp apache-tomcat...tar.gz /usr/local
    [root@localhost ~]# cd /usr/local  
    [root@localhost ~]# tar -zxv -f apache-tomcat-8.0.14.tar.gz // 解压压缩包  
    [root@localhost ~]# rm -rf apache-tomcat-8.0.14.tar.gz // 删除压缩包  
    [root@localhost ~]# mv apache-tomcat-8.0.14.tar.gz  

### 将8080端口添加到防火墙例外并重启

firewall-cmd --zone=public --add-port=8080/tcp --permanent
firewall-cmd --reload

### 启动Tomcat

    cd /opt/soft/apache-tomcat-8.0.33/bin/
    ./startup.sh

### 停止Tomcat

    [root@localhost ~]# /usr/local/tomcat/bin/shutdown.sh //停止tomcat</span>

## 安装 Geoserver

[网络教程1](http://www.cnblogs.com/think8848/p/5992736.html)
[网络教程2](http://tessykandy.iteye.com/blog/1462610)

[下载页面](http://geoserver.org/release/2.12.0/)

[文件地址](http://sourceforge.net/projects/geoserver/files/GeoServer/2.12.0/geoserver-2.12.0-war.zip)

geoserver 2.12  需要Java 8,不是 9

[扩展GeoServer数据源](http://www.cnblogs.com/sillyemperor/p/3862179.html)


扩展方式:
    
    下载的文件拷贝到..\webapps\geoserver\WEB-INF\lib目录下


## 开机自动启动

- [x] apache
- [x] postgresql
- [ ] tomcat

