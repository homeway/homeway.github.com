---
layout: page
title: Git快速入门
---
{% include JB/setup %}

##动手试一试
    $ mkdir project1
    $ cd project1
    $ git init .
    $ echo 'hello' >> hello.txt
    $ git add hello.txt
    $ git commit -m 'hello init'

##Git结构
自Rails流行依赖，Git就是开源社区中最主要的版本管理系统。

Git与其他开源社区的工具一样，天然地生长在unix类操作系统上（linux、macos、bsd、unix等），这主要是指在windows下使用git是需要一些额外工作的。但这方面的文章很多，本文不打算探讨。

####四个概念
* 工作区，是指手头正在编辑的项目文件目录结构
* 缓存区，即stage，是指工作区中的内容保存到版本库之前的缓存，随着使用Git做很多工作，你会非常喜欢这个stage
* 本地版本库，在做了项目初始化的项目目录下，有一个.git的隐藏目录，本地版本库就保存在这里
* 远程版本库，你可以自己搭建git服务器，也可以使用github


####M的意义
* 第二列的M表示“工作区”和“暂存区”有改动
* 第一列的M表示“暂存区”和“版本库”有改动

####对象ID
是一个40位的SHA1哈希值
 
####为什么需要一个暂存区？
多了一个缓存，避免了不必要的提交错误，更加方便commit反悔撤销（反悔可以不影响工作目录），而且提高了提交质量。
<br>图形工具中多会提供这个功能，不过也有例外，如github客户端。

>这里透露了一个`频繁提交`的思想，既期待使用者频繁提交，又希望每次都是慎重的提交。思路清晰的部分写好提交说明，提交到版本库；还不清晰的部分就让她留在缓存区，一样可以作版本库管理。

####对当前提交反悔
使用图形工具中的`Amend`重新提交即可。

####回到多次提交以前
这个功能，图形工具一般不提供。通过命令以下命令都可以回到最近两次提交之前的状态： 

    $ git reset HEAD^^
    $ git reset HEAD^2
    $ git reset --soft HEAD^^

##Git图形化工具
macOS下可使用gitx，linux和windows可使用gitk。
<br>另外，为了方便与github打交道，github客户端也可以安装一个。

##Git命令
Git原本有100多个独立的脚本命令，后来被合并为git的子命令。这些脚本命令集功能非常强大，以至于图形化工具根本无法完全提供，只能选择性地为其实现图形化调用。因此，图形化工具的评价中有一项叫做`功能完备`的星级评价，一般也就是指对这些脚本命令实现的程度了。

在命令行上敲这一句，就可以了解大部分的可用命令：

    $git
    usage: git [--version] [--exec-path[=<path>]] [--html-path] [--man-path] [--info-path]
               [-p|--paginate|--no-pager] [--no-replace-objects] [--bare]
               [--git-dir=<path>] [--work-tree=<path>] [--namespace=<name>]
               [-c name=value] [--help]
               <command> [<args>]

    The most commonly used git commands are:
       add        Add file contents to the index
       bisect     Find by binary search the change that introduced a bug
       branch     List, create, or delete branches
       checkout   Checkout a branch or paths to the working tree
       clone      Clone a repository into a new directory
       commit     Record changes to the repository
       diff       Show changes between commits, commit and working tree, etc
       fetch      Download objects and refs from another repository
       grep       Print lines matching a pattern
       init       Create an empty git repository or reinitialize an existing one
       log        Show commit logs
       merge      Join two or more development histories together
       mv         Move or rename a file, a directory, or a symlink
       pull       Fetch from and merge with another repository or a local branch
       push       Update remote refs along with associated objects
       rebase     Forward-port local commits to the updated upstream head
       reset      Reset current HEAD to the specified state
       rm         Remove files from the working tree and from the index
       show       Show various types of objects
       status     Show the working tree status
       tag        Create, list, delete or verify a tag object signed with GPG

    See 'git help <command>' for more information on a specific command.

想具体了解某个命令，例如`log`，那就再敲这一句：`git help log`或 `git log --help`。
##github团队开发
##走进开源世界