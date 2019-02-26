# cd命令<br>

Linux cd 命令可以说是Linux中最基本的命令语句，其他的命令语句要进行操作，都是建立在使用 cd 命令上的,所以，学习Linux 常用命令，首先就要学好 cd 命令的使用方法技巧。   

1.命令格式：cd [dirName]   
```
其中 dirName 表示法可为绝对路径或相对路径。若目录名称省略，则变换至使用者的 home 目录 (也就是刚 login 时所在的目录)    
另外，"~" 也表示为 home 目录 的意思，"." 则是表示目前所在的目录，".." 则表示目前目录位置的上一层目录。
```
2.命令功能：切换当前目录至dirName   
3.常用范例:   
* 例1：跳入test目录,命令为cd test
```
[root@/root/linuxdaxue.com]#cd testDir/
[root@/root/linuxdaxue.com/testDir]#ls
file1  file2  file3
```
* 例2：跳入上层目录,命令为cd ..
```
[root@/root/linuxdaxue.com/testDir]#cd ..
[root@/root/linuxdaxue.com]#ls
testDir
```
* 例3：跳入用户主目录,命令为cd 或者 cd ~
```
[root@/root/linuxdaxue.com/testDir]#ls
file1  file2  file3
[root@/root/linuxdaxue.com/testDir]#cd ~/
[root@/root]#pwd
/root
```
* 例4: 跳入上次使用目录,命令为cd -
```
[root@/root]#pwd
/root
[root@/root]#cd -
/root/linuxdaxue.com/testDir
[root@/root/linuxdaxue.com/testDir]#
```
* 例5：使用环境变量，命令为cd $环境变量
```
[root@/root]#cd $TEST_PATH
[root@/root/linuxdaxue.com/testDir]#ls
file1  file2  file3
```
