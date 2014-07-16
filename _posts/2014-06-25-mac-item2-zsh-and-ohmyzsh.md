---
layout: post
title:  "Iterm2和zsh"
date:   2014-06-25
categories: Mac Iterm2
---

###Mac Item2 配置zsh 和 oh my zsh

[参考](https://github.com/robbyrussell/oh-my-zsh#readme)

我是采用的自己clone方式安装的，因为没有wget，呜呜呜

1. clone git 地址

		git clone git://github.com/robbyrussell/oh-my-zsh.git ~/.oh-my-zsh
	
2. 拷贝oh-my-zsh中的template来创建新的.zshrc文件

		cp ~/.oh-my-zsh/templates/zshrc.zsh-template ~/.zshrc

3. 设置默认的shell，有/bin/sh 修改为/bin/zsh

		chsh -s /bin/zsh
		
4. 重启shell

		
就可以了。。。。

* PS，以后的需要在iterm2中使用的环境变量，需要在~/.zshrc中设置，而不是/etc/.bashrc了
  