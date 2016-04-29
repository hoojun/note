生成SSH密钥过程：

1.查看是否已经有了ssh密钥：cd ~/.ssh

如果没有密钥则不会有此文件夹，有则备份删除

2.生成密钥：

```
$ ssh-keygen -t rsa -C “haiyan.xu.vip@gmail.com”
```

按3个回车，密码为空。

```
Your identification has been saved in /home/tekkub/.ssh/id_rsa.
Your public key has been saved in /home/tekkub/.ssh/id_rsa.pub.
The key fingerprint is:
………………
```

最后得到了两个文件：id_rsa和id_rsa.pub