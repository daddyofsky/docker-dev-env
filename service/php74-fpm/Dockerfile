FROM php:7.4-fpm-alpine3.15
WORKDIR /opt/work/php
WORKDIR /home/www

RUN apk update \
    && apk add --no-cache bash \
    	php7-opcache php7-mysqli php7-pdo_mysql php7-gmp php7-gd php7-xdebug \
    && echo "zend_extension=/usr/lib/php7/modules/opcache.so" > /usr/local/etc/php/conf.d/opcache.ini \
    && echo "zend_extension=/usr/lib/php7/modules/mysqli.so" > /usr/local/etc/php/conf.d/mysqli.ini \
    && echo "zend_extension=/usr/lib/php7/modules/pdo_mysql.so" > /usr/local/etc/php/conf.d/pdo_mysql.ini \
    && echo "zend_extension=/usr/lib/php7/modules/gmp.so" > /usr/local/etc/php/conf.d/gmp.ini \
    && echo "zend_extension=/usr/lib/php7/modules/gd.so" > /usr/local/etc/php/conf.d/gd.ini \
    && echo "zend_extension=/usr/lib/php7/modules/xdebug.so" > /usr/local/etc/php/conf.d/xdebug.ini

CMD ["php-fpm"]
