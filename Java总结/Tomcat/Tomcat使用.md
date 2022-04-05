Tomcat使用

## 目录结构

- bin：存放tomcat的可执行命令，比如启动和停止。命令主要有两大类：以.bat结尾的是windows命令、以.sh结尾的是linux命令。很多环境变量的设置都在此处，例如可以设置JDK路径、TOMCAT路径，startup 用来启动tomcat，shutdown 用来关闭tomcat，修改catalina可以设置tomcat的内存。
- conf：存放tomcat的配置文件。例如端口设置，用户信息配置等。
- lib：存放tomcat运行依赖的jar包。
- logs：存放tomcat在运行过程中产生的日志文件
- temp：存放tomcat在运行过程中产生的临时文件
- webapps：存放网站内容
- work：用来存放tomcat在运行时的编译后文件，例如JSP编译后的文件。清空work目录，然后重启tomcat，可以达到清除缓存的作用。

## 使用

双击 bin 目录下的 startup.bat 启动，

双击 bin 目录下的 shutdown.bat 关闭

## 测试

成功启动后，使用浏览器访问 localhost:8080

## 后记

乱码问题

