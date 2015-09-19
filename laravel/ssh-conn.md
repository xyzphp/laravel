linux 服务器配置 + ssh 无密码登陆
================================

#服务器配置

1.添加管理员用户

>		adduser admin

2.给用户添加sudo能力
>编辑 sudoers 文件
	
> 		vim /etc/sudoers

> "root	ALL=(ALL:ALL) ALL"  下加一下代码

>		admin	ALL=(ALL:ALL) ALL

3.更新系统
		
>		apt-get update

>		apt-get upgrade

# ssh 无密码登陆

1.修改SSH配置 提升安全性

> 备份ssh 配置文件

>		cp /etc/ssh/sshd_config /etc/ssh/sshd_config.bak

>编辑ssh 配置文件

>		vim /etc/ssh/sshd_config

>修改的配置项

>		Port 2002 #修改默认的22登录端口号为你想要的登陆端口，最好是大于1024，我选择2002

>		PermitRootLogin no #禁止root用户登陆

>		PasswordAuthentication no #禁止使用密码认证

>		PermitEmptyPasswords no #禁止空密码登录

>		StrictModes yes # 检查密钥的用户和权限是否正确，默认打开的

>		RSAAuthentication yes # 启用 RSA 认证

>		PubkeyAuthentication yes # 启用公钥认证

>		ServerKeyBits 1024 # 将ServerKey强度改为1024比特

2.设置RSA公钥（非服务器执行 直接回车就可以）

>		cd ~/.ssh || ( mkdir ~/.ssh && cd ~/.ssh )

>如果只连接服务器

>		ssh-keygen -t rsa

>如果连接服务器 或者 github

>		ssh-keygen -t rsa -C "emai@email.com"

>此时会生成两个文件 id_rsa  和 id_rsa.pub 
>>如果你是想要连接github 上的服务器时 执行下面的命令 复制输出的结果到github即可

>>>		cat id_rsa.pub

>>如果要连接远程服务器 执行下列命令 将username 和ip 换成你对应的username 和ip
		
>>>		scp id_rsa.pub username@192.168.0.1:~/

3.切换连接到远程服务器 配置公钥 和权限

>		ssh username@192.168.0.1
		
>		cd ~/.ssh || ( mkdir ~/.ssh && cd ~/.ssh )

>		cat ../id_rsa.pub >> ./authorized_keys

>		chmod 600 authorized_keys

>		chmod 700 ../ssh

4.重启 ssh 服务
		
>		sudo service ssh restart
		
5.大功告成









