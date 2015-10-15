---
layout: post
title:  "Install oh-my-zsh on your Centos Vagrant box"
author: Peter Wilkins
date:   2015-10-15
permalink: zsh-on-vagrant
comments: true
---

ssh in with `vagrant ssh`

next get zsh with `yum install zsh`

get oh-my-zsh `sh -c "$(wget https://raw.github.com/robbyrussell/oh-my-zsh/master/tools/install.sh -O -)"`

turn it on `chsh -s /bin/zsh` password is `vagrant`

[More info and configuration options here](https://github.com/robbyrussell/oh-my-zsh)
