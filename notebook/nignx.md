## nginx简介
<p align="center">
  <a><img src="https://img.shields.io/badge/-Nignx-green" alt="pig"></a>
</p>

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
./configure --prefix=/Nginx                 //生成Makefile
```
##### 编译和安装
```sh
make && make install
```
##### 重新编译和安装
```sh
make clean
make && make install
```
## nignx服务器目录
- conf 配置文件，其中nginx.conf为主配置文件，.default文件为默认配置文件
- html nignx调试相关的网页文件
- logs 日志
- sbin nginx主程序  
```sh
./nignx -h           //可获取nginx二进制文件的相关用法
./nignx -?
./nginx -v           //打印版本号
./nginx -V           //打印版本号和配置
./ngixn -s signal    //向主进程发送信号  
```

## nginx服务器信号控制
```sh
./ngixn -s signal    //向主进程发送信号
```
- stop — fast shutdown
- quit — graceful shutdown
- reload — reloading the configuration file
- reopen — reopening the log files

## nginx配置文件
##### nginx 文件结构
```
...              #全局块
events {         #events块
   ...
}

http      #http块
{
    ...   #http全局块
    server        #server块
    {
        ...       #server全局块
        location [PATTERN]   #location块
        {
            ...
        }
        location [PATTERN]
        {
            ...
        }
    }
    server
    {
      ...
    }
    ...     #http全局块
}
```
- 全局块：配置影响nginx全局的指令。一般有运行nginx服务器的用户组，nginx进程pid存放路径，日志存放路径，配置文件引入，允许生成worker process数等。
- events块：配置影响nginx服务器或与用户的网络连接。有每个进程的最大连接数，选取哪种事件驱动模型处理连接请求，是否允许同时接受多个网路连接，开启多个网络连接序列化等。
- http块：可以嵌套多个server，配置代理，缓存，日志定义等绝大多数功能和第三方模块的配置。如文件引入，mime-type定义，日志自定义，是否使用sendfile传输文件，连接超时时间，单连接请求数等。
- server块：配置虚拟主机的相关参数，一个http中可以有多个server。
- location块：配置请求的路由，以及各种页面的处理情况。

## 变量
https://nginx.org/en/docs/http/ngx_http_core_module.html
