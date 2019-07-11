Windows环境

打开数据库<br>
`net start mysql`

关闭数据库<br>
`.\mysqladmin.exe -uroot shutdown`

登陆数据库
`mysql -h 主机名 -u 用户名 -p`<br>
参数说明：<br>
-h : 指定客户端所要登录的 MySQL 主机名, 登录本机(localhost 或 127.0.0.1)该参数可以省略;<br>
-u : 登录的用户名;<br>
-p : 告诉服务器将会使用一个密码来登录, 如果所要登录的用户名密码为空, 可以忽略此选项。<br>
