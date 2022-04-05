Apache安装

本教程使用Apache作为后端服务器，并在云服务器上创建一个MySQL数据库用来存储数据。

在ECS服务器上，执行以下命令，安装Apache服务及其扩展包。

```
yum -y install httpd httpd-manual mod_ssl mod_perl mod_auth_mysql
```

在浏览器访问主机ip，可以得到一个页面（要开放80端口）