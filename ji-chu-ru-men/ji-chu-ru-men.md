# 基础入门

这是一个教你如何将 Travis Ci 和 Github 仓库一起使用的简短教程。如果你不熟悉持续集成或者想要了解关于 Travis Ci 的更多文档信息，可以从 [初学者的核心概念](https://docs.travis-ci.com/user/for-beginners) 开始了解。

## 前置条件

在使用 Travis CI 之前，先确认你具有以下条件：

* 一个 [GitHub](https://github.com/) 账户
* [在 GitHub 上托管](https://help.github.com/categories/importing-your-projects-to-github/)一个属于自己的项目

## 开始使用 Travis CI

1. 前往 [travis-cli.com](https://travis-ci.com/) 并使用 [GitHub 账户登录](https://travis-ci.com/signin)。

2. 同意授权给 Travis CI，你将会重定向到 GitHub 网站上。

3. 点击绿色的同意按钮，选择一个你想要使用 Travis CI 的项目仓库。

4. 添加一个 `.travis.yml` 文件到你的项目中告诉 Travis CI 想要做什么，下面这个示例展示了一个 Ruby 项目指定用 Ruby 2.2 版本和最新的 JRuby 版本来构建项目。

```YAML
.travis.yml

language: ruby
rvm:
 - 2.2
 - jruby
```

这个默认的配置会执行 `bundle install` 来[安装依赖](https://docs.travis-ci.com/user/customizing-the-build/#Customizing-the-Installation-Step)，以及执行 `rake` 来构建项目。

1. 将 `.travis.yml` 提交到 git 上，触发 Travis CI 构建：

> 只有当你的项目提交了 `travis.yml` 文件之后才会在你每一次提交代码时触发构建

1. 通过访问 [travis-ci.com 构建状态页面](https://travis-ci.com/auth)，选择对应的仓库，根据构建命令返回的状态来检查构建的结果[成功与否](https://docs.travis-ci.com/user/customizing-the-build/#Breaking-the-Build)。

## 选择不同的编译语言

使用以下常用语言之一：

.travis.yml

```YAML
language: ruby
```

```YAML
language: java
```

```YAML
language: node_js
```

```YAML
language: python
```

```YAML
language: php
```

或者从[完整列表](https://docs.travis-ci.com/user/languages/)列表中选择一个。

## 选择基础结构（可选）

确定构建运行基础结构的最佳方式就是设置 `language`。如果你这么做了，那么你将安装默认的基础结构来构建运行（少数例外），基础的运行容器环境是 Ubuntu 14.04 版本。你可以通过添加 `sudo: false` 到 `.travis.yml` 文件中来明确的指定默认的基础结构配置。

* 如果你需要在虚拟机中运行更多的自定义设置，你可以开启 Sudo 配置：

```YAML
sudo: enabled
```

* 如果你需要在 macOs 中运行测试，或者你的项目使用的是 Swift 或 Object-C 语言，那么你可以使用我们的 OS X 环境：

```YAML
os: osx
```

> 通常情况下即使你在 Mac OS 上开发项目，你也是不需要使用 OS X 环境的，只有当你使用 Swift, Object-C 开发项目或者有用到 macOS 专用软件时，才需要指定 OS X 虚拟环境。

## 不仅仅是运行测试

Travis CI 不仅仅是运行测试，它还可以为你的代码做很多事，比如：

* 部署 [GitHub 页面](https://docs.travis-ci.com/user/deployment/pages/)
* 在 [Heroku](https://docs.travis-ci.com/user/deployment/heroku/) 上运行应用
* 更新 [RubyGems](https://docs.travis-ci.com/user/deployment/rubygems/)
* 发送 [notifications](https://docs.travis-ci.com/user/notifications/)

## 进一步阅读

了解更多

* [自定义你的构建](https://docs.travis-ci.com/user/customizing-the-build)
* [安全最佳实践](https://docs.travis-ci.com/user/best-practices-security/)
* [构建版本](https://docs.travis-ci.com/user/build-stages/)
* [构建模型](https://docs.travis-ci.com/user/customizing-the-build/#Build-Matrix)
* [安装依赖](https://docs.travis-ci.com/user/installing-dependencies)
* [建立数据库](https://docs.travis-ci.com/user/database-setup/)



