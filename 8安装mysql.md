# 安装mysql 5.6

* 添加 MySQL YUM 源
  * 用wget从官网下载yum源
  * rpm -Uvh mysql57-community-release-el7-11.noarch.rpm
* 选择安装版本
  * 修改mysql yum源配置文件
    * vim /etc/yum.repos.d/mysql-community.repo
    * 通过设置 enabled 来决定安装哪个版本，1为安装；0为不安装
* 用yum安装
  * yum -y install mysql-community-server
* 启动mysql
  * systemctl start mysqld
* 修改mysql密码
  * 运行官方脚本：mysql_secure_installation
  * 运行脚本之后，会提示设置5个关键位置：
    1. 设置 root 密码
    2. 禁止 root 账号远程登录
    3. 禁止匿名账号（anonymous）登录
    4. 删除测试库
    5. 是否确认修改
    * 第一次运行的时候密码为空

## 参考文献

<https://www.jianshu.com/p/7cccdaa2d177>

### 至此，lnmp环境配置完成
  
