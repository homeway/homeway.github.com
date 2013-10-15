---
layout: page
title: "rvm用法总结"
---
{% include JB/setup %}

玩ruby，必须熟练使用rvm。

rvm可以让你在不同的ruby版本和不同gem版本的环境之间切换。例如，某个项目要使用rails3.2，而另外一个要使用rails4.0，你当然不希望做gem更新时把他们一股脑更新成统一的版本。

本文对rvm命令做了全面总结，可以作为参考手册收藏。

以下命令演示都在MacOS 10.8环境下完成。

##安装rvm
    $ curl -L get.rvm.io | bash -s stable
    $ source ~/.bashrc
    $ source ~/.bash_profile

安装完成后，手动将以下行添加到Shell的启动脚本（我的是~/.zshrc。根据实际情况当然也可以是~/.bashrc、~/.bash_login或者~/.zprofile）：

    [[ -s "$HOME/.rvm/scripts/rvm" ]] && . "$HOME/.rvm/scripts/rvm"

注意：在这里不需要再将RVM的bin目录手动添加到$PATH。也就是说，PATH=$PATH:$HOME/.rvm/bin这一行在~/.zshrc中并不是必需的。

使用下面两条指令检查RVM的功能提示喝依赖信息等：

    $ rvm notes
    $ rvm requirements
查看RVM的功能提示、依赖信息等等。以后每次升级过RVM后都应检查这些信息，以确保RVM能正常工作。

rvm最常用的Action包括：对Ruby的操作,主要包括读取，安装，卸载，更新，读取ruby等.

##使用rvm安装Ruby
###获得当前可以用的ruby版本
    rvm list known

###安装其中的ruby1.9.2-p290
    rvm install ruby-1.9.2-p290

###切换到刚刚安装的ruby1.9.2-p290版本
    rvm use ruby1.9.2-p290

###设定在默认情况下不使用rvm的Ruby，而使用系统Ruby：
    $ rvm use system --default
    Now using system ruby.

###列出当前rvm下的ruby版本
    rvm list

###查询当前使用的ruby版本路径
    which ruby

###获得当前ruby版本
    ruby -v

###输出rvm当前使用的ruby版本与gemset信息：
    rvm info

###使用下面命令对rvm自己进行升级
    $ rvm update

##使用rvm管理ruby版本

###查看rvm信息
通过以下几个命令查看当前RVM当前信息
    $ rvm info
    $ rvm info 1.9.2

用这个命令查看有哪些RVM可用的Ruby版本
    $ rvm list known
    $ rvm install 1.9.2    # 安装 ruby-1.9.2
    $ rvm install ree   # install Ruby Enterprise Edition (REE)

###切换Ruby版本
安装多个版本的Ruby之后，RVM可以很方便的进行切换。使用下条命令可以设置某一版本为当前使用版本。

    $ rvm  ruby-1.8.7-p160 #切换1.8.7-p160为当前使用版本
    $ rvm 1.8.7-p160    #同上面命令一样rvm ruby-1.8.7-p160
    $ ruby -v #查看当前Ruby版本

###查看当前Ruby的安装位置
    $ which ruby

###设置默认使用版本
将某一个版本的ruby设为默认，这样避免每次启动新的Shell都要选择所要使用的Ruby版本。
    $ rvm –default use 1.8.7   #设置1.9.2为默认版本
    $ rvm default      #通过default可以快速回到默认版本
    $ rvm list default     #查看当前版本设置信息
    $ rvm reset     #恢复系统默认设置

###查看已安装的Ruby信息
列出所有已经安装的Ruby的版本信息
    $ rvm list      #列出已安装的Ruby版本
    $ rvm list rubies     #同上
    $ rvm list default    #显示默认Ruby版本信息
    $ rvm list known     #列出RVM所支持的所有Ruby版本的信息

###创建别名
使用带版本号的ruby时，每次切换时都要输入很长的版本号，非常的不方便，通过使用别名功能，可以创建很简短的别名来代替长长的ruby信息。

    $ rvm alias create reed ree-1.8.7-p2010.01    #为ree-187的Ruby版本创建一个别名叫：reed

    $ rvm use reed  #通过别名迅速切换
    $ rvm alias delete reed   #删除别名
    $ rvm alias list # 查看所有的别名

###删除已安装版本

    $ rvm remove ruby-1.9.2-p0

    $ rvm uninstall ruby-1.9.2-p0

##使用ruby管理Gemset
一个gemset就是一个目录，是某一个Ruby版本的Gem使用集，通过环境变量配置，使该gemset下的gem命令导入到Shell。

一个Ruby版本初装时就默认给了一个同名的gemset，也就是说rvm ruyb-1.9.2-p0 命令在执行时，就是使用该环境变量。

###创建Gemset
基于指定Ruby版本创建一个新的Gemset

    $ rvm gemset create rails3  #创建一个名为rails3的gemset
###指定某一个gemset作为当前环境使用。

    $ rvm gemset use rails3   #在当前Ruby下使用rails3这个gemset
    $ rvm use ruby-1.9.2-p0@rails3 #或者直接使用这种命名，直接指定ruby和gemset的信息。
    $ rvm use ruby-1.9.2-p0@rails3 –default   #设置默认

###列出当前Ruby版本下所有gemset的信息
    $ rvm gemset list

###列出所有Ruby版本下所有gemset的信息
    $ rvm gemset list_all

###显示当前所使用的gemset信息
    $ rvm gemset name     #当前gemset的名称

    rails3
    $ rvm gemdir   #所在位置
    ~/.rvm/gems/ruby-1.9.2-p0@rails3
###删除
删除一个gemset，默认有确认操作，使用 –force 可跳过该步骤。

    $ rvm gemset delete rails3  #会让确认一次
    $ rvm –force gemset delete rails3     #直接删除，没有确定步骤

###清空
可以清空一个Gemset，删除其中的所有的gems包

    $ rvm gemset empty rails3
    $ rvm –force gemset empty rails3   #直接删除，没有确定步骤

###导出
将当前gemsets内的信息导出到一个 name.gems文件，gems文件内定义gem的名称，版本号和其信赖关系。

    $ rvm gemset export rails3.gems

###导入
将gems文件所指定的gems安装到当前gemset下。

    $ rvm gemset rails3
    $ rvm gemset import rails3

###复制
可以将一个gemset内的所有gems包都复制到另一个gemset，很快速的复制一个当前环境。

    $ rvm gemset copy 1.8.7@rails3 1.9.2-head@rails3

###使用全局gemset
    $ rvm gemset list

    gemsets for ruby-1.9.3-p448 (found in /Users/homeway/.rvm/gems/ruby-1.9.3-p448)
    => (default)
       global
       rails32
    $ rvm gemset use global
    $ gem install ... #你所安装的gem包会在各个gemset中共享

每一个ruby版本都默认创建一个全局的gemset，以ruby_version@global命名，这样基于该ruby版本下所有的gemsets都会包含全局gemset里的gem包。可以起到统一约定的作用，也避免重复创建。
默认安装的global gemset内仅有一个gem包：rake

###在项目文件中使用rvm
在自己的项目根目录下面，创建一个**.rvmrc**文件，里面内容可以指定ruby版本与gemset。例如，某项目根目录下面的**.rvmrc**文件内容如下：

    rvm ruby-1.9.3-p448@rails32
当你使用cd命令切换到该目录时，gemset和ruby版本就生效了。