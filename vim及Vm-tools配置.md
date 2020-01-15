## 安装vmware tools 

设置共享文件夹需要先安装**vmware tools **

然后点击VMware菜单栏“虚拟机”下的“安装VMware Tools”

​                         ![image-20200115094352467](00_vim及Vm-tools配置.assets/image-20200115094352467.png)      

然后，会在Linux的系统桌面上生成一个名字为“VMware Tools”的光驱文件。

 ![image-20200115094358046](00_vim及Vm-tools配置.assets/image-20200115094358046.png)

双击“VMware Tools”光驱文件并进入，会看到一个后缀为.tar.gz的压缩文件。

 ![image-20200115094405306](00_vim及Vm-tools配置.assets/image-20200115094405306.png)

将压缩文件复制到home目录下

打开命令行终端，默认应该就是home目录，如果不是home目录，在命令行终端输入“cd ~”命令进入home目录下，在home目录下输入"ls"命令就可以看到我们刚刚复制的压缩包文件。

 ![image-20200115094419444](00_vim及Vm-tools配置.assets/image-20200115094419444.png)

执行 tar -xvf VMwareTools-10.2.0-7259539.tar.gz

 ![image-20200115094424031](00_vim及Vm-tools配置.assets/image-20200115094424031.png)

进入解压后的目录 

 ![image-20200115094429927](00_vim及Vm-tools配置.assets/image-20200115094429927.png)

执行 sudo ./vmware-install.pl 一路回车 + yes

重启客户机 然后就可以正常复制文件 和 设置共享文件夹了

 ![image-20200115094435366](00_vim及Vm-tools配置.assets/image-20200115094435366.png)

 ![image-20200115094442686](00_vim及Vm-tools配置.assets/image-20200115094442686.png)

 ![image-20200115094446887](00_vim及Vm-tools配置.assets/image-20200115094446887.png)

 

## vim配置：

1、拷贝vimconfig.tar.gz压缩包到自己的虚拟机

​          ![image-20200115131542496](00_vim及Vm-tools配置.assets/image-20200115131542496.png)                    

2、在自己vimconfig.tar.gz所在的路径输入tar -xvf vimconfig.tar.gz对该压缩包进行解压，人下图所示

 ![image-20200115131547358](00_vim及Vm-tools配置.assets/image-20200115131547358.png)

解压完成如下图所示，生成vimconfig目录

 ![image-20200115131553559](00_vim及Vm-tools配置.assets/image-20200115131553559.png)

3、cd切换到vimconfig目录，执行config.sh，如下图

 ![image-20200115131557596](00_vim及Vm-tools配置.assets/image-20200115131557596.png)

报这些问题不要紧，在线安装ctags

 ![image-20200115131603716](00_vim及Vm-tools配置.assets/image-20200115131603716.png)

安装完成再次执行config.sh，如下图所示，这样就表示成功了

 ![image-20200115131608507](00_vim及Vm-tools配置.assets/image-20200115131608507.png)

Vi测试，出如下错误，安装下vim就可以了。

 ![image-20200115131613346](00_vim及Vm-tools配置.assets/image-20200115131613346.png)

sudo apt-get install vim

 ![image-20200115131623007](00_vim及Vm-tools配置.assets/image-20200115131623007.png)

 

 