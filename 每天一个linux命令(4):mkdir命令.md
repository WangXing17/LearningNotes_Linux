# mkdir命令   

mkdir是make directories的缩写，意思是创建目录(文件夹)。mkdir命令也是用的很多的命令，用法也是相对简单。    

1.命令格式：mkdir [option] dirName   
2.命令功能：创建名为dirName的文件夹   
3.常用参数：   
　　-m,--mode=Mode:为目录指定访问权限，类似chmod,而不是a=rwx-umask(777-umask)。   
```
umask设置了用户创建文件的默认权限，它与chmod的效果刚好相反，umask设置的是权限“补码”，而chmod设置的是文件权限码。    
一般可在/etc/profile、/etc/bashrc、$ [HOME]/.bash_profile、$[HOME]/.profile或$[HOME]/.bashrc中设置umask值。
```
　　-p,--parents:如果目录已经存在，则不会有错误提示。若父目录不存在，将会创建父目录。该选项常用于创建级联目录。    
　　-v,--verbose:为每个创建的目录打印提示信息。   
  
4.常用范例：   
* 例1：创建一个名为test1空目录,命令为mkdir test1     
```
xw@ubuntu:~/Linux_Everyday/28_Feb$ mkdir test1
xw@ubuntu:~/Linux_Everyday/28_Feb$ ls -l
total 4
drwxr-xr-x 2 xw xw 4096 Feb 28 04:52 test1
```
* 例2：创建多个目录，命令为mkdir test2 test3 test4 或者 mkdir {test2,test3,test4}
```
xw@ubuntu:~/Linux_Everyday/28_Feb$ mkdir test2 test3 test4
xw@ubuntu:~/Linux_Everyday/28_Feb$ ls -l
total 16
drwxr-xr-x 2 xw xw 4096 Feb 28 04:52 test1
drwxr-xr-x 2 xw xw 4096 Feb 28 05:06 test2
drwxr-xr-x 2 xw xw 4096 Feb 28 05:06 test3
drwxr-xr-x 2 xw xw 4096 Feb 28 05:06 test4
```
```
xw@ubuntu:~/Linux_Everyday/28_Feb$ mkdir {test2,test3,test4}
xw@ubuntu:~/Linux_Everyday/28_Feb$ ls -l
total 16
drwxr-xr-x 2 xw xw 4096 Feb 28 04:52 test1
drwxr-xr-x 2 xw xw 4096 Feb 28 05:09 test2
drwxr-xr-x 2 xw xw 4096 Feb 28 05:09 test3
drwxr-xr-x 2 xw xw 4096 Feb 28 05:09 test4
```
* 例3：创建级联目录,同一目录下的子目录放在大括号中，并用逗号分隔。命令为mkdir -p aa/{bb,cc/{dd,ee}}
```
xw@ubuntu:~/Linux_Everyday/28_Feb$ mkdir -p aa/{bb,cc/{dd,ee}}
xw@ubuntu:~/Linux_Everyday/28_Feb$ ls -R aa
aa:
bb  cc

aa/bb:

aa/cc:
dd  ee

aa/cc/dd:

aa/cc/ee:
```
* 例4-1：为创建的test5目录指定权限。命令为mkdir -m 777 test5。   
```
xw@ubuntu:~/Linux_Everyday/28_Feb$ mkdir -m 777 test5
xw@ubuntu:~/Linux_Everyday/28_Feb$ ls -l
total 28
drwxr-xr-x 4 xw xw 4096 Feb 28 05:15 aa
drwxr-xr-x 5 xw xw 4096 Feb 28 05:29 baklog
drwxr-xr-x 2 xw xw 4096 Feb 28 04:52 test1
drwxr-xr-x 2 xw xw 4096 Feb 28 05:09 test2
drwxr-xr-x 2 xw xw 4096 Feb 28 05:09 test3
drwxr-xr-x 2 xw xw 4096 Feb 28 05:09 test4
drwxrwxrwx 2 xw xw 4096 Feb 28 17:10 test5
```
* 例4-2：为目录指定权限，指定的权限为mode-umask。例如，mode=rw，umask=022，则最终权限为666-022=644，即rw-r--r--。    
```
xw@ubuntu:~/Linux_Everyday/28_Feb/test5$ mkdir -m=r a
xw@ubuntu:~/Linux_Everyday/28_Feb/test5$ mkdir -m=w b
xw@ubuntu:~/Linux_Everyday/28_Feb/test5$ mkdir -m=rw c
xw@ubuntu:~/Linux_Everyday/28_Feb/test5$ mkdir -m=rx d
xw@ubuntu:~/Linux_Everyday/28_Feb/test5$ mkdir -m=rwx e
xw@ubuntu:~/Linux_Everyday/28_Feb/test5$ ls -l
total 20
dr--r--r-- 2 xw xw 4096 Feb 28 17:19 a
d-w------- 2 xw xw 4096 Feb 28 17:19 b
drw-r--r-- 2 xw xw 4096 Feb 28 17:19 c
dr-xr-xr-x 2 xw xw 4096 Feb 28 17:19 d
drwxr-xr-x 2 xw xw 4096 Feb 28 17:20 e
```
* 例5： 查看创建目录的过程信息。命令为mkdir -vp baklog/{bin,lib,log/{cep,dod,testlog}}   
```
xw@ubuntu:~/Linux_Everyday/28_Feb$ mkdir -vp baklog/{bin,lib,log/{cep,dod,testlog}}
mkdir: created directory 'baklog'
mkdir: created directory 'baklog/bin'
mkdir: created directory 'baklog/lib'
mkdir: created directory 'baklog/log'
mkdir: created directory 'baklog/log/cep'
mkdir: created directory 'baklog/log/dod'
mkdir: created directory 'baklog/log/testlog'
xw@ubuntu:~/Linux_Everyday/28_Feb$ ls -R baklog/
baklog/:
bin  lib  log

baklog/bin:

baklog/lib:

baklog/log:
cep  dod  testlog

baklog/log/cep:

baklog/log/dod:

baklog/log/testlog:
```
