# LEMP
#   CentOS 7
#   Nginx
#   MariaDB
#   PHP-fpm 7

FROM centos:7
LABEL  maintainer "okapiffxiv"

# env
RUN yum update -y && \
    yum clean all && \
    yum -y install epel-release zip unzip bash gcc gcc-c++ make libpng-devel wget

# Nginx
COPY ./nginx.repo /etc/yum.repos.d/nginx.repo
RUN yum -y --enablerepo=nginx install nginx && \
    yum clean all && \
    systemctl enable nginx.service
COPY ./default.conf /etc/nginx/conf.d/default.conf

# PHP
RUN wget http://rpms.famillecollet.com/enterprise/remi-release-7.rpm
RUN rpm -Uvh ./remi-release-7.rpm
RUN yum -y install --enablerepo=remi,remi-php70 php php-devel php-mbstring php-pdo php-gd php-fpm php-mysql php-xml --skip-broken && \
    yum clean all
COPY ./php.ini /etc/php.ini
COPY ./www.conf /etc/php-fpm.d/www.conf
RUN systemctl enable php-fpm.service

# MariaDB
RUN yum -y install mariadb mariadb-server && \
    yum clean all && \
    systemctl enable mariadb.service

# composer & npm
RUN curl -sL https://rpm.nodesource.com/setup_8.x | bash -
RUN yum install -y nodejs which libpng-devel pngquant && \
    yum clean all
RUN npm install -g n
RUN php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');"
RUN php composer-setup.php
RUN rm -rf composer-setup.php
RUN mv composer.phar /usr/local/bin/composer

RUN echo "<?php echo phpinfo(); ?>" > /var/www/html/index.php
