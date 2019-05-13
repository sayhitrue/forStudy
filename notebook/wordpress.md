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
