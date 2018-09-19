# 设置centos7静态ip

## 设置网络设置

* cd /etc/sysconfig/network-scripts/
* 编辑该目录下第一个文件，文件名类似于为**ifcfg-enp0s3**，视自己系统中的文件为准
* 系统刚安装完成的时候并没有安装vim
* 使用vi编辑**ifcfg-enp0s3**，**vi ifcfg-enp0s3**
* 将该文件中的**BOOTPROTO=dhcp**修改为**BOOTPROTO=static**
* 将**ONBOOT=no**修改为**ONBOOT=yes**
* 在文件的末尾添加内容
* IPADDR=192.168.0.111 **centos7的ip地址，需要和物理主机地址保持在同一IP段**
* GATEWAY=192.168.0.1 **默认网关，和屋里主机网关保持一致**
* NETMASK=255.255.255.0 **子网掩码**
* 保存退出文件

## 设置DNS

* 切换到上一级目录，**cd ../**，目录位置为：**/etc/sysconfig/**
* 用vi编辑network文件，**vi network**
* 在network文件中增加DNS配置，如：DNS1=8.8.8.8，可以添加任意多个DNS
* 保存退出文件
* 重启网络服务，**systemctl restart network**
* 通过**ip addr**命令可以看到配置后的ip地址

## 关闭防火墙&&禁止防火墙开启启动

* 关机防火墙，**systemctl stop firewalld.service**
* 禁止防火墙开机启动 **systemctl disable firewalld.service**
* 永久关闭SELinux 
  * **vim /etc/selinux/config**
  * 将SELINUX=enforcing改为SELINUX=disabled
  * 设置后重启系统生效

===========================================================

* 至此，设置ip地址，关闭防火墙，设置防火墙开机不启动完成
* 在虚拟机启动完成之后，可以通过xshell等工具链接centos7
