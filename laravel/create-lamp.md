lamp环境的搭建
================
1. 切换root账号

		sudo su

2. 修改主机名

		vi /etc/hostname

3. 安装软件前更新apt-get

		apt-get update

4. 安装软件 vim apache2 mysql-server mysql-client

		apt-get install vim

		apt-get install apache2

		apt-get install mysql-server mysql-client

5. 安装mcrpt扩展

		apt-get install mcrypt

		apt-get install php5-mcrypt

		cd /etc/php5/apache2/conf.d/
		
		ln -s /etc/php5/mods-available/mcrypt.ini ./

6. 安装mysql扩展

		apt-get install php5-mysql

7. 重启apach

		apachectl restart

8. 站点默认路径是

		cd  /var/www/html

		vim info.php