vmware workstation 16 player免费使用
下载centos 7 iso,使用阿里云mirror更快:http://mirrors.aliyun.com/centos/7/isos/x86_64/
在vm下安装centos 7.
问题:刚安装完centos 7的vm下使用centos7，字体太小了,需要改大字体,首先安装vm tools
安装vm tools:https://blog.csdn.net/Enochzhu/article/details/103566748
https://youzipi.blog.csdn.net/article/details/23049271?utm_medium=distribute.pc_relevant.none-task-blog-BlogCommendFromMachineLearnPai2-1.control&depth_1-utm_source=distribute.pc_relevant.none-task-blog-BlogCommendFromMachineLearnPai2-1.control
安装vm tools
(1)linux.iso解压vmware-tools-distrib/vmware-install.pl
(2)设置虚拟机和宿主机共享文件夹:player->管理->虚拟机设置->选项-共享文件夹->添加D:\vmware-share为共享文件夹
(3)df -h查看所有文件系统; cd /mnt/hgfs进入共享文件夹
(4)运行./vmware-install.pl
得到错误unable to execute ./vmware-install.pl:no such file or directory.
因为安装的是minimal的os version,所以/usr/bin/perl模块没有,执行yum install perl安装
参考:http://hypervmwarecloud.com/vmware-tools-install-error-usr-bin-perl-bad-interpreter-or-no-such-file-or-directory/
问题:vm中执行yum install perl报错：Cannot find a valid baseurl for repo
参考:https://blog.csdn.net/csd753111111/article/details/100428360

建议安装中文版:选择联网,选择服务器GUI界面