---
layout: post
title:  "Mac 使用Github Pages搭建博客"
category: dev
---

## 在GitHub上创建username.github.io的仓库
这一步按照Github Docs顺利完成

## 本地按照Ruby和jekyll
Mac上自带一个2.6版本的Ruby，但是后续安装bundle时，由于Mac默认禁止修改Ruby目录下的内容，会导致安装bundle失败。一个推荐的解决方法是安装另一个独立的Ruby版本，在该版本下运行jekyll。可以参见[](https://stackoverflow.com/questions/51126403/you-dont-have-write-permissions-for-the-library-ruby-gems-2-3-0-directory-ma).

这里选择使用chruby and ruby-install安装一个新版本的Ruby。在使用ruby-install ruby安装最新稳定版Ruby时，遇到curl: (92) HTTP/2 stream 0 was not closed cleanly: PROTOCOL_ERROR (err 1),这是由于Ruby的下载站点较远，多试几次就好了。下载完Ruby进行安装时，会出现Configuration of ruby 3.1.2 failed! Error的报错，这是因为尽管chruby and ruby-install都需要xz包，但是两者却没有将其显式指为依赖。运行下面的命令便可以解决，参见[](https://networkcult.com/configuration-of-ruby-3-1-2-failed-error-6607/)
```
brew install xz
```
完成Ruby的安装后，将需要在.zsrc中做相应的配置，可以参见[](https://mac.install.guide/ruby/12.html)
```
### ~/.zshrc~
# enable chruby
source /usr/local/share/chruby/chruby.sh
source /usr/local/share/chruby/auto.sh
chruby ruby-3.1.2
```
此时系统中存在两个版本的Ruby，会默认使用系统自带的版本。有以下方法可以切换到指定的版本，可以参见[](https://blog.csdn.net/lamp113/article/details/78733521)
- 在命令行中使用chruby ruby-3.1.2
- 在`.zshrc`中添加`chruby ruby-3.1.2`，则终端会默认使用配置的版本
- 在项目目录下添加一个文件.ruby-version，文件内添加一行`ruby-3.1.2`，在此目录下会使用配置的版本。

记得修改完`.zshrc`,要关闭并重新打开终端。

## 安装bundle和jekyll
```
gem install jekyll bundler
```
安装完成后，在项目目录下执行以下命令，创建一个默认的jekyll站点。
```
jekyll new . --force
```
ruby-3.1.2版本会依赖于webrick，直接启动jekyll，会报错：bundler: failed to load command: jekyll，可以使用以下命令解决：
```
bundle add webrick
```
然后执行命令：
```
bundle exec jekyll serve
```




