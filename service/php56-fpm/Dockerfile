FROM php:5.6-fpm-alpine
WORKDIR /opt/work/php
WORKDIR /home/www

RUN apk update \
    && apk add --no-cache bash \
    	php5-opcache php5-mysqli php5-pdo_mysql php5-gmp php5-gd \
    	--virtual .build-deps $PHPIZE_DEPS \
    && echo "zend_extension=/usr/lib/php5/modules/opcache.so" > /usr/local/etc/php/conf.d/opcache.ini \
    && echo "zend_extension=/usr/lib/php5/modules/mysqli.so" > /usr/local/etc/php/conf.d/mysqli.ini \
    && echo "zend_extension=/usr/lib/php5/modules/pdo_mysql.so" > /usr/local/etc/php/conf.d/pdo_mysql.ini \
    && echo "zend_extension=/usr/lib/php5/modules/gmp.so" > /usr/local/etc/php/conf.d/gmp.ini \
    && echo "zend_extension=/usr/lib/php5/modules/gd.so" > /usr/local/etc/php/conf.d/gd.ini \
	&& pecl install xdebug-2.5.5 && docker-php-ext-enable xdebug

CMD ["php-fpm"]
