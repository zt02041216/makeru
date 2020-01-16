## 1、对于fork函数的理解：

  一个进程包括代码、数据和分配给进程的资源。  fork（）函数通过系统调用创建一个与原来进程几乎完全相同的进程，即两个进程可以做完全相同的事，但如果初始参数或者传入的变量不同，两个进程也可以做不同的事。      一个进程调用fork（）函数后，系统先给新的进程分配资源，例如存储数据和代码的空间。然后把原来的进程的所有值都复制到新的新进程中，只有少数值与原来的进程的值不同，相当于克隆了一个自己。      一个现有进程可以调用fork函数创建一个新进程。由fork创建的新进程被称为子进程（child process）。fork函数被调用一次但返回两次。  

 

## 2、为什么fork会返回两次？

  在复制时复制了父进程的堆栈段，所以两个进程都停留在fork函数中，等待返回。因此fork函数会返回两次，一次是在父进程中返回，另一次是在子进程中返回，这两次的返回值是不一样的。  

 

**代码示例:**

```c
#include<stdio.h>
#include<unistd.h>
int main(){
	int pid;
	pid=fork();
	int i = 0;
	for(i=0;i<2;i++){
		if(pid==0){
			printf("I am old son, my pid is %d\n",getpid());
		}else if(pid>0){
			printf("I am father, my pid is %d\n",getpid());
			pid=fork();
			if(pid==0){
				printf("I am young girl, my pid is %d\n",getpid());
			}else if(pid>0){
				printf("I am father, my pid is %d\n",getpid());
			}else{
				printf("fork() error.\n");}}
		else{
			printf("fork() error.\n");}}
	return 0;}

```

```
运行结果：
linux@linux:~/Desktop$ gcc test.c 
linux@linux:~/Desktop$ ./a.out 
I am father, my pid is 3849
I am father, my pid is 3849
I am father, my pid is 3849
I am father, my pid is 3849
I am young girl, my pid is 3852
I am young girl, my pid is 3851
I am old son, my pid is 3851
I am old son, my pid is 3850
I am old son, my pid is 3850
```

**实例总结：**

  从进程并发执行来看，上面的三个进程没有同步措施，只要进程就绪就可能执行，因此各种执行顺序都有可能，所以三个进程的输出次序带有随机性。并且，每当一个进程执行了一段时间，其它就绪进程可能抢占处理机，因此，多个进程可能交错执行。不过，操作系统实现函数printf( )时，保证了进程每次调用该函数输出一个字符串时不会被中断。本次实验虽然有些难度，但大家不要灰心，仔细想想问题还是能够得到解决的（把fork()函数放入父进程即可实现）  。

## 3、运行程序的父进程是多少，进程0号和1号的作用

**解决办法：**

  可以编写一个死循环，使用ps –ef查看当前程序的父进程，最终都是0号进程。  进程0：Linux引导中创建的第一个进程，完成加载系统后，演变为进程调度、交换及存储管理进程  进程1：init 进程，由0进程创建，完成系统的初始化. 是系统中所有其它用户进程的祖先进程  

## 4、 Could not get lock /var/lib/dpkg/lock-frontend - open (11: Resource temporarly unavailable)

**问题描述：**

```
Could not get lock /var/lib/dpkg/lock-frontend - open (11: Resource temporarly unavailable)
Unable to acquire the dpkg frontend lock (/var/lib/dpkg/lock-frontend), is an other process using it?
```

**问题解决：**

```
1 首先查看是否有apt-get这个程序在运行
　　ps aux|grep apt-get
2 如果发现存在这样的程序在运行那么就kill掉，否则执行2.3
3 直接删除锁文件
　　sudo rm /var/lib/dpkg/lock-frontend
　　sudo rm /var/lib/dpkg/lock
```

