# touch命令

touch命令是用来修改文件的时间戳，或者创建新的文件。    

1.命令格式：touch [option]... FILE...   

2.命令功能：用**当前时间**来更改文件或目录的日期时间，包括存取时间和修改时间。    

3.常用参数：   
　　-a:只改变存取时间。相当于--time=atime,--time=access,--time=use。   
　　-c,--no-create:不创建任何文件。   
　　-d,--date=STRING:使用指定的日期时间(STRING)，而不是当前时间。     
　　-m:只改变修改时间。相当于--time=mtime,--time=modify。   
　　-r,--reference=FILE:使用FILE的时间，而不是当前时间。   
　　-t:使用指定的日期，而不是当前时间。   
4.常用范例：   
* 例1：创建一个名字为a.txt的文件。命令为touch a.txt。
```
xw@ubuntu:~/Linux_Everyday/Mar/4_Mar$ touch a.txt
xw@ubuntu:~/Linux_Everyday/Mar/4_Mar$ ls -l
total 0
-rw-r--r-- 1 xw xw 0 Mar  4 05:04 a.txt
```
* 例2：更改c.txt的时间和b.txt的时间戳相同。命令为touch -r b.txt c.txt或者touch --reference=b.txt c.txt
```
xw@ubuntu:~/Linux_Everyday/Mar/4_Mar$ touch c.txt
xw@ubuntu:~/Linux_Everyday/Mar/4_Mar$ ls -l
total 0
-rw-r--r-- 1 xw xw 0 Mar  4 05:07 a.txt
-rw-r--r-- 1 xw xw 0 Mar  4 05:09 b.txt
-rw-r--r-- 1 xw xw 0 Mar  4 05:10 c.txt
xw@ubuntu:~/Linux_Everyday/Mar/4_Mar$ touch -r b.txt c.txt 
xw@ubuntu:~/Linux_Everyday/Mar/4_Mar$ ls -l
total 0
-rw-r--r-- 1 xw xw 0 Mar  4 05:07 a.txt
-rw-r--r-- 1 xw xw 0 Mar  4 05:09 b.txt
-rw-r--r-- 1 xw xw 0 Mar  4 05:09 c.txt
```
```
xw@ubuntu:~/Linux_Everyday/Mar/4_Mar$ touch c.txt
xw@ubuntu:~/Linux_Everyday/Mar/4_Mar$ ls -l
total 0
-rw-r--r-- 1 xw xw 0 Mar  4 05:07 a.txt
-rw-r--r-- 1 xw xw 0 Mar  4 05:09 b.txt
-rw-r--r-- 1 xw xw 0 Mar  4 05:11 c.txt
xw@ubuntu:~/Linux_Everyday/Mar/4_Mar$ touch --reference=b.txt c.txt 
xw@ubuntu:~/Linux_Everyday/Mar/4_Mar$ ls -l
total 0
-rw-r--r-- 1 xw xw 0 Mar  4 05:07 a.txt
-rw-r--r-- 1 xw xw 0 Mar  4 05:09 b.txt
-rw-r--r-- 1 xw xw 0 Mar  4 05:09 c.txt
```
* 例3：利用指定时间修改文件的时间戳。命令为touch -t 201901012234.50 a.txt
```
xw@ubuntu:~/Linux_Everyday/Mar/4_Mar$ ls -l
total 0
-rw-r--r-- 1 xw xw 0 Mar  4 05:07 a.txt
-rw-r--r-- 1 xw xw 0 Mar  4 05:09 b.txt
-rw-r--r-- 1 xw xw 0 Mar  4 05:09 c.txt
xw@ubuntu:~/Linux_Everyday/Mar/4_Mar$ touch -t 201901012234.50 a.txt 
xw@ubuntu:~/Linux_Everyday/Mar/4_Mar$ ls -l
total 0
-rw-r--r-- 1 xw xw 0 Jan  1 22:34 a.txt
-rw-r--r-- 1 xw xw 0 Mar  4 05:09 b.txt
-rw-r--r-- 1 xw xw 0 Mar  4 05:09 c.txt
```
#### 说明
```
-t  time 使用指定的时间值 time 作为指定文件相应时间戳记的新值．此处的 time规定为如下形式的十进制数:      
 [[CC]YY]MMDDhhmm[.SS]     
 这里，CC为年数中的前两位，即”世纪数”；YY为年数的后两位，即某世纪中的年数．如果不给出CC的值，则touch将把年数CCYY限定在1969--2068之内。  
 MM为月数，DD为天数，hh 为小时数(几点)，mm为分钟数，SS为秒数．此处秒的设定范围是0--61，这样可以处理闰秒。  
 这些数字组成的时间是环境变量TZ指定的时区中的一个时间．由于系统的限制，早于1970年1月1日的时间是错误的。
```

