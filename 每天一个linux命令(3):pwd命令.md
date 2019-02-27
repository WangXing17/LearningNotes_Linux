# pwd命令<br>

pwd是Print Working Directory的缩写，意思是打印当前所在工作目录，pwd命令是一个比较简单的命令，需要学习的内容较少。   

1.命令格式：pwd   
2.命令功能：显示当前所在路径（工作目录）   
3.常用参数：   
　　-L:显示当前路径，如果目录是链接时，显示链接路径。（不加参数时默认此方式）    
　　-P:显示当前路径，如果目录是链接时，不使用链接路径，直接显示链接文件所指向的文件。当包含多层链接文件时，显示链接文件最终指向的文件。     
4.常用范例:   
* 例1：查看当前所在路径,命令为pwd 或者 pwd -L
```
[root@localhost var]# pwd
/var
```
* 例2：查看当前所在路径，不使用连接路径,命令为pwd -P
```
[root@localhost ~]# cd /var/   #进入/var目录，该目录下有个mail连接文件，方便对比查看
[root@localhost var]# ll
total 164
...
drwxr-xr-x 12 root root 4096 Apr 22 19:56 log
lrwxrwxrwx  1 root root   10 Oct 17  2015 mail -> spool/mail
drwxr-xr-x  2 root root 4096 May 11  2011 nis
...

[root@localhost var]# cd mail/   #进入mail目录，mail为连接文件。
[root@localhost mail]# pwd     #默认，使用连接文件，直接显示连接文件全路径。
/var/mail

[root@localhost mail]# pwd -P    #不使用逻辑路径，连接文件最终指向的文件
/var/spool/mail
```
* 例3：多层连接文件时，显示所有连接文件最终指向的文件全路径,命令为pwd -P
```
[root@localhost ~]# ll      # /root目录下面有个dir1目录，test连接文件指向dir1目录
total 12
drwxr-xr-x 2 root root 4096 Apr 24 05:51 dir1
lrwxrwxrwx 1 root root    5 Apr 24 05:54 test -> dir1/
[root@localhost ~]# ll /home/   #/home目录下面有一个test连接文件，指向/root/test连接文件 
total 20
drwx------ 16 sgl  sgl  4096 Oct 17  2015 sgl
lrwxrwxrwx  1 root root   10 Apr 24 05:55 test -> /root/test

[root@localhost ~]# cd /home/test/   #通过cd命令进入/home/test
[root@localhost test]# pwd      #默认，只显示连接文件的全路径
/home/test
[root@localhost test]# pwd -P   # 显示连接文件最终指向的文件的全路径。注意这里不是/root/test。
/root/dir1
```
