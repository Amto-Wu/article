Centos7之后从init完全换成了systemd的启动方式，systemd 启动服务的机制主要是通过 systemctl 的这个系统服务管理指令来处理。systemctl在用法上也囊括 service / chkconfig / setup / init 的大部分功能。

**语法格式**：systemctl [参数] [服务]

**常用参数：**

|                             |                    |
| --------------------------- | ------------------ |
| -start                      | 启动服务           |
| -stop                       | 停止服务           |
| -restart                    | 重启服务           |
| -enable                     | 使某服务开机自启   |
| -disable                    | 关闭某服务开机自启 |
| -status                     | 查看服务状态       |
| -list -units --type=service | 列举所有已启动服务 |

**参考实例**

启动httpd服务：

```
[root@linuxcool ~]# systemctl start httpd.service 
```

停止httpd服务：

```
[root@linuxcool ~]# systemctl stop httpd.service 
```

重启httpd服务：

```
[root@linuxcool ~]# systemctl restart httpd.service 
```

查看httpd服务状态：

```
[root@linuxcool ~]# systemctl status httpd.service  
```

使httpd开机自启：

```
[root@linuxcool ~]# systemctl enable httpd.service  
```

取消httpd开机自启：

```
[root@linuxcool ~]# systemctl disable httpd.service   
```

列举所有已启动服务(unit单元) ：

```
[root@linuxcool ~]# systemctl list-units --type=service
```