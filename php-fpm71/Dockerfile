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
RUN yum install php-mongodb${PHP_VERSION} -y
RUN yum install php-msgpack${PHP_VERSION} -y
RUN yum install php-swoole${PHP_VERSION} -y

RUN ln -s /usr/local/php${PHP_VERSION}/sbin/php-fpm /usr/sbin/php-fpm
RUN ln -s /usr/local/php${PHP_VERSION}/bin/php /usr/sbin/php

CMD ["php-fpm"]