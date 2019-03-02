# rmdir命令   

rmdir是remove empty directories的缩写，意思为移除空的目录。功能类似rm -d dirName。    

1.命令格式：rmdir [option] dirName   

2.命令功能：移除空的目录。   

3.常用参数：   
　　-p,--parents:递归删除目录dirName以及其祖先目录，当子目录删除后其父目录为空时，也一同被删除。如果整个路径被删除或者由于某种原因保留部分路径，则系统在标准输出上显示相应的信息。   
　　-v,--verbose:显示指令执行过程。

4.常用范例：   
* 例1：删除名为test1的空目录。命令为rmdir test1。如果目录不为空会提示错误。
```
xw@ubuntu:~/Linux_Everyday/2_Mar$ mkdir test1
xw@ubuntu:~/Linux_Everyday/2_Mar$ ls
test1
xw@ubuntu:~/Linux_Everyday/2_Mar$ ls -R
.:
test1

./test1:
xw@ubuntu:~/Linux_Everyday/2_Mar$ rmdir test1
xw@ubuntu:~/Linux_Everyday/2_Mar$ ls
xw@ubuntu:~/Linux_Everyday/2_Mar$ 
```
```
xw@ubuntu:~/Linux_Everyday/2_Mar$ mkdir -p test1/test2/test3
xw@ubuntu:~/Linux_Everyday/2_Mar$ ls -R
.:
test1

./test1:
test2

./test1/test2:
test3

./test1/test2/test3:
xw@ubuntu:~/Linux_Everyday/2_Mar$ rmdir test1/
rmdir: failed to remove 'test1/': Directory not empty
```
* 例2：递归删除test3以及其祖先目录。命令为mkdir -p test1/test2/test3。
```
xw@ubuntu:~/Linux_Everyday/2_Mar$ mkdir -p test1/test2/test3
xw@ubuntu:~/Linux_Everyday/2_Mar$ ls -R
.:
test1

./test1:
test2

./test1/test2:
test3

./test1/test2/test3:
xw@ubuntu:~/Linux_Everyday/2_Mar$ rmdir -pv test1/test2/test3/
rmdir: removing directory, 'test1/test2/test3/'
rmdir: removing directory, 'test1/test2'
rmdir: removing directory, 'test1'
xw@ubuntu:~/Linux_Everyday/2_Mar$ 
```
