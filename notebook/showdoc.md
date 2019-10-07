# showdoc 部署
采用docker方式部署
默认部署目录及nginx目录：
/var/lib/docker/overlay2/fade392bd8faf9cbdec01d4fa5df5f83cde226bfc61a245999519092582e4d49/merged/etc/nginx

nginx配置文件
/var/lib/docker/overlay2/fade392bd8faf9cbdec01d4fa5df5f83cde226bfc61a245999519092582e4d49/merged/etc/nginx/nginx.conf

如果nginx进程为其他用户启动，可在这里把用户置为user=root

如果出现403，则可考虑关闭防火墙和SELinux

SELinux
- 临时关闭SELinux <br>
setenforce 0
- 临时打开SELinux <br>
setenforce 1
- 查看SELinux状态 <br>
getenforce
- 开机关闭SELinux <br>
编辑/etc/selinux/config文件，将SELINUX的值设置为disabled。下次开机SELinux就不会启动了。

容器导出
docker export {容器名称} > {带文件名的路径}
容器导入
docker import <文件路径>  <容器名>

容器运行需要一个command，需要在导出的时候记下来或者配置好，一些官方制作的容器都是配置好的，所以不用带
