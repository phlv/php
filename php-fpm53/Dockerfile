#php 53 base
FROM shopex/centos6.8
MAINTAINER zhangxuehui <zhangxuehui@shopex.cn>
ENV PHP_VERSION 53
ENV PHP_PATH /usr/local/php${PHP_VERSION}
ENV PHP_EXT_PATH ${PHP_PATH}/etc/php.d
#install php-fpm
RUN yum install php-fpm${PHP_VERSION} -y
RUN yum install Zend${PHP_VERSION}  -y
RUN yum install php-memcached${PHP_VERSION} -y
RUN yum install php-memcache${PHP_VERSION} -y
RUN yum install php-mongo${PHP_VERSION} -y
RUN yum install php-redis${PHP_VERSION} -y
RUN yum install php-swoole${PHP_VERSION} -y
RUN yum install php-amqp${PHP_VERSION} -y

RUN echo "zend_loader.license_path='/data/httpd/docker/php/php-fpm53/etc/'" >>  /usr/local/php53/etc/php.d/Zend.ini
RUN sed -i 's/127.0.0.1:9000/9000/g' "$PHP_PATH/etc/php-fpm.conf"
RUN sed -i 's/;daemonize = yes/daemonize = no/g' "$PHP_PATH/etc/php-fpm.conf"
RUN sed -i 's/display_errors = Off/display_errors = On/g' "$PHP_PATH/etc/php.ini"
RUN sed -i 's/ = 128/ = 5/g' "/usr/local/php53/etc/php-fpm.conf"

RUN ln -s /usr/local/php${PHP_VERSION}/sbin/php-fpm /usr/sbin/php-fpm
RUN ln -s /usr/local/php${PHP_VERSION}/bin/php /usr/sbin/php

COPY libmysqlclient.so.18 /usr/local/php53/lib/libmysqlclient.so.18
RUN echo "/usr/local/php53/lib/" >>/etc/ld.so.conf
RUN ldconfig

COPY php-fpm.sh /usr/sbin/php-fpm53
RUN chmod +x /usr/sbin/php-fpm53
ENTRYPOINT ["php-fpm53"]