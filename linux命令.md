## 一.常用linxu命令 
### 1.查看文件系统命令
ls、cd、pwd、du、df
#### 1.1 输出目录或文件的内容:ls
##### 1.1.1 ls -l输出内容解释 
![](pictures\\ls命令输出图解.png)
##### 1.1.2 文件权限
例如:-rw-r--r--, 9个字符
第一个字符表示类型:-表示文件,d表示目录  
第2-4个字符表示拥有者权限     
第5-7个字符表示拥有group权限    
第8-10个字符表示其他人权限   
##### 1.1.3 列出当前目录的内容:ls
![](pictures\\ls列出当前目录下的文件和子目录.png)
##### 1.1.4 列出指定目录的内容:ls [directory]
![](pictures\\ls列出指定目录下的文件和子目录.png)
##### 1.1.5 列出多个目录下的内容:ls [direcotory1] [direcotory2] ...
![](pictures\\ls列出多个目录下的文件和子目录.png) 
##### 1.1.6 输出目录详细信息:ls -l [directory]
##### 1.1.7 以人类可读模式输出目录详细信息:ls -lh [directory]
![](pictures\\ls-lh以人类可读模式输出详细信息.png) 
##### 1.1.7 以人类可读模式输出并按照文件大小排序:ls -lSh [directory]
![](pictures\\ls-lSh以人类可读模式输出并按照文件大小排序.png) 
#### 1.2 命令的基本模式  
command -options arguments  
ls的arguments是"文件或者目录"  
option可以是'-'跟着一个单个字母,比如ls -l,或者是'--'跟着一个完整的单词,比如ls --reverse  
linux下的opition是大小写敏感的  
#### 1.3 切换工作目录:cd
##### 1.3.1 切换到上一层:cd ..
##### 1.3.2 切换到当前目录:cd .
##### 1.3.3 切换到指定目录:cd [directory]
##### 1.3.4 切换到home:cd ~
##### 1.3.5 切换到根目录:cd /
#### 1.4 打印当前目录的完全路径:pwd
#### 1.5 列出文件/目录所占用的磁盘空间:du [option] [directory/file]
##### 1.5.1 列出下一级所有目录和文件的大小:du
![](pictures\\du列出下一级所有目录和文件的大小.png) 
##### 1.5.2 显示指定文件或目录的大小:du [directory1/file1]
![](pictures\\du显示指定目录的大小.png) 
![](pictures\\du显示指定文件的大小.png) 
##### 1.5.3 显示指定的多个文件或目录的大小:du [directory1/file1] [directory2/file2] ...
![](pictures\\du显示多个文件的大小.png) 
##### 1.5.4 只显示目录内文件和目录总和大小:du -s
![](pictures\\du只显示总和.png) 
##### 1.5.5 以可读形式显示总和:du -sh
![](pictures\\du以可读形式显示总和.png) 
##### 1.5.6 显示所有文件的大小:du -a
![](pictures\\du所有文件的大小.png) 
[du命令参考](https://www.cnblogs.com/peida/archive/2012/12/10/2810755.html)
##### 1.5.7 显示多个文件大小并统计总和:du -c [directory1/file1] [directory2/file2] ...
![](pictures\\du显示多个文件的大小并统计总和.png) 
##### 1.5.8 按照占用空间大小排序:du|sort -nr|more
![](pictures\\du按照空间大小排序.png) 
#### 1.6 文件系统的磁盘空间占用情况:df [option]
##### 1.6.1 全部文件系统列表:df -a
##### 1.6.2 方便阅读方式显示:df -h; 1k = 1024
##### 1.6.3 方便阅读方式显示:df -H; 1k = 1000
##### 1.6.4 显示inode信息:df -i
##### 1.6.5 只显示选定文件系统的磁盘信息:df -t [fileSystemType] 
##### 1.6.6 不显示选定文件系统的磁盘信息:df -x [fileSystemType]
### 2.文件系统操作命令
mkdir、cp、mv、rm、touch
#### 2.1 创建目录:mkdir [directory]
![](pictures\\mkdir创建目录.png) 
#### 2.2 复制目录或文件:cp
##### 2.2.1 复制文件:cp [old-file] [new-file]
![](pictures\\cp复制文件.png) 
##### 2.2.2 复制目录下的所有文件:cp -r [old-directory] [new-directory]
![](pictures\\cp复制目录.png) 
##### 2.2.3 复制目录下的所有文件,并保留链接、文件属性:cp -a [old-directory] [new-directory]
#### 2.3 移动文件或目录,重命名:mv [option] [directory/file]
##### 2.3.1 重命名指定文件的名字:mv [path/old-file_name] [path/new-file_name]
![](pictures\\mv修改文件名.png) 
##### 2.3.2 移动目录:mv [path1/directory] [path2/directory]
把/home/directory1移动到home/directory2下
![](pictures\\mv修改文件名.png) 
##### 2.3.3 移动文件并重命名:mv [path1/old-file_name] [path2/new-file_name]
![](pictures\\mv移动目录.png) 
##### 2.3.4 要移动的目的目录存在和源文件或目录同名文件或目录时
-b: 当目标文件或目录存在时，在执行覆盖前，会为其创建一个备份    
-i: 如果指定移动的源目录或文件与目标的目录或文件同名，则会先询问是否覆盖旧文件，输入 y 表示直接覆盖，输入 n 表示取消该操作  
-f: 如果指定移动的源目录或文件与目标的目录或文件同名，不会询问，直接覆盖旧文件  
-n: 不要覆盖任何已存在的文件或目录  
-u：当源文件比目标文件新或者目标文件不存在时，才执行移动操作  
#### 2.4 删除文件或目录:rm [option] [file/directory]
#####  2.4.1 删除文件带询问:rm [file]
![](pictures\\rm删除文件带询问.png) 
#####  2.4.2 强行删除文件不带询问:rm -f [file]
![](pictures\\rm直接删除文件不带询问.png) 
#####  2.4.3 删除目录带询问:rm -r [directory]
![](pictures\\rm删除目录带询问.png) 
#####  2.4.4 强行删除目录不带询问:rm -rf [directory]
#### 2.5 更新文件时间戳或创建空文件:touch [file]
##### 2.5.1 更新文件时间戳:touch [old-file]
![](pictures\\touch对已有的文件修改时间戳.png) 
##### 2.5.2 创建空文件:touch [new-file]
![](pictures\\touch创建新的空文件.png) 
[df命令参考](https://www.cnblogs.com/peida/archive/2012/12/07/2806483.html)
### 3.文件内容命令
cat、head/tail、more/less、wc、grep
#### 3.1 查看整个文本内容:cat [file]
不适合很大的文件
![](pictures\\cat打印所有文件内容.png) 
#### 3.2 查看头部部分内容:tail -[number] [file]
默认打印头部10行:head [file]
![](pictures\\head默认打印10行.png) 
从头部指定打印行数:head -[number] [file]
![](pictures\\head指定打印行数.png) 
#### 3.3 查看尾部部分内容:tail -[number] [file]
默认打印尾部10行:tail [file]
![](pictures\\tail从末尾打印默认10行.png) 
从尾部指定打印行数:tail -[number] [file]
![](pictures\\tail从末尾指定打印行数.png) 
#### 3.4.1翻页查看大文件:more [file]
查看下一页:空格(space)  
查看上一页:b   
查找字符:/[字符];从该字串前两行之后开始显示  
注意:more在启动时就加载整个文件  
#### 3.4.2翻页查看大文件:less [file]
类似于more,但启动时不加载整个文件
#### 3.5 统计文件的Byte数、字数、或是列数:wc [option] [file]
wc只能用来统计英语文本:因为区分一个单词是认为其左右两端都是空格  
![](pictures\\wc命令输出详解.png) 
##### 3.5.1只想统计文本某一项指标
-c或--bytes或--chars 只显示Bytes数  
-l或--lines 显示行数  
-w或--words 只显示字数  
![](pictures\\wc只统计文本的某一项指标.png) 
#### 3.6 搜索文件中的内容:grep [regex] [file]
##### 3.6.1 搜索某个文件中符合正则的所有行

##### 3.6.2 搜索文件中的内容:grep [option] [file]
#### 3.7 查找文件:find [path] [option] [expression]

在-[opiton]之前的为path,之后的为expression
##### 3.7.1 在特定路径下查找特定名字的文件:find [path] -name [expression]
![](pictures\\find全局搜索特定名字的文件.png) 
find查找名字以特定开头和特定结尾的文件
![](pictures\\find查找名字以特定开头和特定结尾的文件.png)  
全局查找:find / [option] [expression]
当前目录查找:find . [option] [expression]

### 4.文件编辑命令和工具
vim、cut、tr、sort、awk  
特殊符号:|、||、&、&&、]、]]
#### 4.1文本编辑: vim
阅读模式:esc键  
插入模式:esc+i   
命令模式:esc+:  
配置文件:.vimrc  
colorscheme darkblue  
set tabstop=4  
set shiftwidth=4  
set smarttab  
set expandtab  
##### 4.2.1文本搜索关键字
切换到阅读模式  
使用/[keyword]命令搜索    
从文档当前位置向下查找关键字，按n键查找关键字下一个位置  
![](pictures\\vim搜索关键字.png) 
?[keyword]
从文档当前位置向上查找关键字，按n键向上查找关键字  
##### 4.2.2文本替换关键字
切换到阅读模式,使用:s 命令来替换字符串    
替换当前行第一个old_string为new_string:":s/[old_string]/[new_string]"
替换当前行所有old_string为new_string":s/[old_string]/[new_string]/g "  
替换从第x行到第y行的第一个old_string为new_string: ":x,ys/[old_string]/[new_string]"  
替换从第x行到第y行的所有old_string为new_string: ":x,ys/[old_string]/[new_string]/g" 
#### 4.3 对文本分片并输出: cut [option] [arguments] [file]
##### 4.3.1 对文本的每一行抽取指定"字节"位置的内容并输出: cut -b [arguments] [file]
b是byte  
抽取每一行的第1,3,5字节并输出:cut -b 1,3,5 [file]   
抽取每一行的第3到最后一个字节并输出:cut -b 1- [file]   
抽取每一行的第一个到第7字节并输出:cut -b -7 [file]   
注意:tab和space视为一个字节   
![](pictures\\cut截取文件每行的指定字节位置内容.png)  
##### 4.3.2 对文本的每一行抽取指定"字符"位置的内容并输出: $cut -c [arguments] [file]$
>适合column为固定长度

