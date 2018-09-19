# 安装git
* yum -y install git
# 创建SSH Key
* ssh-keygen -t rsa -C "youremail@example.com"
  * 你需要把邮件地址换成你自己的邮件地址，然后一路回车，使用默认值即可，由于这个Key也不是用于军事目的，所以也无需设置密码
  * 如果一切顺利的话，可以在用户主目录里找到.ssh目录，里面有id_rsa和id_rsa.pub两个文件，这两个就是SSH Key的秘钥对，id_rsa是私钥，不能泄露出去，id_rsa.pub是公钥，可以放心地告诉任何人
* 将id_rsa.pub文件中的内容添加到远程仓库中
* 设置添加完成后就可以正常使用git了

# 参考文献
* https://www.liaoxuefeng.com/wiki/0013739516305929606dd18361248578c67b8067c8c017b000/001374385852170d9c7adf13c30429b9660d0eb689dd43a000
