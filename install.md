# docker install
centos7环境安装，需要centos-extra repository可用，在CentOS-base.repo中将extra设置成enable=1。

**建议使用非root用户操作docker**

    # useradd -g docker xxx
*安装相关依赖包*
    
    $ sudo yum install -y yum-utils \
    device-mapper-persistent-data \
    lvm2
*添加docker repo*
    
    $ sudo yum-config-mapper \
    --add-repo \
    https://download.docker.com/linux/centos/docker-ce.repo
 
*安装docker*
    
    $ sudo yum -y install docker-ce
    
*启动docker*
 
    $ sudo systemctl start docker
    
*设置开机启动*
  
    $ sudo systemctl enable docker
    
*设置国内加速器（需要在DaoCloud注册账号）*

> curl -sSL https://get.daocloud.io/daotools/set_mirror.sh | sh -s http://d90a4c98.m.daocloud.io

*安装管理工具-portainer*

    $ docker search portainer
    $ docker pull portainer/portainer
    $ docker run -d --name portainer \
    -p 9000:9000 \
    --restart=always \
    -v /var/run/docker.sock:/var/run/docker.sock \
    portainer/portainer
    
> 访问http://xxx:9000可以进入管理服务
    
*开放需要的端口*
 
    $ sudo vi /lib/systemd/system/docker.service
     
> 修改 ExecStart=/user/bin/dockerd -H tcp://0.0.0.0:2375 -H unix:///var/run/docker.sock

    $ sudo systemctl daemon-reload
    $ sudo systemctl restart docker.service
    
    $ sudo firewall-cmd --zone=pulic --add-port=2375/tcp --permanent && \
    sudo firewall-cmd --zone=public --add-port=9000/tcp --permanent && \
    sudo firewall-cmd --reload
 
