# cd 命令

Linux cd 命令可以说是Linux中最基本的命令语句，其他的命令语句要进行操作，都是建立在使用 cd 命令上的。所以，学习Linux 常用命令，首先就要学好 cd 命令的使用方法技巧。

## 命令格式

cd [目录名]

## 命令功能

切换当前目录至dirName

## 使用范例

**例一：进入系统根目录**

命令

```bash
cd /
```

输出


```bash
[root@localhost ~]# cd / 
```

进入系统根目录,上面命令执行完后拿ls命令看一下，当前目录已经到系统根目录了

```bash
[root@localhost soft]# pwd
/opt/soft
[root@localhost soft]# cd ..
[root@localhost opt]# cd ..//
[root@localhost /]# pwd
/
```

**例2：使用 cd 命令进入当前用户主目录**

```
[root@localhost soft]# cd ~
[root@localhost ~]# pwd
/root
```

**例3：返回进入此目录之前所在的目录** 

```
[root@localhost soft]# pwd
/opt/soft
[root@localhost soft]# cd -
/root
[root@localhost ~]# pwd
/root
[root@localhost ~]# cd -
/opt/soft
[root@localhost soft]#
```

**例4：把上个命令的参数作为cd参数使用**

命令 `cd !$`

```
[root@localhost soft]# cd !$
cd -
/root
[root@localhost ~]# cd !$
cd -
/opt/soft
[root@localhost soft]#
```