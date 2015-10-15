#git小技巧和窍门
---

###git命令的自动补全

你是不是对git命令感觉敲起来很麻烦，你是不是有时候会忘掉命令的拼写。别着急，让我来告诉你一个好玩的东东。这就是 git 命令自动补全。由于我用的是mac 操作系统所以我只写一下mac如何给git配置自动补全功能。
哈哈！妈妈再也不用担心我敲代码手残了。

1. 安装  bash-completion 工具  （已安装就忽略这一步）
	
			brew istall bash-completion       //brew包管理工具就是牛，一行代码搞定。
	
2. 查看 bash-completion  工具的配置信息 

			brew info bash-completion 

			=======复制信息中的下面这句话====（以系统输出为准）======

			if [ -f $(brew --prefix)/etc/bash_completion ]; then
				. $(brew --prefix)/etc/bash_completion
			fi


3. 把第二步的复制出来的代码添加入 .bash_profile 文件中并保存

			vi ~/.bash_profile 
			
4. 克隆git源码

			git clone https://github.com/git/git.git	
5. 找到  git-completion.bash  脚本并复制到家目录	

			cp git/contrib/completion/git-completion.bash ~/.git-completion.bash

6. 修改 .bashrc文件 （没有则创建该文件）

			vi  ~/.bashrc
			
			++++++++添加下面的代码+++++++++++
			
			source ~/.git-completion.bash
			
7. 重启终端


####哈哈！大功告成，可以试试了，git 用起来 特别爽。

-----
	

			
	

	



