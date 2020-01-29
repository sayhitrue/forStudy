## git学习

[菜鸟教程](https://www.runoob.com/git/git-tutorial.html)

[git官网](https://git-scm.com/book/zh/v2)

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
|参数|说明|
|:--|:--|
|local|仓库级别，最高优先级，具体到git目录，配置文件是当前仓库下的.git/config|
|global|用户级别，使用最多，一般我们一台电脑就一个用户，改一处就能改全部，配置文件一般在用户宿主目录下的~/.gitconfig，比如C:\Users\sayhi|
|system|系统级别，用的比较少，配置文件在安装目录的/etc/gitconfig|

config指令除了上述参数设置用户名密码外，还有许多参数，可git config查看。

    git config --local --list    //--list同-l  查看local下面的配置

#### git仓库建立
<br>
新建git仓库分为两种情况，已有代码要纳入git管理、新建项目  
<br>
<br>
已有代码要纳入git管理

    cd 已有项目路径
    git init

新建项目

    cd 你要放项目的文件夹
    git init your_project  //会在当前目录创建你的项目文件夹
    cd your_project

配置

    git config --global --list  //查看当前的全局设置
    git config --local user.name 'xxx'   //如果你要配置独立的名称和邮箱
    git config --local user.email 'xxx@gmail.com'
    git config --local -l //再次查看配置，因为local的优先级高于global

提交

先来看看git的工作区、暂存区和版本库概念
- 工作区：就是你在电脑里能看到的目录。
- 暂存区：英文叫stage, 或index。一般存放在 ".git目录下" 下的index文件（.git/index）中，所以我们把暂存区有时也叫作索引（index）。
- 版本库：工作区有一个隐藏目录.git，这个不算工作区，而是Git的版本库。



    git add readme.md  //提交到stage
    git commit -m 'Add readme' //-m为添加提交注释
    git log //会显示当前提交的版本号、作者信息、时间等
