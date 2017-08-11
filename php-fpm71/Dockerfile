#php 71 base
FROM shopex/centos6.8
MAINTAINER zhangxuehui <zhangxuehui@shopex.cn>
ENV PHP_VERSION 71
ENV PHP_PATH /usr/local/php${PHP_VERSION}
ENV PHP_EXT_PATH ${PHP_PATH}/etc/php.d
#install php-fpm
RUN yum install php-fpm${PHP_VERSION} -y
RUN yum install php-redis${PHP_VERSION} -y
RUN yum install php-amqp${PHP_VERSION} -y
RUN yum install php-libzookeeper${PHP_VERSION} -y
RUN yum install php-mongodb${PHP_VERSION} -y
RUN yum install php-msgpack${PHP_VERSION} -y
RUN yum install php-swoole${PHP_VERSION} -y
RUN yum install php-zookeeper${PHP_VERSION} -y

RUN sed -i 's/127.0.0.1:9000/[::]:9000/g' "$PHP_PATH/etc/php-fpm.d/www.conf"
RUN sed -i 's/;daemonize = yes/daemonize = no/g' "$PHP_PATH/etc/php-fpm.conf"
RUN sed -i 's/ = 128/ = 5/g' "$PHP_PATH/etc/php-fpm.d/www.conf"
RUN sed -i 's/listen.allowed_clients/;listen.allowed_clients/g' "$PHP_PATH/etc/php-fpm.d/www.conf"

RUN sed -i 's/display_errors = Off/display_errors = On/g' "$PHP_PATH/etc/php.ini"

RUN ln -s /usr/local/php${PHP_VERSION}/sbin/php-fpm /usr/sbin/php-fpm
RUN ln -s /usr/local/php${PHP_VERSION}/bin/php /usr/sbin/php

ENTRYPOINT ["php-fpm"]