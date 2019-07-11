# 记第一次离线安装wordpress
- 嵌套列表1
 + 嵌套列表2
 + 嵌套列表3
 - 嵌套列表4
  * 嵌套列表5
- 嵌套列表6

``` python
@requires_authorization
def somefunc(param1='', param2=0):
    '''A docstring'''
    if param1 > param2: # interesting
        print 'Greater'
    return (param2 - param1 + 1) or None
class SomeClass:
    pass
>>> message = '''interpreter
... prompt'''
 ```
123'
<hr>

表格

  表头  | 表头
  ------------- | -------------
 单元格内容  | 单元格内容
 单元格内容l  | 单元格内容


安装Apache
 yum install -y httpd
启动服务，可以在前台输入网址查看
 service httpd start

 安装mysql

rpm -qa | grep mysql
查看是否安装了mysql，返回空的话，没有安装
注意：在新版本的CentOS7中，默认的数据库已更新为了Mariadb，而非 MySQL，所以执行 yum install mysql 命令只是更新Mariadb数据库，并不会安装 MySQL 。
查看已安装的 Mariadb 数据库版本。rpm -qa|grep -i mariadb
卸载已安装的 Mariadb 数据库。rpm -qa|grep mariadb|xargs rpm -e --nodeps
再次查看rpm -qa|grep -i mariadb

下载mysql
wget http://repo.mysql.com/yum/mysql-8.0-community/el/7/x86_64/mysql80-community-release-el7-3.noarch.rpm
rpm -ivh mysql80-community-release-el7-3.noarch.rpm
yum install mysql-server

https://www.cnblogs.com/DarrenChan/p/6622233.html

yum安装时rpm包的目录
/var/cache/yum/x86_64/7
也可以直接下载好放到这么目录
yum安装目录/var/lib

service mysqld start

安装php及组件
yum install php php-mysql
yum install php-gd php-imap php-ldap php-odbc php-pear php-xml php-xmlrpc

vi /var/www/html/info.php

<?php
phpinfo();
?>

下载wordpress，解压缩拷贝到服务器上

mysql建立数据库
<!-- vi /etc/my.cnf
添加：skip-grant-tables   跳过密码
重启数据库service mysqld restart
直接输入mysql登录数据库
use mysql;
update user set password=password("你的新密码") where user="root";
如：update user set password=password("password") where user="root";
update user set password=password("123") where user="root";
ALTER USER root@localhost IDENTIFIED  BY 'password';
刷新权限：flush privileges;
退出：quit -->

grep 'temporary password' /var/log/mysqld.log
初始化密码在这个日志目录中
mysql -u root -p
输出临时密码
ALTER USER root@localhost IDENTIFIED  BY 'Kjb,4286';
现在密码必须包含大写字母、小写字母、特殊符号。

如果要使用navicat登陆的话，需要执行下面的语句
ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY 'Kjb,4286';


./configure --prefix=/usr/local/php  --with-curl=/usr/local/curl  --with-freetype-dir  --with-gd  --with-gettext  --with-iconv-dir  --with-kerberos  --with-libdir=lib64  --with-libxml-dir  --with-mysqli  --with-openssl  --with-pcre-regex  --with-pdo-mysql  --with-pdo-sqlite  --with-pear  --with-png-dir  --with-xmlrpc  --with-xsl  --with-zlib  --enable-fpm  --enable-bcmath  --enable-libxml  --enable-inline-optimization  --enable-mbregex  --enable-mbstring  --enable-opcache  --enable-pcntl  --enable-shmop  --enable-soap  --enable-sockets  --enable-sysvsem  --enable-xml  --enable-zip


/etc/httpd/conf/httpd.conf

php70w-pdo.x86_64
