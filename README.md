# mysql
Docker


#创建镜像：
#sudo docker build mysql:latest .

#使用镜像：
#sudo docker run -d -P mysql           -P 自动映射容器的22和3306端口

#默认容器内，mysql提供root账号和admin账号，root无密码，只允许本地访问;admin用户有远程访问权限，使用docker logs 查看admin密码：
#sudo docker logs eef


#############可以在启动容器时指定admin账号的用户名和密码##########################
#sudo  docker run -d -P -e MYSQL_PASS="mypass"   mysql
#######################################


#挂载本地主机目录到容器：
#docker run -d -P -v /opt/mysqldb:/var/lib/mysql:rw mysql



#启动主从模式：   <以下主mysql服务器的名字必须是mysql,否则报错：Connotconfigure slave,please link it to another MYSQL container with alias as 'mysql'>
#1、首先创建mysql主容器：sudo  docker run -d -e REPLICATION_MASTER=true  -P  --name mysql  mysql
#2、创建从mysql容器，并连接主容器: sudo  docker run -d -e REPLICATION_SLAVE=true  -p  --link  mysql:mysql  mysql







