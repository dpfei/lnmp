# 安装Samba服务，安装完成之后就可以通过网络映射在windows上访问linux中的目录。

## Samba说明

* Samba是在Linux和UNIX系统上实现SMB协议的一个免费软件，由服务器及客户端程序构成。SMB（Server Messages Block，信息服务块）是一种在局域网上共享文件和打印机的一种通信协议，它为局域网内的不同计算机之间提供文件及打印机等资源的共享服务。

## 安装Samba

* yum -y install samba samba-client

## 验证是否安装成功

* rpm -qi samba
* 如果返回Samba信息则证明安装成功

## 设置Samba开机启动

* systemctl enable smb.service

## 配置Samba服务

* 进入Samba配置目录
  * cd /etc/samba
  * 编辑配置文件，在samba.conf文件末尾添加自己要共享的文件配置，例如：
    <pre><code>
      [code]
        comment = code directory
        path = /home/work/code
        browseable = yes
        writable = yes
        available = yes
        admin users = root
        public = yes
    </code></pre>

* 用pdbedit添加Samba用户。**注意，Samba用户必须是linux用户**
  * pdbedit -a root
    * 添加用户的时候会要求设置密码，此时设置的密码用于通过Samba登陆使用
* 添加完成，即可在windows上访问Samba中的共享目录
* **通过Samba访问centos 7之后创建的文件，文件的创建者将是登陆Samba用的linux用户**
* **注意文件的权限问题，权限问题将会导致一大堆问题**
  
### 参考文献  

* http://blog.51cto.com/yuanbin/115761
* https://www.linuxidc.com/Linux/2017-03/141390.htm
