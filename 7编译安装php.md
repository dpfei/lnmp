# 编译安装nginx

## 安装依赖

* yum -y install gcc bison bison-devel zlib-devel libmcrypt-devel mcrypt mhash-devel openssl-devel libxml2-devel libcurl-devel bzip2-devel readline-devel libedit-devel sqlite-devel jemalloc jemalloc-devel

* 下载源码包
  * wget http://cn2.php.net/distributions/php-7.2.10.tar.gz
* 解压下载好的源码包
  * tar -zxvf php-7.2.10.tar.gz
* 进入解压后的目录
* 配置
  * ./configure --prefix=/home/work/software/php --with-config-file-path=/home/work/software/php/etc --enable-inline-optimization --disable-debug --disable-rpath --enable-shared --enable-opcache --enable-fpm --with-fpm-user=root --with-fpm-group=root --with-pdo-mysql=mysqlnd --with-mysqli=mysqlnd --with-pdo-mysql=mysqlnd --with-gettext --enable-mbstring --with-iconv --with-mhash --with-openssl --enable-bcmath --enable-soap --with-libxml-dir --enable-pcntl --enable-shmop --enable-sysvmsg --enable-sysvsem --enable-sysvshm --enable-sockets --with-curl --with-zlib --enable-zip --with-bz2 --with-readline
* 编译安装
  * make && make install
* 配置服务
  * cp php-fpm.conf.default php-fpm.conf
  * chmod +x ./php-fpm.conf
* 增加环境变量
  * vim /etc/profile
  * 在文件末尾增加
    * PATH=$PATH:/usr/local/php/bin
    * export PATH
* 执行命令：source profile
* 将php-fpm.d中的文件重命名
  * cd /home/work/software/php/etc/php-fpm.d
  * mv www.conf.default www.conf
* 配置nginx支持php
  * cd /home/work/software/nginx/conf/
  * 去除nginx.conf文件中大概65行处的配置的#
  * 修改66行处的内容为
    * root /home/work/code;
  * 修改69行处的内容为
    * fastcgi_param  SCRIPT_FILENAME  $document_root$fastcgi_script_name;
  * 重启php-fpm服务
  * 安装完成

## 参考文献

* <https://www.cnblogs.com/37yan/p/6879404.html>