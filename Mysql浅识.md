# 浅识Mysql

## 一.架构

客户端-服务器架构

## 二.启动Mysql服务器程序

Unix系统

```shell
#启动
mysql.server start
#停止
mysql.server stop
```

Windows系统

```cmd
#第一种方式：双击mysqld
#第二种方式：以服务的方式启动
#1.注册Windows服务
mysqld路径 install mysql
#2.启动mysql
net mysql start
#3.停止mysql
net mysql stop
```

## 三.启动Mysql客户端程序

```shell
#启动
mysql -h主机名 -u用户名 -p密码
#退出
quit
```

注意事项：

1. 最好不要在一行命令中输入密码：mysql -uroot -p123456
2. 如果非要在一行命令中输入密码，-p与密码值中间不能有空格，其他参数可以有
3. 各个参数没有硬性规定顺序
4. 如果客户端和服务器是同一台机器，可省略-h参数
5. 如果没有输入-u参数，默认使用当前登录操作系统的用户名