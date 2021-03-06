unzip命令是用于.zip格式文件的解压缩工具 ，unzip命令将列出、测试或从zip格式存档中提取文件，这些文件通常位于MS-DOS系统上。

默认行为（就是没有选项）是从指定的ZIP存档中提取所有的文件到当前目录（及其下面的子目录）。一个配套程序zip（1L）创建ZIP存档；这两个程序都与PKWARE的PKZIP和PKUNZIP为MS-DOS创建的存档文件兼容，但许多情况下，程序选项或默认行为是不同的。

**语法格式：**unzip [参数] [文件]

**常用参数：**

|      |                                                  |
| ---- | ------------------------------------------------ |
| -l   | 显示压缩文件内所包含的文件                       |
| -v   | 执行时显示详细的信息                             |
| -c   | 将解压缩的结果显示到屏幕上，并对字符做适当的转换 |
| -n   | 解压缩时不要覆盖原有的文件                       |
| -j   | 不处理压缩文件中原有的目录路径                   |
| -o   | 覆盖文件而不提示                                 |

**参考实例**

把/home目录下面的mydata.zip解压到mydatabak目录里面：

```
[root@linuxcool ~]# unzip mydata.zip -d mydatabak 
```

把/home目录下面的wwwroot.zip直接解压到/home目录里面：

```
[root@linuxcool ~]# unzip wwwroot.zip 
```

把/home目录下面的abc12.zip、abc23.zip、abc34.zip同时解压到/home目录里面：

```
[root@linuxcool ~]# unzip abc\*.zip 
```

查看把/home目录下面的wwwroot.zip里面的内容：

```
[root@linuxcool ~]# unzip -v wwwroot.zip 
```

验证/home目录下面的wwwroot.zip是否完整：

```
[root@linuxcool ~]# unzip -t wwwroot.zip  
```