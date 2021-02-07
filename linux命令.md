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
##### 1.1.4 列出指定目录的内容:ls <directory>
![](pictures\\ls列出指定目录下的文件和子目录.png)
##### 1.1.5 列出多个目录下的内容:ls <direcotory1> <direcotory2> ...
![](pictures\\ls列出多个目录下的文件和子目录.png) 
##### 1.1.6 输出目录详细信息:ls -l <directory>
##### 1.1.7 以人类可读模式输出目录详细信息:ls -lh <directory>
![](pictures\\ls-lh以人类可读模式输出详细信息.png) 
##### 1.1.7 以人类可读模式输出并按照文件大小排序:ls -lSh <directory>
![](pictures\\ls-lSh以人类可读模式输出并按照文件大小排序.png) 
#### 1.2 命令的基本模式  
command -options arguments  
ls的arguments是"文件或者目录"  
option可以是'-'跟着一个单个字母,比如ls -l,或者是'--'跟着一个完整的单词,比如ls --reverse  
linux下的opition是大小写敏感的  
#### 1.3 切换工作目录:cd
##### 1.3.1 切换到上一层:cd ..
##### 1.3.2 切换到当前目录:cd .
##### 1.3.3 切换到指定目录:cd <directory>
##### 1.3.4 切换到home:cd ~
##### 1.3.5 切换到根目录:cd /
#### 1.4 打印当前目录的完全路径:pwd
#### 1.5 列出文件/目录所占用的磁盘空间:du <option> <directory/file>
##### 1.5.1 列出下一级所有目录和文件的大小:du
![](pictures\\du列出下一级所有目录和文件的大小.png) 
##### 1.5.2 显示指定文件或目录的大小:du <directory1/file1>
![](pictures\\du显示指定目录的大小.png) 
![](pictures\\du显示指定文件的大小.png) 
##### 1.5.3 显示指定的多个文件或目录的大小:du <directory1/file1> <directory2/file2> ...
![](pictures\\du显示多个文件的大小.png) 
##### 1.5.4 只显示目录内文件和目录总和大小:du -s
![](pictures\\du只显示总和.png) 
##### 1.5.5 以可读形式显示总和:du -sh
![](pictures\\du以可读形式显示总和.png) 
##### 1.5.6 显示所有文件的大小:du -a
![](pictures\\du所有文件的大小.png) 
[du命令参考](https://www.cnblogs.com/peida/archive/2012/12/10/2810755.html)
##### 1.5.7 显示多个文件大小并统计总和:du -c <directory1/file1> <directory2/file2> ...
![](pictures\\du显示多个文件的大小并统计总和.png) 
##### 1.5.8 按照占用空间大小排序:du|sort -nr|more
![](pictures\\du按照空间大小排序.png) 
#### 1.6 文件系统的磁盘空间占用情况:df <option>
##### 1.6.1 全部文件系统列表:df -a
##### 1.6.2 方便阅读方式显示:df -h; 1k = 1024
##### 1.6.3 方便阅读方式显示:df -H; 1k = 1000
##### 1.6.4 显示inode信息:df -i
##### 1.6.5 只显示选定文件系统的磁盘信息:df -t <fileSystemType> 
##### 1.6.6 不显示选定文件系统的磁盘信息:df -x <fileSystemType>
### 2.文件系统操作命令
mkdir、cp、mv、rm、touch
#### 2.1 创建目录:mkdir <directory>
![](pictures\\mkdir创建目录.png) 
#### 2.2 复制目录或文件:cp
##### 2.2.1 复制文件:cp <old_file> <new_file>
![](pictures\\cp复制文件.png) 
##### 2.2.2 复制目录下的所有文件:cp -r <old_directory> <new_directory>
![](pictures\\cp复制目录.png) 
##### 2.2.3 复制目录下的所有文件,并保留链接、文件属性:cp -a <old_directory> <new_directory>
#### 2.3 移动文件或目录,重命名:mv <option> <directory/file>
##### 2.3.1 重命名指定文件的名字:mv <path/old_file_name> <path/new_file_name>
![](pictures\\mv修改文件名.png) 
##### 2.3.2 移动目录:mv <path1/directory> <path2/directory>
把/home/directory1移动到home/directory2下
![](pictures\\mv修改文件名.png) 
##### 2.3.3 移动文件并重命名:mv <path1/old_file_name> <path2/new_file_name>
![](pictures\\mv移动目录.png) 
##### 2.3.4 要移动的目的目录存在和源文件或目录同名文件或目录时
-b: 当目标文件或目录存在时，在执行覆盖前，会为其创建一个备份    
-i: 如果指定移动的源目录或文件与目标的目录或文件同名，则会先询问是否覆盖旧文件，输入 y 表示直接覆盖，输入 n 表示取消该操作  
-f: 如果指定移动的源目录或文件与目标的目录或文件同名，不会询问，直接覆盖旧文件  
-n: 不要覆盖任何已存在的文件或目录  
-u：当源文件比目标文件新或者目标文件不存在时，才执行移动操作  
#### 2.4 删除文件或目录:rm <option> <file/directory>
#####  2.4.1 删除文件带询问:rm <file>
![](pictures\\rm删除文件带询问.png) 
#####  2.4.2 强行删除文件不带询问:rm -f <file>
![](pictures\\rm直接删除文件不带询问.png) 
#####  2.4.3 删除目录带询问:rm -r <directory>
![](pictures\\rm删除目录带询问.png) 
#####  2.4.4 强行删除目录不带询问:rm -rf <directory>
#### 2.5 更新文件时间戳或创建空文件:touch <file>
##### 2.5.1 更新文件时间戳:touch <old_file>
![](pictures\\touch对已有的文件修改时间戳.png) 
##### 2.5.2 创建空文件:touch <new_file>
![](pictures\\touch创建新的空文件.png) 
[df命令参考](https://www.cnblogs.com/peida/archive/2012/12/07/2806483.html)
### 3.文件内容命令
cat、head/tail、more/less、wc、grep
#### 3.1 查看整个文本内容:cat
不适合很大的文件
![](pictures\\cat打印所有文件内容.png) 
#### 3.2 查看头部部分内容
默认打印头部10行:head <file>
![](pictures\\head默认打印10行.png) 
从头部指定打印行数:head -<number> <file>
![](pictures\\head指定打印行数.png) 
#### 3.3 查看尾部部分内容
默认打印尾部10行:tail <file>
![](pictures\\tail从末尾打印默认10行.png) 
从尾部指定打印行数:tail -<number> <file>
![](pictures\\tail从末尾指定打印行数.png) 
#### 3.4.1翻页查看大文件:more
查看下一页:空格(space)  
查看上一页:b   
查找字符:/<字符>;从该字串前两行之后开始显示  
注意:more在启动时就加载整个文件  
#### 3.4.2翻页查看大文件:less
类似于more,但启动时不加载整个文件
#### 3.5 统计文件的Byte数、字数、或是列数:wc <option> <file>
wc只能用来统计英语文本:因为区分一个单词是认为其左右两端都是空格  
![](pictures\\wc命令输出详解.png) 
##### 3.5.1只想统计文本某一项指标
-c或--bytes或--chars 只显示Bytes数  
-l或--lines 显示行数  
-w或--words 只显示字数  
![](pictures\\wc只统计文本的某一项指标.png) 
#### 3.6 搜索文件中的内容:grep <option> <file>

### 4.文件编辑命令和工具
vim、cut、tr、sort、awk  
特殊符号:|、||、&、&&、>、>>
### 二.如何将windows上的文件上传到linux服务器  
#### 1.查看linux发行版:lsb_release -a  
![](pictures\\lsb_release查看linux发行版.png)  
centos是redhat的社区版,所以使用yum命令来安装和查看ftp服务  
#### 2.yum搜索是否安装了ftp:yum list installed | grep ftp  
![](pictures\\yum搜索安装包是否有需要的软件.png)   
#### 3.如果没有安装,搜索可用的安装包:yum list | grep ftp  
![](pictures\\yum搜索可用的安装包.png)   
#### 4.安装:yum install vsftpd  
#### 5.开启ftp服务:service vsftpd start  
#### 6.查看是否开启成功:netstat -nltp | grep 21  
![](pictures\\查看服务是否开启成功.png)   
#### 7.上传文件  
(1)Filezilla软件  
(2)windows的ftp命令行命令?