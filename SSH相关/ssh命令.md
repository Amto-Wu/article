## ssh命令

**ssh命令**是 openssh 套件中的客户端连接工具，可以给予ssh加密协议实现安全的远程登录服务器。

### 语法

```shell
ssh(选项)(参数)
```

### 选项

```sh
-1：强制使用ssh协议版本1；
-2：强制使用ssh协议版本2；
-4：强制使用IPv4地址；
-6：强制使用IPv6地址；
-A：开启认证代理连接转发功能；
-a：关闭认证代理连接转发功能；
-b：使用本机指定地址作为对应连接的源ip地址；
-C：请求压缩所有数据；
-F：指定ssh指令的配置文件；
-f：后台执行ssh指令；
-g：允许远程主机连接主机的转发端口；
-i：指定身份文件；
-l：指定连接远程服务器登录用户名；
-N：不执行远程指令；
-o：指定配置选项；
-p：指定远程服务器上的端口；
-q：静默模式；
-X：开启X11转发功能；
-x：关闭X11转发功能；
-y：开启信任X11转发功能。
-T: 测试连接
```

### 参数

- 远程主机：指定要连接的远程 ssh 服务器；
- 指令：要在远程ssh服务器上执行的指令。

**工作流程：**

这里我们可以使用 `-i` 指定私钥文件

```sh
# 生成密钥对
ssh-keygen -t rsa -C "your_email@example.com" -b 2048 
# 上传公钥 
ssh-copy-id -i ~/.ssh/id_rsa2.pub root@127.0.0.1 -p 2222 
# 连接 
ssh -p 2222 -i ~/.ssh/id_rsa2 root@127.0.0.1 
```



## ssh-keygen命令

**ssh-keygen命令**用于为"ssh"生成、管理和转换认证密钥，它支持RSA和DSA两种认证密钥。

### 语法

```sh
ssh-keygen(选项)
```



### 选项

```sh
-b：指定密钥长度；
-e：读取openssh的私钥或者公钥文件；
-C：添加注释；
-f：指定用来保存密钥的文件名；
-i：读取未加密的ssh-v2兼容的私钥/公钥文件，然后在标准输出设备上显示openssh兼容的私钥/公钥；
-l：显示公钥文件的指纹数据；
-N：提供一个新密码；
-P：更改（旧）密码；
-q：静默模式；
-t：指定要创建的密钥类型。
```



为私钥添加或更改密码：

```sh
$ ssh-keygen -p
# Start the SSH key creation process 
> Enter file in which the key is (/Users/you/.ssh/id_rsa): [Hit enter] 
> Key has comment '/Users/you/.ssh/id_rsa' 
> Enter new passphrase (empty for no passphrase): [Type new passphrase] 
> Enter same passphrase again: [One more time for luck] 
> Your identification has been saved with the new passphrase. 
```



## ssh-agent命令

ssh agent ，意为 ssh 代理，是一个密钥管理器，用来管理一个多个密钥，并为其他需要使用 ssh key 的程序提供代理。

### 语法

```sh
ssh-agent [-c | -s] [-d] [-a bind_address] [-t life] [command [arg ...]]
ssh-agent [-c | -s] -k
```



### 选项

```sh
-a bind_address：bind the agent to the UNIX-domain socket bind_address.
-c：生成C-shell风格的命令输出。
-d：调试模式。
-k：把ssh-agent进程杀掉。
-s：生成Bourne shell 风格的命令输出。
-t life：设置默认值添加到代理人的身份最大寿命。
```



### 实例

运行ssh-agent，它会打印出来它使用的环境和变量：

```sh
$ ssh-agent 
SSH_AUTH_SOCK=/tmp/ssh-U91ObneiXkoL/agent.4608; export SSH_AUTH_SOCK; SSH_AGENT_PID=1392; export SSH_AGENT_PID; echo Agent pid 1392; 
```



**启动与关闭ssh-agent**

**方式一：**

