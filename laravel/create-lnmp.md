lnmp环境的搭建
===============

1.安装软件前更新apt-get

		apt-get update

2.安装软件 vim nginx mysql-server mysql-client

		apt-get install vim

		apt-get install nginx

		apt-get install mysql-server mysql-client

3.安装php-fpm
		
		apt-get install php5-fpm

4.配置nginx
	
		cd /etc/nginx/conf.d/
		
		vim www.conf

5.编写nginx配置文件

		server {
	        listen 80 default_server;
	        listen [::]:80 default_server ipv6only=on;

	        root /usr/share/nginx/html;
	        index index.html index.htm;

	        server_name localhost;

	        location / {
	                try_files $uri $uri/ =404;
	        }

	        location ~ \.php$ {
	                fastcgi_split_path_info ^(.+\.php)(/.+)$;
	                # NOTE: You should have "cgi.fix_pathinfo = 0;" in php.ini

	                # With php5-cgi alone:
	        		# fastcgi_pass 127.0.0.1:9000;
	                # With php5-fpm:
	                fastcgi_pass unix:/var/run/php5-fpm.sock;
	                fastcgi_index index.php;
	                include fastcgi_params;
	        }
	        location ~ /\.ht {
	                deny all;
	        }
		}
6.编写info.php

		cd /usr/share/nginx/html

		echo "<?php phpinfo(); ?>" >> info.php

7.通过浏览器访问
		
		localhost/info.php

8.加php扩展

		apt-get install php5-curl
		apt-get install php5-gd
		apt-get install php5-intl
		apt-get install php-pear
		apt-get install php5-imagick
		apt-get install php5-imap
		apt-get install php5-mcrypt
		apt-get install php5-common
		apt-get install php5-pspell
		apt-get install php5-recode 
		apt-get install php5-snmp
		apt-get install php5-sqlite
		apt-get install php5-tidy
		apt-get install php5-xmlrpc
		apt-get install php5-xsl
		apt-get install php5-memcached

		cd /etc/php5/fpm/conf.d
		ln -s /ete/php5/mods-available/mcrypt.ini ./20-mcrypt.ini
	
8.lnmp环境搭建完成