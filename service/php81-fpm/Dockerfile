FROM php:8.1-fpm-alpine
WORKDIR /opt/work/php
WORKDIR /home/www

RUN apk update \
    && apk add --no-cache bash \
    	php81-opcache php81-mysqli php81-pdo_mysql php81-gmp php81-gd php81-xdebug \
    && echo "zend_extension=/usr/lib/php81/modules/opcache.so" > /usr/local/etc/php/conf.d/opcache.ini \
    && echo "zend_extension=/usr/lib/php81/modules/mysqli.so" > /usr/local/etc/php/conf.d/mysqli.ini \
    && echo "zend_extension=/usr/lib/php81/modules/pdo_mysql.so" > /usr/local/etc/php/conf.d/pdo_mysql.ini \
    && echo "zend_extension=/usr/lib/php81/modules/gmp.so" > /usr/local/etc/php/conf.d/gmp.ini \
    && echo "zend_extension=/usr/lib/php81/modules/gd.so" > /usr/local/etc/php/conf.d/gd.ini \
    && echo "zend_extension=/usr/lib/php81/modules/xdebug.so" > /usr/local/etc/php/conf.d/xdebug.ini

CMD ["php-fpm"]
