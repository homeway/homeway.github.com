---
layout: page
title: Gem
tagline: 如何使用gem
---
{% include JB/setup %}

##Gem基本用法
`gem install`用法：

    用法: gem install GEMNAME [GEMNAME ...] [options] -- --build-flags [options]

##避免直接从https://rubygems.org安装的几种方案
* 更换gem源，如使用`http://ruby.taobao.org`
* 在bundle的Gemfile中指定不同的源
* 使用`rails new [project-name] --skip-bundle`创建项目，然后执行`bundle install --local`从本地安装gem包
* 使用`gem server`从本地或局域网安装
* 搭建较为专业的`geminabox`服务器，甚至对rubygems.org做镜像

##更换gem源
列举ruby环境中的gem源：

    $ gem source
    *** CURRENT SOURCES ***
    
    https://rubygems.org
    http://ruby.taobao.org

`gem source`用法：

    $ gem source --help
      用法: gem sources [options]
    
      选项:
        -a, --add SOURCE_URI             添加gem源
        -l, --list                       列举gem源
        -r, --remove SOURCE_URI          删除gem源
        -c, --clear-all                  删除所有gem源，并清除源缓存
        -u, --update                     跟新源的缓存
        
      默认选项:
        --list    
##在bundle中更换gem源
    #source 'https://rubygems.org'
    source 'http://ruby.taobao.org'

##在本地运行gem服务器
[运行本地gem服务器](http://guides.rubygems.org/run-your-own-gem-server/)
使用内建的`gem server`命令，可以将本地已安装的所有gem包通过