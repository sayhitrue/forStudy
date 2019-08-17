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

A temporary password is generated for root@localhost: MuhVouChd2.e

ALTER USER root@localhost IDENTIFIED  BY 'Kjb,4286';

ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY 'Kjb,4286';


Establishing SSL connection without server's identity verification is not recommended. According to MySQL 5.5.45+, 5.6.26+ and 5.7.6+ requirements SSL connection must be established by default if explicit option isn't set. For compliance with existing applications not using SSL the verifyServerCertificate property is set to 'false'. You need either to explicitly disable SSL by setting useSSL=false, or set useSSL=true and provide truststore for server certificate verification.
