FROM php:5.6-fpm-alpine
WORKDIR /opt/work/php
WORKDIR /home/www

RUN apk update \
    && apk add --no-cache bash \
    	gmp-dev php5-opcache \
    	zlib-dev libpng libpng-dev libjpeg libjpeg-turbo-dev freetype freetype-dev \
    	--virtual .build-deps $PHPIZE_DEPS \
    && echo "zend_extension=/usr/lib/php5/modules/opcache.so" > /usr/local/etc/php/conf.d/opcache.ini \
    && docker-php-ext-configure gd --with-freetype=/usr/include/ --with-jpeg=/usr/include/ \
	&& docker-php-ext-install mysql mysqli pdo_mysql gmp gd \
	&& pecl install xdebug-2.5.5 && docker-php-ext-enable xdebug

CMD ["php-fpm"]