在`子shell`中打开ssh-agent，执行该命令后我们也会进入到子shell中；退出子shell自动结束代理（这是一种安全机制）。

```
# 这里 $SHELL 会自动选择当前默认shell  
# 可以指定为 bash、csh等各种shell 
ssh-agent $SHELL 
```



**方式二：**

通过`当前shell`下开启一个ssh-agent进程，为了安全考虑退出当前shell**之前**可以使用`ssh-agent -k`关闭对应代理（只有在当前shell中还可使用上述命令关闭对应代理，在其它shell中就只能使用kill命令了）。

```sh
# 启动 
# 在 linux 中 
eval ssh-agent
# 在 Windows 中 
eval $(ssh-agent) 
# 关闭 
ssh-add -D 
ssh-agent -k 
```



> 这两种启动方式 的 另一种解释：启动ssh-agent，您可以创建一个继承SSH_AUTH_SOCK环境变量的子进程，也可以将其作为守护进程运行。

## ssh-add命令

**ssh-add命令** ，作用：是把专用密钥添加到 ssh-agent 的高速缓存中。

```sh
ssh-add [-cDdLlXx] [-t life] [file ...]
ssh-add -s pkcs11
ssh-add -e pkcs11
```



### 选项

```sh
-D：删除ssh-agent中的所有密钥.
-d：从ssh-agent中的删除密钥
-e pkcs11：删除PKCS#11共享库pkcs1提供的钥匙。
-s pkcs11：添加PKCS#11共享库pkcs1提供的钥匙。
-L：显示ssh-agent中的公钥
-l：显示ssh-agent中的密钥
-t life：对加载的密钥设置超时时间，超时ssh-agent将自动卸载密钥
-X：对ssh-agent进行解锁
-x：对ssh-agent进行加锁
```



### 实例

1、把专用密钥添加到 ssh-agent 的高速缓存中：

```sh
ssh-add ~/.ssh/id_dsa
```



2、从ssh-agent中删除密钥：

```sh
ssh-add -d ~/.ssh/id_xxx.pub
```



3、查看ssh-agent中的密钥：

```sh
ssh-add -l
```



更多

```sh
# 将私钥添加到 ssh-agent 
ssh-add ~/.ssh/key_name 
# 添加时同时指定私钥失效时间 
ssh-add -t <seconds> 
# 查看ssh-agent中的私钥 
ssh-add -l 
# 查看ssh-agent中的公钥 
ssh-add -L 
# 测试连接（这里是github） 
ssh -T git@github.com 
# 移除指定私钥 
ssh-add -d ~/.ssh/key_name 
# 移除ssh-agent 中的所有私钥 
ssh-add -D 
# 锁定ssh-agent ：创建锁时需要设置密码 
ssh-add -x 
# 解锁 ssh-agent ：输入密码 
ssh-add -X 
```



## ssh-copy-id命令

**ssh-copy-id命令**可以把本地主机的公钥复制到远程主机的authorized_keys文件上，ssh-copy-id命令也会给远程主机的用户主目录（home）和`~/.ssh`, 和`~/.ssh/authorized_keys`设置合适的权限。

### 语法

```sh
ssh-copy-id [-i [identity_file]] [user@]machine
```



### 选项

```sh
-i：指定公钥文件
```



### 实例

1、把本地的ssh公钥文件安装到远程主机对应的账户下：

```sh
ssh-copy-id user@server
ssh-copy-id -i ~/.ssh/id_rsa.pub user@server
```



## ssh-keyscan命令

**ssh-keyscan命令**是一个收集大量主机公钥的使用工具。

### 语法

```sh
ssh-keyscan(选项)(参数)
```



### 选项

```sh
-4：强制使用IPv4地址；
-6：强制使用IPv6地址；
-f：从指定文件中读取"地址列表/名字列表"；
-p：指定连接远程主机的端口；
-T：指定连接尝试的超时时间；
-t：指定要创建的密钥类型；
-v：信息模式，打印调试信息。
```

