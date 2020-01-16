## samba服务的安装及配置

 **一、安装：**

```
sudo apt-get install samba
```

**二、配置：**

  1、创建一个需要共享的目录，并修改权限：

```
lpf@ubuntu:~$ mkdir 1703
lpf@ubuntu:~$ sudo chmod 777 1703/ -R 
```

  2、打开配置文件：

```
lpf@ubuntu:~$ sudo vim /etc/samba/smb.conf
```

  3、对创建的共享目录进行配置并保存退出：

```
    [1703]
path = /home/lpf/1703
available = yes
browseable = yes
public = yes
writable = yes
```

**三、重新samba服务：**

```
  lpf@ubuntu:~/1703$ sudo /etc/init.d/smbd restart
```

**四、测试：**

```
在windows中点击：
-->开始
--->运行
--->\\linux的IP （例如：\\192.168.7.4）
```

五、设置samba密码：

  （1）、在配置文件/etc/samba/smb.conf中加入以下内容：

```
 [1703]
path = /home/lpf/1703
available = yes
browseable = yes
public = yes
writable = yes
valid users = lpf
```

  （2）、设置samba密码：

```
 sudo smbpasswd -a lpf
```

  （3）、重启samba服务：

```
sudo /etc/init.d/smbd restart
```

