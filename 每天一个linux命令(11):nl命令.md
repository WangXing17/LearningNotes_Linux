# nl命令    

nl是number lines of files的缩写，意思是文件的行数。   

1.命令格式：nl [option]... [file]...   

2.命令功能：带有行号的标准输出每个文件的内容。   

3.常用参数：   
　　-b：指定行号指定的方式，主要有两种：   
　　　-b a ：表示不论是否为空行，也同样列出行号(类似 cat -n)  
　　　-b t ：如果有空行，空的那一行不要列出行号(默认值)   
　　-n：列出行号表示的方法，主要有三种：    
　　　-n ln ：行号在萤幕的最左方显示   
　　　-n rn ：行号在自己栏位的最右方显示，且不加 0   
　　　-n rz ：行号在自己栏位的最右方显示，且加 0    
　　-w：行号栏位的占用的位数。    
4.常用范例：   
* 例1：无论空行与否都添加行号。命令为nl -b a.txt   
```
xw@ubuntu:~/Linux_Everyday/Mar/8_Mar$ nl -b a a.txt 
     1	This is a.txt!
     2		hello,i am xw.
     3	what your name?
     4	
     5	
     6	thank you 
     7	
     8	
     9	haha
```
* 例2：空号不显示行号。命令为nl -b t a.txt   
```
xw@ubuntu:~/Linux_Everyday/Mar/8_Mar$ nl -b t a.txt 
     1	This is a.txt!
     2		hello,i am xw.
     3	what your name?
       
       
     4	thank you 
       
       
     5	haha
```
* 例3：行号在行号栏的左边显示。命令为nl -n ln a.txt   
```
xw@ubuntu:~/Linux_Everyday/Mar/8_Mar$ nl -n ln a.txt 
1     	This is a.txt!
2     		hello,i am xw.
3     	what your name?
       
       
4     	thank you 
       
       
5     	haha
```
* 例4：行号在行号栏的右边显示且不补0。命令为nl -n rn a.txt   
```
xw@ubuntu:~/Linux_Everyday/Mar/8_Mar$ nl -n rn a.txt 
     1	This is a.txt!
     2		hello,i am xw.
     3	what your name?
       
       
     4	thank you 
       
       
     5	haha
```
* 例5：行号在行号栏的右边显示且补0。命令为nl -n rn a.txt      
```
xw@ubuntu:~/Linux_Everyday/Mar/8_Mar$ nl -n rz a.txt 
000001	This is a.txt!
000002		hello,i am xw.
000003	what your name?
       
       
000004	thank you 
       
       
000005	haha
```
* 例6：行号在行号栏的右边显示且补0且控制行号栏位数为3。命令为nl -n rn -w 3 a.txt  
```
001	This is a.txt!
002		hello,i am xw.
003	what your name?
    
    
004	thank you 
    
    
005	haha
```
