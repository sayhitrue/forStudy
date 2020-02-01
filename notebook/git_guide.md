## git学习

[菜鸟教程](https://www.runoob.com/git/git-tutorial.html)

[git官网](https://git-scm.com/book/zh/v2)

git帮助文档在安装目录如下位置 D:\Program Files\Git\mingw64\share\doc\git-doc，可通过 `git help <command>` 打开，如`git help log`

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
- 暂存区：英文叫stage, 或index。一般存放在 ".git目录下" 下的index文件（.git/index）中，所以我们把暂存区有时也叫作索引（index）。（如果你对一个功能有多个想法，可以先完成一个提交到暂存区，然后再去完成下一个想法。）
- 版本库：工作区有一个隐藏目录.git，这个不算工作区，而是Git的版本库。

新增

    git add readme.md  //新增和编辑文件提交到stage
    git commit -m 'Add readme' //-m为添加提交注释
    git log //会显示当前提交的版本号、作者信息、时间等
    git status //查看状态
    git add .




暂存区删除

    usage: git rm [<options>] [--] <file>...

    -n, --dry-run         dry run
    -q, --quiet           do not list removed files
    --cached              only remove from the index
    -f, --force           override the up-to-date check
    -r                    allow recursive removal
    --ignore-unmatch      exit with a zero status even if nothing matched

    #用的比较多的如下
    git rm -f <file>  #强行删除，会同时删除本地工作区的文件
    git rm --cache <file>  #删除暂存区，但不会删除本地工作区
    git rm <file>   #本地工作区文件已经没了，删除暂存区的
    git status  # 查看状态

改文件名

    #改文件名你可以先新增+删除实现，但是太麻烦，git提供了mv指令，用于移动或重命名一个文件、目录、软连接。
    usage: git mv [<options>] <source>... <destination>

    -v, --verbose         be verbose
    -n, --dry-run         dry run
    -f, --force           force move/rename even if target exists
    -k                    skip move/rename errors

    git mv readme readme.md #更改名称，同时修改本地和暂存区文件

版本库->暂存区恢复

    usage: git reset [--mixed | --soft | --hard | --merge | --keep] [-q] [<commit>]
    or: git reset [-q] [<tree-ish>] [--] <paths>...
    or: EXPERIMENTAL: git reset [-q] [--stdin [-z]] [<tree-ish>]
    or: git reset --patch [<tree-ish>] [--] [<paths>...]

    -q, --quiet           be quiet, only report errors
    --mixed               reset HEAD and index
    --soft                reset only HEAD
    --hard                reset HEAD, index and working tree
    --merge               reset HEAD, index and working tree
    --keep                reset HEAD but keep local changes
    --recurse-submodules[=<reset>]
                          control recursive updating of submodules
    -p, --patch           select hunks interactively
    -N, --intent-to-add   record only the fact that removed paths will be added later
    -z                    EXPERIMENTAL: paths are separated with NUL character
    --stdin               EXPERIMENTAL: read paths from <stdin>

    #一般指令如下
    git reset HEAD  #拉去最近一次版本库的不影响工作区,HAED是一个游标（指针）
    git reset HEAD^  #回退到上一个版本
    $ git log --oneline
    a9fd3a6 (HEAD -> master) Add readme

    git reset a9fd3a6 --<文件>
    #不是主分支也是同样的道理，先要切分支，HEAD用其他分支代替


    git reset --hard HEAD   #会把工作区的同时修改，不建议有风险


暂存区->工作区恢复

    $ git checkout -h
    usage: git checkout [<options>] <branch>
    or: git checkout [<options>] [<branch>] -- <file>...

    git checkout .
    git checkout --<file>  #会用暂存区全部或指定的文件替换工作区的文件。这个操作很危险，会清除工作区中未添加到暂存区的改动。



版本库->工作区恢复

    git checkout HEAD .
    git checkout HEAD <file>
    git checkout <branch> #切换分支，会改变工作区
    git checkout -b <new-branch> <branch>  #以旧的版本库分支创建新的分支，并拉到工作区
    git commit -am'直接提交'  //注意新建文件不能这样提交，修改的可以

    #git checkout 带版本号就是从版本库中拉取到工作区，不带就是从暂存区拉取


日志

    $ git log -h
    usage: git log [<options>] [<revision-range>] [[--] <path>...]
    or: git show [<options>] <object>...

    -q, --quiet           suppress diff output
    --source              show source
    --use-mailmap         Use mail map file
    --decorate-refs <pattern>
                          only decorate refs that match <pattern>
    --decorate-refs-exclude <pattern>
                          do not decorate refs that match <pattern>
    --decorate[=...]      decorate options
    -L <n,m:file>         Process line range n,m in file, counting from 1

    git log --oneline --all --graph -n4  #oneline显示在一行,graph图形化，n4最新4行

.git文件夹

    #git cat-file 的命令显示版本库对象的内容、类型、及大小信息。
    $ git cat-file -h
    usage: git cat-file (-t [--allow-unknown-type] | -s [--allow-unknown-type] | -e | -p | <type> | --textconv | --filters) [--path=<path>] <object>
       or: git cat-file (--batch | --batch-check) [--follow-symlinks] [--textconv | --filters]

    <type> can be one of: blob, tree, commit, tag
        -t                    show object type
        -s                    show object size
        -e                    exit with zero when there's no error
        -p                    pretty-print object's content
        --textconv            for blob objects, run textconv on object's content
        --filters             for blob objects, run filters on object's content
        --path <blob>         use a specific path for --textconv/--filters
        --allow-unknown-type  allow -s and -t to work with broken/corrupt objects
        --buffer              buffer --batch output
        --batch[=<format>]    show info and content of objects fed from the standard input
        --batch-check[=<format>]
                              show info about objects fed from the standard input
        --follow-symlinks     follow in-tree symlinks (used with --batch or --batch-check)
        --batch-all-objects   show all objects with --batch or --batch-check
        --unordered           do not order --batch-all-objects output


        $ ll
        total 14
        -rw-r--r-- 1 sayhi 197609  10 1月  31 21:48 COMMIT_EDITMSG
        -rw-r--r-- 1 sayhi 197609 191 1月  31 23:24 config
        -rw-r--r-- 1 sayhi 197609  73 1月  29 22:18 description
        -rw-r--r-- 1 sayhi 197609 132 1月  31 22:38 gitk.cache
        -rw-r--r-- 1 sayhi 197609  23 1月  31 22:02 HEAD
        drwxr-xr-x 1 sayhi 197609   0 1月  29 22:18 hooks/
        -rw-r--r-- 1 sayhi 197609 209 1月  31 22:03 index
        drwxr-xr-x 1 sayhi 197609   0 1月  29 22:18 info/
        drwxr-xr-x 1 sayhi 197609   0 1月  30 23:34 logs/
        drwxr-xr-x 1 sayhi 197609   0 1月  31 21:48 objects/
        drwxr-xr-x 1 sayhi 197609   0 1月  29 22:18 refs/

        $ cat HEAD
        ref: refs/heads/master  #引用，指向master分支

        $ ll refs/
        total 0
        drwxr-xr-x 1 sayhi 197609 0 1月  31 21:59 heads/  #分支
        drwxr-xr-x 1 sayhi 197609 0 1月  29 22:18 tags/   #标签又叫里程碑，对于特殊版本打上特殊标记，如大版本变更v2.0.0


        #git所有都是以对象的形式保存的，生成的hash作为唯一标识，2位的目录就是hash的前2位
        $ ll objects/
        total 0
        drwxr-xr-x 1 sayhi 197609 0 1月  30 21:31 19/
        drwxr-xr-x 1 sayhi 197609 0 1月  30 23:34 4a/
        drwxr-xr-x 1 sayhi 197609 0 1月  30 23:19 4b/
        drwxr-xr-x 1 sayhi 197609 0 1月  31 21:48 4d/
        drwxr-xr-x 1 sayhi 197609 0 1月  30 23:34 a9/
        drwxr-xr-x 1 sayhi 197609 0 1月  31 21:48 e6/
        drwxr-xr-x 1 sayhi 197609 0 1月  29 22:18 info/
        drwxr-xr-x 1 sayhi 197609 0 1月  29 22:18 pack/

        $git cat-file -p a9fd3a6ae5e8c6b #hash40位，如果前几位可以唯一表示这串hash则可以前几位短的代替长的
        tree 4a05013c8ee7a06ad6f1c65ce04c29bf4f038c30  
        author sayhitrue <sayhitrue@163.com> 1580398497 +0800
        committer sayhitrue <sayhitrue@163.com> 1580398497 +0800

        Add readme

        #config文件保存本地配置信息，同如下指令
        $git config --local -l    #如果你配置本地化的用户名和邮箱的话，就会在这边显示
