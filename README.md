1、Linux安装docker环境
安装yum-utils：yum install -y yum-utils device-mapper-persistent-data lvm2
为yum源添加docker仓库位置：yum-config-manager --add-repo https://download.docker.com/linux/centos/docker-ce.repo
安装docker：yum install docker-ce
启动docker：systemctl start docker
2、拉取/下载镜像,比如tomcat镜像
docker pull tomcat
等待时间，下载过程看网速快慢
3、添加镜像加速器，可以提高下载的速度,比如阿里镜像仓库
vim /etc/docker/daemon.json
{
    "registry-mirrors":["https://ung2thfc.mirror.aliyuncs.com"]
}
4、卸载docker ce
yum remove docekr-ce
rm -rf /var/lib/docker
5、创建容器并启动
docker run --name tomcat-8080 -p 8080:8080 --rm -d tomcat
6、查看当前哪些容器在运行 docker ps
查看所有的容器（包含运行和退出的）docker ps -a
7、进入容器：docker exec -it tomcat-8080 bash
退出：exit
8、删除镜像：docker image rmi 镜像ID
9、关闭正在运行的容器 docker stop 容器ID 
10、宿主机与容器交换文件
（1）把宿主机的文件复制到容器中的指定目录下  
docker cp yy.png tomcat-8080:/usr/local/photo
（2）把容器中的指定目录下的文件复制到宿主机的指定目录下
docker cp tomcat-8080:/usr/local/photo/yy.png /

