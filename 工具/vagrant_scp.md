#vagrant使用scp拷贝文件

vagrant 在安装完毕后, 默认的用户名是`vagrant`,密码也是`vagrant`; 开发连接到vagrant的ssh端口是2222.

我们可以使用这个命令来查看vagrant的ssh配置

```bash
$ vagrant ssh-config
Host default
  HostName 127.0.0.1
  User vagrant
  Port 2222
  UserKnownHostsFile /dev/null
  StrictHostKeyChecking no
  PasswordAuthentication no
  IdentityFile /Users/hujun-iri/vagrant_project/.vagrant/machines/default/virtualbox/private_key
  IdentitiesOnly yes
  LogLevel FATAL
```

可以使用下面的命令格式来实现从本地往vagrant虚拟机里面拷贝文件
```bash
$ scp -P 2222 ~/Downloads/node-v5.0.0-linux-x64.tar.gz vagrant@127.0.0.1:/home/vagrant/Download
```

>上面的命令是把本地的`~/Downloads/node-v5.0.0-linux-x64.tar.gz`复制到vagrant虚拟机的`/home/vagrant/Download`目录下面
