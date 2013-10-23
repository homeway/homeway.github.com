---
layout: page
title: 前言
tagline: 《RSpec手册》
---
{% include JB/setup %}
[目录](/the-rspec-book)

本书使用ruby语言探索如何实践做BDD的敏捷开发。书中的许多源代码例子都是基于当时的ruby版本和gem版本所做的，因此要想运行流畅，最好按照指定版本去安装环境。当然，仅将书中的例子作为参考，使用最新版本去书写代码，也是值得鼓励的。
##Ruby and Gem Versions
* ruby-1.8.71
* rubygems-1.3.7
* rspec-2.0.0
* rspec-rails-2.0.0
* cucumber-0.9.2
* cucumber-rails-0.3.2
* database_cleaner-0.5.2 
* webrat-0.7.2
* selenium-client-1.2.18 
* rails-3.0.0
##代码下载
大部分源代码例子可以从[pragprog.com](http://pragprog.com/titles/achbd/source_code)下载。这些源文件都是按照章节序号分组的。

##如何阅读本书
* 第一部分

第三章开始，我们从一个实例教程开始学习描述特性，这是一个可以使用命令行来玩的逻辑游戏的简单例子。这可以让你快速体验RSpec和Cucumber，并感受一下使用RSpec实践BDD技术的方式。

* 第二部分

第十章开始是深入介绍BDD开发的背景和概念。你会更了解BDD深层概念，作为BDD历史的极限编程（XP)，以及为什么我们发现验收驱动测试（TDD）是一种非常好的设计和文档实践。

* 第三部分

当你读完前两部分，或原本对RSpec就有一些了解，你会在第十二章开始学习一些教深入的RSpec知识。这部分，包括很多例子，会增强对各种RSpec用法的理解。

* 第四部分

第十七章较详细介绍Cucumber。Cucumber是`Aslak Hellesøy`对 `Dan North`所写RBehave框架的重新实现。

* 第五部分

第十九章开始详细介绍了如何利用上述知识在Ruby On Rails中实践BDD。
