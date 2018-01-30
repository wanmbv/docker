# docker
## Docker是一款轻量级、可移植的容器。

* 可支持web应用自动打包部署；
* 自动化测试，持续集成和发布；
* 在服务型环境中调整数据库或其他应用的后台；
* 从头编译或是扩展openshit或cloud foundry平台来搭建自己的paas环境；

## Docker相关名词

1. 镜像
  
> Docker镜像就像是一个只读模板，里面可以包含一个完整的centos系统环境，安装一些需要的应用。
  镜像可以自己创建，也可以在仓库中下载，镜像运行后的实例就是一个容器。
2. 容器
 
> 容器是一个镜像运行实例，在容器中可以运行应用，可以把容器看成是一个简易的linux环境，上面运行一些需要的应用。
3. 仓库

> 仓库上存储镜像，仓库有公开仓库和是有仓库，最大的Docker仓库为Docker hub。

## 镜像制作
1. dockerFile指令
>FROM(构建指令):FROM <image>或FROM <image><tag>(可以在dockerFile中多次使用)

    FROM base/centos:7.3-3
    
