#搭建git 服务器
---
####git服务器搭建分以下几个步骤


>服务器端配置

* 安装git

		sudo apt-get install git

* 创建git 用户 用于运行git 服务

		sudo adduser git

* 创建 git 裸仓库

		 sudo git init --bare gitname.git

* 修改仓库权限为git用户

		sudo chown -R git:git gitname.git

-----------
> 客户端配置

* 设置ssh-kengen 公钥 （一路回车）（已有秘钥请忽略）

		ssh-keygen -t rsa -C "email@email.com"

* 上传 id_ras.pub 公钥

		scp id_rsa.pub git@server:~/	
  服务器端git用户登录执行

		cd ~/.ssh || ( mkdir ~/.ssh && cd ~/.ssh )

		cat ../id_rsa.pub >> ./authorized_keys

		chmod 600 authorized_keys

		chmod 700 ../ssh
		
		
* ssh 远程连接git服务器

		git init 
		
		git remote add origin ssh://git@servername.com:/git/gitname.git
		
* 远程克隆git服务器

		git clone ssh://git@servername.com:/git/gitname.git
		
---

####这样就大功告成了

>接下来我们搞搞git的自动化部署

* 创建web目录

		mkdir /var/www
* 编写git 钩子

		cd /git/gitname.git/hooks
		
		vi post-receive
		
  编写以下内容
  		
		#!/bin/bash
  		
		git --work-tree=/var/www checkout -f
		 
#####自动化部署也ok了
你本地每次 push mater 分支的时候 远程服务器中得代码会自动更新到web目录中去。

好开心啊每次提交到远程仓库就会把最新的代码部署到服务器中去，妈妈再也不用担心我上传同步代码了，以后push一下代码就会上线了。
  		



	


