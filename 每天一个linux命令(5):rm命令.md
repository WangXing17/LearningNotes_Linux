# rm命令    

rm是remove files or directories。意为移除文件或目录。rm也是一个非常常用的Linux命令，但同时也是一个非常危险的命令。    
在使用的时候要特别当心，尤其对于新手，否则整个系统就会毁在这个命令（比如在/（根目录）下执行rm * -rf）。    
所以，我们在执行rm之前最好先确认一下在哪个目录，到底要删除什么东西，操作时保持高度清醒的头脑。
    
1.命令格式：rm [option] [file]   

2.命令功能：移除文件或目录，如果删除的文件或目录不存在，会提示。默认情况下是不能删除目录的，要删除目录，需使用- r选项。   

3.常用参数：   
　　-f,--force:忽略不存在的文件，从不给出提示。   
　　-i,--interactive:进行交互式删除。   
　　-d,--dir:删除空的目录。      
　　-r,-R,--recursive:指示rm将参数中列出的全部目录和子目录均递归地删除。   
　　-v,--verbose:详细显示进行的步骤。   
4.常用范例：   
* 例1.带询问的删除a.txt文件，命令为rm -i a.txt   
```
xw@ubuntu:~/Linux_Everyday/1_Mar$ ls
a.txt
xw@ubuntu:~/Linux_Everyday/1_Mar$ rm -i a.txt 
rm: remove regular empty file 'a.txt'? y
xw@ubuntu:~/Linux_Everyday/1_Mar$ ls
xw@ubuntu:~/Linux_Everyday/1_Mar$ 
```
* 例2.不带提示的强行删除a.txt文件，命令为rm -f a.txt   
```
xw@ubuntu:~/Linux_Everyday/1_Mar$ ls
a.txt
xw@ubuntu:~/Linux_Everyday/1_Mar$ rm -f a.txt 
xw@ubuntu:~/Linux_Everyday/1_Mar$ ls
xw@ubuntu:~/Linux_Everyday/1_Mar$
```
* 例3.带信息的删除a.txt文件，命令为rm -v a.txt  
```
xw@ubuntu:~/Linux_Everyday/1_Mar$ ls
a.txt
xw@ubuntu:~/Linux_Everyday/1_Mar$ rm -v a.txt 
removed 'a.txt'
xw@ubuntu:~/Linux_Everyday/1_Mar$ ls
xw@ubuntu:~/Linux_Everyday/1_Mar$ 
```
* 例4.带信息的递归的删除test1目录下的文件，命令为rm -r test1
```
xw@ubuntu:~/Linux_Everyday/1_Mar$ mkdir -p test1/test2/test3
xw@ubuntu:~/Linux_Everyday/1_Mar$ ls -R
.:
test1

./test1:
test2

./test1/test2:
test3

./test1/test2/test3:
xw@ubuntu:~/Linux_Everyday/1_Mar$ rm -rv test1
removed directory 'test1/test2/test3'
removed directory 'test1/test2'
removed directory 'test1'
xw@ubuntu:~/Linux_Everyday/1_Mar$ ls
xw@ubuntu:~/Linux_Everyday/1_Mar$ 
```

