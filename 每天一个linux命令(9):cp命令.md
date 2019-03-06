# cp命令    

cp是copy files and directories的缩写，意思是复制文件或目录。cp是一个非常常用的命令，必须要熟练掌握。

1.命令格式：   
　　1) cp [option] SOURCE DIRECTORY   
　　2) cp [option] -t DIRECTORY SOURCE   
　　3) cp [option] [-T] SOURCE DEST   
2.命令功能：将源文件复制至目标文件，或将多个源文件复制至目标目录。   

3.常用参数：   
　　-a,--archive:相当于-dR --preserve=all。   
　　--backup[=CONTROL]：当目标文件存在时为其创建一个备份。    
　　-b:类似--backup，但是不接受参数。   
　　-d：等于--no-dereference --preserve=links。   
　　-f,--force:如果一个存在的目标文件无法打开，则将其移除并重试。    
　　-i,--interactive: 若目标文件已经存在时，就会询问是否覆盖。（会使-n失效）     
　　-n,--no-clobber：若目标文件已经存在时，不要覆盖。（会使-i失效）    
　　-l,--link：创建硬链接文件而不是复制文件。    
　　-s,--symbolic-link:创建符号链接（软链接）文件而不是复制文件   
　　-L,--dereference：总是跟随符号链接。    
　　-p，--no-dereference：不跟随源文件中的符号链接。    
　　-t,--target-directory=DIRECTORY:指定目标目录，复制所有的源文件到目标目录中。    
　　-r,-R,--recursive:复制目录及目录内的所有内容。   
4.常用范例：   
* 例1：复制a.txt，b.txt，c.txt到test1目录，文件在目标目录中不存在。命令为cp a.txt b.txt c.txt test1
```
xw@ubuntu:~/Linux_Everyday/Mar/6_Mar$ ls -R
.:
a.txt  b.txt  c.txt  test1

./test1:
xw@ubuntu:~/Linux_Everyday/Mar/6_Mar$ cp a.txt b.txt c.txt test1
xw@ubuntu:~/Linux_Everyday/Mar/6_Mar$ ls -R
.:
a.txt  b.txt  c.txt  test1

./test1:
a.txt  b.txt  c.txt
xw@ubuntu:~/Linux_Everyday/Mar/6_Mar$ ls -lR
.:
total 8
-rw-r--r-- 1 xw xw    3 Mar  6 03:39 a.txt
-rw-r--r-- 1 xw xw    0 Mar  6 03:40 b.txt
-rw-r--r-- 1 xw xw    0 Mar  6 04:09 c.txt
drwxr-xr-x 2 xw xw 4096 Mar  6 04:10 test1

./test1:
total 4
-rw-r--r-- 1 xw xw 3 Mar  6 04:10 a.txt
-rw-r--r-- 1 xw xw 0 Mar  6 04:10 b.txt
-rw-r--r-- 1 xw xw 0 Mar  6 04:10 c.txt
```
##### 说明
```
在没有带-a参数时，两个文件的时间是不一样的。在带了-a参数时，两个文件的时间是一致的。
```
* 例2：目标文件存在时，会询问是否覆盖。命令为cp -i a.txt b.txt c.txt test1
```
xw@ubuntu:~/Linux_Everyday/Mar/6_Mar$ cp -i a.txt b.txt c.txt test1
cp: overwrite 'test1/a.txt'? y
cp: overwrite 'test1/b.txt'? y
cp: overwrite 'test1/c.txt'? y
xw@ubuntu:~/Linux_Everyday/Mar/6_Mar$ ls -R
.:
a.txt  b.txt  c.txt  test1

./test1:
a.txt  b.txt  c.txt
```
* 例3：复制整个目录。命令为cp -a test1 test2
```
目录存在时   
xw@ubuntu:~/Linux_Everyday/Mar/6_Mar$ ls
a.txt  b.txt  c.txt  test1
xw@ubuntu:~/Linux_Everyday/Mar/6_Mar$ mkdir test2
xw@ubuntu:~/Linux_Everyday/Mar/6_Mar$ ls
a.txt  b.txt  c.txt  test1  test2
xw@ubuntu:~/Linux_Everyday/Mar/6_Mar$ cp -a test1 test2
xw@ubuntu:~/Linux_Everyday/Mar/6_Mar$ ls -R
.:
a.txt  b.txt  c.txt  test1  test2

./test1:
a.txt  b.txt  c.txt

./test2:
test1

./test2/test1:
a.txt  b.txt  c.txt
```
```
目录不存在时    
xw@ubuntu:~/Linux_Everyday/Mar/6_Mar$ ls
a.txt  b.txt  c.txt  test1
xw@ubuntu:~/Linux_Everyday/Mar/6_Mar$ cp -a test1/ test2
xw@ubuntu:~/Linux_Everyday/Mar/6_Mar$ ls -R
.:
a.txt  b.txt  c.txt  test1  test2

./test1:
a.txt  b.txt  c.txt

./test2:
a.txt  b.txt  c.txt
```
##### 说明
```
注意目标目录存在与否结果是不一样的。目标目录存在时，整个源目录被复制到目标目录里面。
```
* 例4：复制的 a.txt建立一个连结档a_link.txt。命令为cp -s a.txt a_link.txt
```
xw@ubuntu:~/Linux_Everyday/Mar/6_Mar$ cp -s a.txt a_link.txt
xw@ubuntu:~/Linux_Everyday/Mar/6_Mar$ ls -l
total 12
lrwxrwxrwx 1 xw xw    5 Mar  6 04:26 a_link.txt -> a.txt
-rw-r--r-- 1 xw xw    3 Mar  6 03:39 a.txt
-rw-r--r-- 1 xw xw    0 Mar  6 03:40 b.txt
-rw-r--r-- 1 xw xw    0 Mar  6 04:09 c.txt
drwxr-xr-x 2 xw xw 4096 Mar  6 04:10 test1
drwxr-xr-x 3 xw xw 4096 Mar  6 04:20 test2
xw@ubuntu:~/Linux_Everyday/Mar/6_Mar$ cat a_link.txt 
aa
```
