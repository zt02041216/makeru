1、终端输入：

```
sudo service network-manager stop
sudo rm /var/lib/NetworkManager/NetworkManager.state
sudo service network-manager start
```

一般此时图标已经出来了。

然后：

```
sudo gedit /etc/NetworkManager/NetworkManager.conf
```

把false改成true

把false改成true

![image-20200116110533091](0.2.3_ubuntu 18.04 网络图标不见的问题解决方案.assets/image-20200116110533091.png)



![image-20200116110704875](0.2.3_ubuntu 18.04 网络图标不见的问题解决方案.assets/image-20200116110704875.png)

最后：

```
sudo service network-manager restart
```

网络测试：ping  www.naidu.com

![image-20200116111102707](0.2.3_ubuntu 18.04 网络图标不见的问题解决方案.assets/image-20200116111102707.png)

查看网段：

![image-20200116111251639](0.2.3_ubuntu 18.04 网络图标不见的问题解决方案.assets/image-20200116111251639.png)





结束。。。。。。