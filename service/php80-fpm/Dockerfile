FROM php:8.0-fpm-alpine
WORKDIR /opt/work/php
WORKDIR /home/www

RUN apk update \
    && apk add --no-cache bash \
    	php8-opcache php8-mysqli php8-pdo_mysql php8-gmp php8-gd php8-xdebug \
    && echo "zend_extension=/usr/lib/php8/modules/opcache.so" > /usr/local/etc/php/conf.d/opcache.ini \
    && echo "zend_extension=/usr/lib/php8/modules/mysqli.so" > /usr/local/etc/php/conf.d/mysqli.ini \
    && echo "zend_extension=/usr/lib/php8/modules/pdo_mysql.so" > /usr/local/etc/php/conf.d/pdo_mysql.ini \
    && echo "zend_extension=/usr/lib/php8/modules/gmp.so" > /usr/local/etc/php/conf.d/gmp.ini \
    && echo "zend_extension=/usr/lib/php8/modules/gd.so" > /usr/local/etc/php/conf.d/gd.ini \
    && echo "zend_extension=/usr/lib/php8/modules/xdebug.so" > /usr/local/etc/php/conf.d/xdebug.ini

CMD ["php-fpm"]
