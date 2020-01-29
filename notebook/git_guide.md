## git学习

[菜鸟教程][1]

#### git简介
- 分布式

git分布式本地有一套完整的版本控制


#### git安装

查看版本`git --version`

#### git配置

配置用户名和邮箱

     git config --global user.name 'sayhitrue'
     git config --global user.email 'sayhitrue@gmail.com'
其中git代表是git指令，windows系统git自带git bash，如果要在windows的cmd或者powerShell中执行，需要配置环境变量。

config是指令，后面的是参数，--global还有其他几个选项

    usage: git config [<options>]
|参数||
|:--|:--|
|local|仓库级别，具体到git目录，配置文件是当前仓库下的.git/config|
|global|用户级别，使用最多，一般我们一台电脑就一个用户，改一处就能改全部，配置文件一般在用户宿主目录下的~/.gitconfig，比如C:\Users\sayhi|
|system|系统级别，用的比较少，配置文件在安装目录的/etc/gitconfig|






[1]:https://www.runoob.com/git/git-tutorial.html
