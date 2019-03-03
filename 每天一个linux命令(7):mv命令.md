# mv命令    
mv是move(rename) files的缩写，意思是移动(重命名)文件，linux下经常用此命令来备份文件或目录。   
1.命令格式：   
　　1) mv [option] SOURCE DIRECTORY   
　　2) mv [option] -t DIRECTORY SOURCE   
　　3) mv [option] [-T] SOURCE DEST   
2.命令功能：实现文件的移动或者重命名。    
　　1)DIRECTORY是一个目录。     
　　2)将源文件下所有文件移动到目标目录下。    
　　3)DEST可以是一个文件   
3.常用参数：   
　　-b:若需覆盖文件，则覆盖前先进行备份。   
　　-f,--force:如果目标文件已经存在，不会询问直接覆盖。   
　　-i,--interactive: 若目标文件 已经存在时，就会询问是否覆盖。  
　　-u,--update: 若目标文件已经存在，且SOURCE比较新，才会更新。   
　　-t,--target-directory=DIRECTORY:指定目标目录，移动所有的源文件到目标目录中。    
　　-v,--verbose:提示完成的每一个步骤。   
4.常用范例：   
* 例1：将a.txt重命名为b.log，命令为mv a.txt b.log   
```
xw@ubuntu:~/Linux_Everyday/3_Mar$ ls -l
total 4
-rw-r--r-- 1 xw xw 4 Mar  3 04:32 a.txt
xw@ubuntu:~/Linux_Everyday/3_Mar$ mv a.txt b.log
xw@ubuntu:~/Linux_Everyday/3_Mar$ ls -l
total 4
-rw-r--r-- 1 xw xw 4 Mar  3 04:32 b.log
```
* 例2：将b.log文件移动到test1目录下。命令为mv b.log test1
```
xw@ubuntu:~/Linux_Everyday/3_Mar$ mkdir test1
xw@ubuntu:~/Linux_Everyday/3_Mar$ mv b.log test1/
xw@ubuntu:~/Linux_Everyday/3_Mar$ ls -R
.:
test1

./test1:
b.log
```
* 例3：将文件a.txt，b.txt，c.txt移动到test1目录中。命令为mv a.txt b.txt c.txt test1 或者 mv -t test1 a.txt b.txt c.txt
```
xw@ubuntu:~/Linux_Everyday/3_Mar$ touch a.txt
xw@ubuntu:~/Linux_Everyday/3_Mar$ touch b.txt
xw@ubuntu:~/Linux_Everyday/3_Mar$ touch c.txt
xw@ubuntu:~/Linux_Everyday/3_Mar$ ls
a.txt  b.txt  c.txt  test1
xw@ubuntu:~/Linux_Everyday/3_Mar$ mv a.txt b.txt c.txt test1/
xw@ubuntu:~/Linux_Everyday/3_Mar$ ls -R
.:
test1

./test1:
a.txt  b.log  b.txt  c.txt
```
```
xw@ubuntu:~/Linux_Everyday/3_Mar$ touch a.txt b.txt c.txt
xw@ubuntu:~/Linux_Everyday/3_Mar$ ls
a.txt  b.txt  c.txt  test1
xw@ubuntu:~/Linux_Everyday/3_Mar$ mv -t test1 a.txt b.txt c.txt 
xw@ubuntu:~/Linux_Everyday/3_Mar$ ls -R
.:
test1

./test1:
a.txt  b.log  b.txt  c.txt
```
* 例4：将文件a.txt改名为b.txt，如果b.txt已存在，则询问是否覆盖。命令为mv -i a.txt b.txt
```
xw@ubuntu:~/Linux_Everyday/3_Mar$ echo "this is a.txt" >> a.txt
xw@ubuntu:~/Linux_Everyday/3_Mar$ cat a.txt 
this is a.txt
xw@ubuntu:~/Linux_Everyday/3_Mar$ echo "this is b.txt" >> b.txt
xw@ubuntu:~/Linux_Everyday/3_Mar$ cat b.txt 
this is b.txt
xw@ubuntu:~/Linux_Everyday/3_Mar$ mv -i a.txt b.txt 
mv: overwrite 'b.txt'? y
xw@ubuntu:~/Linux_Everyday/3_Mar$ ls
b.txt  test1
xw@ubuntu:~/Linux_Everyday/3_Mar$ cat b.txt 
this is a.txt
```
* 例5：将文件a.txt改名为b.txt，如果b.txt已存在，则直接覆盖。命令为mv -f a.txt b.txt
```
xw@ubuntu:~/Linux_Everyday/3_Mar$ echo "this is a.txt" >> a.txt
xw@ubuntu:~/Linux_Everyday/3_Mar$ cat a.txt 
this is a.txt
xw@ubuntu:~/Linux_Everyday/3_Mar$ echo "this is b.txt" >> b.txt
xw@ubuntu:~/Linux_Everyday/3_Mar$ cat b.txt 
this is b.txt
xw@ubuntu:~/Linux_Everyday/3_Mar$ mv -f a.txt b.txt 
xw@ubuntu:~/Linux_Everyday/3_Mar$ ls
b.txt  test1
xw@ubuntu:~/Linux_Everyday/3_Mar$ cat b.txt 
this is a.txt
```
* 例6：把test1目录移动到test2，目录中，如果test2目录不存在，则是将test1目录重命名为test2。命令为mv test1 test2
```
w@ubuntu:~/Linux_Everyday/3_Mar$ mkdir test2
xw@ubuntu:~/Linux_Everyday/3_Mar$ ls
b.txt  test1  test2
xw@ubuntu:~/Linux_Everyday/3_Mar$ mv test1 test2
xw@ubuntu:~/Linux_Everyday/3_Mar$ ls -R
.:
b.txt  test2

./test2:
test1

./test2/test1:
a.txt  b.log  b.txt  c.txt
```
* 例7：移动test2文件下所有文件到上一级目录。命令为mv * ..
```
xw@ubuntu:~/Linux_Everyday/3_Mar$ cd test2/
xw@ubuntu:~/Linux_Everyday/3_Mar/test2$ mv * ..
xw@ubuntu:~/Linux_Everyday/3_Mar/test2$ ls
xw@ubuntu:~/Linux_Everyday/3_Mar/test2$ cd ..
xw@ubuntu:~/Linux_Everyday/3_Mar$ ls 
b.txt  test1  test2
xw@ubuntu:~/Linux_Everyday/3_Mar$ ls -R
.:
b.txt  test1  test2

./test1:
a.txt  b.log  b.txt  c.txt

./test2:
```
* 例8：当用a.txt对b.txt进行覆盖前，做一个备份。命令为mv -b a.txt b.txt
```
xw@ubuntu:~/Linux_Everyday/3_Mar$ echo "this is a.txt" >> a.txt
xw@ubuntu:~/Linux_Everyday/3_Mar$ cat a.txt 
this is a.txt
xw@ubuntu:~/Linux_Everyday/3_Mar$ echo "this is b.txt" >> b.txt
xw@ubuntu:~/Linux_Everyday/3_Mar$ cat b.txt 
this is b.txt
xw@ubuntu:~/Linux_Everyday/3_Mar$ mv -b a.txt b.txt 
xw@ubuntu:~/Linux_Everyday/3_Mar$ ls
b.txt  b.txt~  test2
xw@ubuntu:~/Linux_Everyday/3_Mar$ cat b.txt
this is a.txt
xw@ubuntu:~/Linux_Everyday/3_Mar$ cat b.txt~
this is b.txt
```
#### 说明
```
说明：

-b 不接受参数，mv会去读取环境变量VERSION_CONTROL来作为备份策略。

--backup该选项指定如果目标文件存在时的动作，共有四种备份策略：
1.CONTROL=none或off : 不备份。   
2.CONTROL=numbered或t：数字编号的备份    
3.CONTROL=existing或nil：如果存在以数字编号的备份，则继续编号备份m+1...n：
执行mv操作前已存在以数字编号的文件log2.txt.~1~，那么再次执行将产生log2.txt~2~，以次类推。如果之前没有以数字编号的文件，则使用下面讲到的简单备份。   
4.CONTROL=simple或never：使用简单备份：在被覆盖前进行了简单备份，简单备份只能有一份，再次被覆盖时，简单备份也会被覆盖。
```
