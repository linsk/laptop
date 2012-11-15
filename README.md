#Introduction
This repository was forked from https://github.com/thoughtbot/laptop.

Since I'm using bash, rather than zsh, I have to modify script to suit my needs.

> * Download and install XCode, and the [Command Line Tools for XCode](https://developer.apple.com/downloads/index.action).
> * ``` bash < <(curl -s https://raw.github.com/xiaolai/laptop/master/mac-port-way) ```
> OR:
> * ``` bash < <(curl -s https://raw.github.com/xiaolai/laptop/master/mac-brew-way) ```
> **NOTE**:  XCode is essentially not needed if you only want to play with ruby and rails...

Though most favor HomeBrew over MacPorts, I found it's much easier and less problematic to use [MacPorts](http://macports.org/).

--

#天朝优化
将 Ruby 下载地址和 Gem sources 的镜像替换成淘宝提供的节点 http://ruby.taobao.org
原文在http://ruby-china.org/wiki/install_ruby_guide
其中有两个小问题，

1. 
$ sed -i 's/ftp\.ruby-lang\.org\/pub\/ruby/ruby\.taobao\.org\/mirrors\/ruby/g' ~/.rvm/config/db
这一行在Mountain Lion中是出错的，改为:
$ sed -ig 's/ftp\.ruby-lang\.org\/pub\/ruby/ruby\.taobao\.org\/mirrors\/ruby/' ~/.rvm/config/db

2.
$ gem source -r https://rubygems.org/
至少我的情况默认文件是「http://rubygems.org/」所以是匹配不到，不太清楚是不是有的是https版本，所以加上一行
$ gem source -r http://rubygems.org/

#NOTE

The following code will solve the problem : ["OpenSSL Errors and Rails – Certificate Verify Failed – Gem::RemoteFetcher::FetchError"](http://railsapps.github.com/openssl-certificate-verify-failed.html)

```
# Install openssl
echo "Install openssl..."
brew install openssl
brew link openssl
# download cert.pem file for openssl
cd /usr/local/etc/openssl/certs/
sudo curl -O http://curl.haxx.se/ca/cacert.pem
sudo mv cacert.pem cert.pem
cd -
echo "
# cert.pem file for openssl 
export SSL_CERT_FILE=/usr/local/etc/openssl/certs/cert.pem" >> ~/.bash_profile
source ~/.bash_profile
```

# Batch scripts for Ruby production environment install on Ubuntu Server.
```
 ______              __           __
/\__  _\          __/\ \__       /\ \
\/_/\ \/     ___ /\_\ \ ,_\      \_\ \
   \ \ \   /' _ `\/\ \ \ \/      /'_` \
    \_\ \__/\ \/\ \ \ \ \ \_  __/\ \L\ \
    /\_____\ \_\ \_\ \_\ \__\/\_\ \___,_\
    \/_____/\/_/\/_/\/_/\/__/\/_/\/__,_ /
```		
https://github.com/huacnlee/init.d


--

Laptop
======

Laptop is a script to set up a Mac OS X laptop for Rails development.

Requirements
------------

* Install a C compiler, such as GCC, LLVM, or Clang.

Download a compiler from the [OS X GCC Installer](https://github.com/kennethreitz/osx-gcc-installer/) if you're on Snow Leopard (OS X 10.6) or use the [Command Line Tools for XCode](https://developer.apple.com/downloads/index.action) for Lion (OS X 10.7) or Mountain Lion (OS X 10.8).

* Set zsh as your login shell.

To change your login shell run this from a Terminal:

    chsh -s /bin/zsh

Install
-------

Run the script:

    zsh < <(curl -s https://raw.github.com/thoughtbot/laptop/master/mac)

What it sets up
---------------

* Ack for finding things in files
* Bundler gem for managing Ruby libraries
* Foreman gem for serving Rails apps locally
* Heroku gem for interacting with the Heroku API
* Heroku Config plugin for local `ENV` variables
* Homebrew for managing operating system libraries
* ImageMagick for cropping and resizing images
* Postgres for storing relational data
* Postgres gem for talking to Postgres from Ruby
* Qt for headless JavaScript testing via Capybara Webkit
* Rails gem for writing web applications
* Ruby stable for writing general-purpose code
* RVM for managing versions of the Ruby programming language
* SSH public key for authenticating with Github and Heroku
* Tmux for saving project state and switching between projects

It should take less than 30 minutes to install (depends on your machine).

Credits
-------

![thoughtbot](http://thoughtbot.com/images/tm/logo.png)

Laptop is maintained and funded by [thoughtbot, inc](http://thoughtbot.com/community).

Thank you to all [the contributors](https://github.com/thoughtbot/laptop/contributors)!

The names and logos for thoughtbot are trademarks of thoughtbot, inc.

License
-------

Laptop is Copyright © 2011-2012 thoughtbot, inc. It is free software, and may be
redistributed under the terms specified in the LICENSE file.