抽取每一行的第1,3,5字符并输出:cut -c 1,3,5 [file]  
抽取每一行的第3到最后一个字符并输出:cut -c 1- [file]  
抽取每一行的第一个到第7字符并输出:cut -c -7 [file] 
![](pictures\\cut对每行按指定字符位置截取并输出.png)  
##### 4.3.3 对文本的每一行抽取指定"filed"位置的内容并输出: cut -d $[delimiter] -f [arguments] [file]
>适合column不是固定长度,-d 设置分隔符,默认使用tabu作为分隔符

抽取每一行的第1,3 field并输出:cut -d " " -f 1,3 [file]  
抽取每一行的第1到第5 field并输出:cut -d " " -f 1-5 [file]  
抽取每一行的第二到最后一个 field并输出:cut -d " "-f 2- [file] 
抽取每一行的第一个到第7 field并输出:cut -d " "-f -7 [file]
![](pictures\\cut对每行按指定filed截取并输出.png)  



[cut命令参考](https://www.geeksforgeeks.org/cut-command-linux-examples/)
#### 4.3处理字符串: tr
[tr命令参考](https://www.geeksforgeeks.org/tr-command-in-unix-linux-with-examples/)
#### 4.4文本内容排序: sort [opiton] 
>对文件内容进行排序,不会修改源文件,默认将源文件内容排序后输出到屏幕

##### 4.4.1 默认排序规则
(1)数字在字母前面
(2)字母按照字母表从小到大排序,同样的字母,小写在大写前面
![](pictures\\sort基本排序规则.png) 
##### 4.4.2 排序内容重定向:sort -o [redirect-file] [file] 等价于 sort [file] > [redirect-file]
![](pictures\\sort排序内容重定向.png) 
##### 4.4.3 逆序排序:sort -r [file]
![](pictures\\sort排序逆序输出.png) 
##### 4.4.4 对数字排序:sort -n [file]
sort [file]只能对0-9的数字进行正确排序,而对更大范围的数字排序需要使用-n   
对数字逆序排序:sort -nr [file]   
![](pictures\\sort对更大范围数字排序.png) 
![](pictures\\sort对数字逆序排序.png) 
##### 4.4.5 指定使用一行中的某一列来排序: sort -k [number] [file]
![](pictures\\sort指定一行的某一列排序.png) 
##### 4.4.6 检查一个文件是否已经排序:sort -c [file]
如果file已经排序,则不会有任何输出  
![](pictures\\sort检查文件是否有序.png) 
##### 4.4.7 移除重复项的排序:sort -u [file]
![](pictures\\sort移除重复项排序.png) 
##### 4.4.8 按照月份来排序:sort -M [file]
>如果文件中包含月份,可以按照月份来排序  
![](pictures\\sort按照月份来排序.png)  
[sort命令参考](https://www.geeksforgeeks.org/sort-command-linuxunix-examples/)
#### 4.5文本编辑: awk
[awk命令参考](https://www.geeksforgeeks.org/awk-command-unixlinux-examples/)
#### 4.6命令输出写入文本
直接覆盖或者创建:>  
追加或者创建:>>
#### 4.7 一个命令的输出作为另一个命令的输入:|
#### 4.8 其他命令
&:命令在后台运行
||: 第一个命令失败时,第二个命令才会运行
&&: 第一个命令执行成功时,第二个命令才会运行
#### 问题:如何将windows上的文件上传到linux服务器?
##### 1.查看linux发行版:lsb_release -a  
![](pictures\\lsb_release查看linux发行版.png)  
centos是redhat的社区版,所以使用yum命令来安装和查看ftp服务  
##### 2.yum搜索是否安装了ftp:yum list installed | grep ftp  
![](pictures\\yum搜索安装包是否有需要的软件.png)   
##### 3.如果没有安装,搜索可用的安装包:yum list | grep ftp  
![](pictures\\yum搜索可用的安装包.png)   
##### 4.安装:yum install vsftpd  
##### 5.开启ftp服务:service vsftpd start  
##### 6.查看是否开启成功:netstat -nltp | grep 21  
![](pictures\\查看服务是否开启成功.png)   
##### 7.上传文件  
(1)Filezilla软件  
(2)windows的ftp命令行命令?

##### 8.su和sudo
su:  
切换用户  
临时用户bofan切换到root用户:su root  
通过su root切换为root后拥有root的一切权限  
切换root用户,需要输入root用户的密码
sudo:sudo [command],临时提升一般command的权限,首先需要在/etc/sudoers给用户加上权限
/etc/sudoers只有root用户才可以编辑  
如何编辑/etc/sudoers?
su root  
visudo(不要使用vi /etc/sudoers,visudo是安全的编辑/etc/sudoers的命令) 
/etc/sudoers文件解释
##### 9.curl命令


