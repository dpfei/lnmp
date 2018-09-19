# 安装Samba服务，安装完成之后就可以通过网络映射在windows上访问linux中的目录。

## Samba说明
* Samba是在Linux和UNIX系统上实现SMB协议的一个免费软件，由服务器及客户端程序构成。SMB（Server Messages Block，信息服务块）是一种在局域网上共享文件和打印机的一种通信协议，它为局域网内的不同计算机之间提供文件及打印机等资源的共享服务。
## 安装Samba
* yum -y install samba samba-client
## 验证是否安装成功
* rpm -qi samba
* 如果返回Samba信息则证明安装成功

## 配置Samba服务
* 进入Samba配置目录
  * cd /etc/samba
