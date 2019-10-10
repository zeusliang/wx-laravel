FROM php:7.3.9-apache-stretch
# server configure
COPY  ${PWD}/server-cnf/sources.list /etc/apt/sources.list
# copy certicate
COPY ${PWD}/server-cnf/000-default.conf /etc/apache2/sites-enabled/000-default.conf
# 镜像助手
COPY  ${PWD}/server-cnf/set_grant /var/www/html
COPY  ${PWD}/server-cnf/pdo_ext /var/www/html
# 部署项目
ADD ${PWD}/wx-dev-laravel.tar.gz_aa /var/www/html
# 安装composer
RUN mv wx-dev-laravel/composer /usr/bin/composer; \
	chmod +x /usr/bin/composer; \ 
# 设置端口
	# 设置监听端口
	echo "Listen 8080" >> /etc/apache2/ports.conf; \
# 开启apache路由重写模块
	ln -s /etc/apache2/mods-available/rewrite.load /etc/apache2/mods-enabled/rewrite.load; \
# 设置权限
	./set_grant; \
# 添加pdo扩展
	./pdo_ext;
# 设置逻辑卷
VOLUME '/var/www/html/'
EXPOSE 8080