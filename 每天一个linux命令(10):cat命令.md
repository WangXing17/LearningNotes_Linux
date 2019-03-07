# cat命令   

cat是concatenate files and print on the standard output.意思是连接文件并打印标准输出。经常与重定向符号配合使用。   

1.命令格式：cat [option]... [file]...

2.命令功能：连接文件并标准输出。可以没有file参数，或者file参数是-时，读取标准输入。   

3.常用参数：   
　　-A,--show-all:等价于-vET。    
　　-b,--number-nonblank：对非空输出行编号。使-n失效。    
　　-e:等价于-vE。    
　　-E,--show-ends:在每一行的末尾输出$。    
　　-n,--number: 为所有行编号。    
　　-s,--squeeze-blank:有连续两行以上的空白行，就用一行代替。    
　　-t：等价于-vT。    
　　-T,--show-tabs：将TAB用^I代替显示。   
　　-v,--show-nonprinting:使用 ^ 和 M- 符号，除了 LFD 和 TAB 之外。   
4.常用范例：   
* 例1：读取标准输入并标准输出。命令为cat或者cat -。
```
xw@ubuntu:~/Linux_Everyday/Mar/7_Mar$ cat 
a
a
b
b
c
c
d
d
^C
xw@ubuntu:~/Linux_Everyday/Mar/7_Mar$ 
```
* 例2：连接多个文件的内容(带行号)显示在屏幕上。命令为cat -n a.txt b.txt
```
xw@ubuntu:~/Linux_Everyday/Mar/7_Mar$ cat -n a.txt b.txt 
     1	This is a.txt!
     2		hello,i am xw.
     3	what your name?
     4	
     5	
     6	thank you 
     7	
     8	
     9	haha
    10	this is b.txt!
    11		hello,my name is xw
    12	
    13	
    14	what is your name?
    15	how are you 
    16	
    17	
    18	haha
```
* 例3：连接多个文件的内容(带行号，但是空白行不算行号)显示在屏幕上。命令为cat -b a.txt b.txt
```
xw@ubuntu:~/Linux_Everyday/Mar/7_Mar$ cat -b a.txt b.txt 
     1	This is a.txt!
     2		hello,i am xw.
     3	what your name?


     4	thank you 


     5	haha
     6	this is b.txt!
     7		hello,my name is xw


     8	what is your name?
     9	how are you 


    10	haha
```
* 例4：把a.txt的内容追加到c.txt文件中。命令为cat -b a.txt >> c.txt
```
xw@ubuntu:~/Linux_Everyday/Mar/7_Mar$ cat c.txt 
this is c.txt
xw@ubuntu:~/Linux_Everyday/Mar/7_Mar$ cat -b a.txt >> c.txt 
xw@ubuntu:~/Linux_Everyday/Mar/7_Mar$ cat -n c.txt 
     1	this is c.txt
     2	     1	This is a.txt!
     3	     2		hello,i am xw.
     4	     3	what your name?
     5	
     6	
     7	     4	thank you 
     8	
     9	
    10	     5	haha
```
* 例5：将标准的输入放入到d.txt文件中。命令是cat >> d.txt或者 cat - >> d.txt
```
xw@ubuntu:~/Linux_Everyday/Mar/7_Mar$ cat - >> d.txt
this is d.txt 
hello
	haha
^C
xw@ubuntu:~/Linux_Everyday/Mar/7_Mar$ cat d.txt 
this is d.txt
hello
	haha
```

### 补充    
linux中shell的here document用法   
什么是Here Documen：    
Here Document 是在Linux Shell 中的一种特殊的重定向方式，它的基本的形式如下    
```
cmd << delimiter
  Here Document Content
delimiter
```
它的作用就是将两个 delimiter 之间的内容(Here Document Content 部分) 传递给cmd 作为输入参数。    
比如在终端中输入cat << EOF ，系统会提示继续进行输入，输入多行信息再输入EOF，中间输入的信息将会显示在屏幕上。如下   
```
xw@ubuntu:~/Linux_Everyday/Mar/7_Mar$ cat << EOF
> a
> b
> c
> EOF
a
b
c
```
#### 注：    
EOF 只是一个标识而已，可以替换成任意的合法字符   
作为结尾的delimiter一定要顶格写，前面不能有任何字符    
作为结尾的delimiter后面也不能有任何的字符（包括空格）   
作为起始的delimiter前后的空格会被省略掉    
