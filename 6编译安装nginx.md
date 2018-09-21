# 编译安装nginx

## 安装nginx依赖

* yum -y install gcc gcc-c++ zlib zlib-devel openssl* pcre pcre-devel gd-devel cyrus-sasl-md5
* 用wget从nginx官网下载tar包
* 用tar命令解压下载的源码包
  * tar -zxvf nginx-1.15.3.tar.gz
* 进入解压后的目录
* 执行configure命令
  * ./configure --prefix=/home/work/software/nginx --user=root --group=root --with-http_stub_status_module --with-http_ssl_module --with-http_sub_module --with-http_realip_module --with-http_image_filter_module
  * 需要什么模块功能可以自己选择 ./configure --help 命令可以查看所有模块。注意一下配置时有没有报错，报错的话缺什么补什么；如果没有报错 则进行编译安装
* 编译安装
  * make && make install
* 编译完成之后，进入nginx.conf配置文件修改运行nginx的用户
  * 将nginx.conf文件中的user nobody;修改为user root;
* 编译完成之后，执行命令启动nginx
  * /home/work/software/nginx/sbin/nginx
  * 其他的nginx命令请自行百度或者谷歌
* nginx启动之后可以可以通过ip直接访问到nginx

## 参考文献

* <https://www.cnblogs.com/KenChung/p/8079313.html>