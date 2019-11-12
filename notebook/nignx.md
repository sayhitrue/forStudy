## nginx简介
Nginx是一款轻量级的Web 服务器/反向代理服务器及电子邮件（IMAP/POP3）代理服务器。

## 常用功能介绍
- HTTP代理和反向代理
- 负载均衡
- WEB缓存

## nginx安装包目录结构
- src 源代码
- man 帮助文档
- auto 脚本文件
- configure nignx软件的自动脚本程序，编译生成Makefile文件。

configure常用参数

选项|说明
:--|:--
--prefix=path|指定安装路径，不指定默认为/usr/local/nginx
--user=name|在nginx.conf文件未指定user情况下，默认nginx服务器进程的属主用户，默认nobody
--add-module=path|指定第三方模块的路径，用以编译到nginx服务器中

## Linux服务器上nignx编译&安装
##### 生成Makefile
```sh
./configure --prefix=/Nginx
```
`./configure --prefix=/Nginx`
