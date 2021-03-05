### 一.[如何安装docker](https://docs.docker.com/engine/install/centos/#prerequisites)
#### (1)设置docker仓库
安装yum-utils,yum-utils提供了yum-config-manager功能  
sudo yum install -y yum-utils
设置docker stable仓库  
sudo yum-config-manager  --add-repo <https://download.docker.com/linux/centos/docker-ce.repo>
#### (2)安装docker
方法1:直接安装最近版本的docker engine   
sudo yum install docker-ce docker-ce-cli containerd.io  
一路yes即可
方法2:安装指定版本的docker engine  
列出可用的docker engine:  
yum list docker-ce --showduplicates | sort -r   
安装指定的docker engine:
sudo yum install docker-ce-&lt;VERSION_STRING> docker-ce-cli-&lt;VERSION_STRING> containerd.io  
VERSION_STRING是命令"yum list docker-ce --showduplicates | sort -r"的输出的第二列,比如3:18.09.1-3.el7取:和-之间的版本号18.09.1
#### (3)启动、关闭、查看状态
sudo systemctl start docker  
sudo systemctl stop docker  
sudo systemctl status docker
#### (4)验证docker是否正确安装
docker info  
docker version  
sudo docker run hello-world
输出:
To generate this message, Docker took the following steps:
 1\. The Docker client contacted the Docker daemon.
 2\. The Docker daemon pulled the "hello-world" image from the Docker Hub.
    (amd64)
 3\. The Docker daemon created a new container from that image which runs the
    executable that produces the output you are currently reading.
 4\. The Docker daemon streamed that output to the Docker client, which sent it
    to your terminal.
参考链接:  
[docker入门教程](https://ruanyifeng.com/blog/2018/02/docker-tutorial.html)
[docker for java developers](https://github.com/docker/labs/tree/master/developer-tools/java)
[docker develop best practice](https://docs.docker.com/develop/dev-best-practices/)
(5)image
列出本机所有image文件:docker image ls
删除指定image文件:docker rm image [imageName]
将image从仓库拉到本地:docker pull image library/hello-world  
运行image文件:docker container run [imageName],从image文件生成一个运行的实例  
docker container run -p 80:8080 -it test-image:0.1
(6)容器文件  
每次执行docker container run [imageName]都会创建一个容器
列出本机正在运行的容器:docker container ls  
列出本机正在运行的容器，包括终止运行的容器:docker container ls --all
终止容器运行:  
docker container kill [container-id]:强行终止docker容器实例,那些正在进行中的操作会全部丢失  
docker container stop [container-id]:进行收尾清理工作后终止docker容器实例
终止运行的容器仍然会占用硬盘空间,要删除:docker container rm [container-id]
启动一个已创建且停止运行的容器:docker container run [container-id]

(7)创建自己的image, dockerfile  
1.创建好Dockerfile
2.创建image:docker image build -t test-image:0.1 .
-t参数指定image名字为test-image,0.1为标签,可以不指定标签(test-image),默认标签为latest
最后那个点表示Dockerfile的路径为当前路径
3.运行image
参考docker入门教程
(8)如何创建自己的springboot jar
1.gradle init初始化  
2.用模板build.gradle文件  
3.创建springboot启动类  
``` 
@SpringBootApplication(exclude = {DataSourceAutoConfiguration.class})
public class App {
    public static void main(String[] args) {
        SpringApplication.run(App.class, args);
    }
}
```
问题:VMware虚拟机中的linux重启后共享文件夹挂载失效的解决方案  
```
sudo /usr/bin/vmhgfs-fuse .host:/ /mnt/hgfs -o allow_other -o uid=1000 -o gid=1000 -o umask=022  
```
问题:如何在linux command命令行get访问ulr:curl -X GET http://<IP地址>:<端口号>/megacorp/employee/1
curl -X GET http://127.0.0.1:80/v1
  