# Mysql安装

## 一、Mysql压缩包下载

官网下载地址： https://dev.mysql.com/downloads/mysql/

## 二、Mysql安装

### 2.1 解压压缩包到合适目录下

![1652024096056](Mysql%E5%AE%89%E8%A3%85.assets/1652024096056.png)

### 2.2 在安装目录下创建配置文件my.ini，只需要配置basedir即可，根据安装目录配置

```properties
[mysql]
# 设置mysql客户端默认字符集
default-character-set=utf8
 
[mysqld]
# 设置3306端口
port = 3306
# 设置mysql的安装目录
basedir=E:\\fxf\\program-util\\mysql-8.0.29-winx64
# 设置 mysql数据库的数据的存放目录，MySQL 8+ 不需要以下配置，系统自己生成即可，否则有可能报错
# datadir=E:\\fxf\\program-util\\mysql-8.0.29-winx64\\data
# 允许最大连接数
max_connections=20
# 服务端使用的字符集默认为8比特编码的latin1字符集
character-set-server=utf8
# 创建新表时将使用的默认存储引擎
default-storage-engine=INNODB
```

### 2.3 配置环境变量

![1652024179128](Mysql%E5%AE%89%E8%A3%85.assets/1652024179128.png)



### 2.4 以管理员身份打开cmd，初始化Mysql，Mysql8.0后自动生成data文件夹

```shell
mysqld  --initialize-insecure （建议使用，不设置root密码）
 
//生成的密码在实际连接的时候可能会不小心输入错误或忘记，导致无法连接Mysql
mysqld  --initialize --console（不建议使用，在控制台生成一个随机的root密码）
```

![1652024214812](Mysql%E5%AE%89%E8%A3%85.assets/1652024214812.png)

### 2.5 安装Mysql

```she
//安装mysql服务
mysqld install mysql
 
//卸载mysql服务
sc delete mysql(需要管理员权限)
 
//移除mysql服务（需要停止mysql）
mysqld -remove
```

执行命令成功后一般会出现Service successfully installed

 ![1652024258169](Mysql%E5%AE%89%E8%A3%85.assets/1652024258169.png)

### 2.6  开启Mysql服务 

```she
net start mysql
```

### 2.7 登录Mysql

```shell
mysql -uroot -p
```

![1652024284062](Mysql%E5%AE%89%E8%A3%85.assets/1652024284062.png)

### 2.8 设置（修改）密码

```shell
//切换数据库
use mysql;
 
//修改root用户的密码为123456，根据需要自己设置
alter user 'root'@localhost identified by '123456';
 
//刷新权限,一般修改密码或授权用户的时候需要使用
flush privileges;
 
 //退出mysql,两个都可以正常退出数据库
 quit
 exit
```

 **注意**：Mysql8.0之后修改密码的方式无法使用password函数 ! 