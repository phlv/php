#php 71 base
FROM shopex/centos6.8
MAINTAINER zhangxuehui <zhangxuehui@shopex.cn>
RUN yum install php-fpm71 -y 
RUN yum install php-redis71 -y
RUN yum install php-mongodb71 -y 
RUN yum install php-opcache71 -y 
RUN yum install php-swoole71 -y 
RUN yum install php-msgpack71 -y 
RUN yum install php-zookeeper71 -y
RUN yum install php-amqp71 -y 
RUN yum install php-libzookeeper71 -y 
CMD ["/etc/init.d/php-fpm71", "start"]