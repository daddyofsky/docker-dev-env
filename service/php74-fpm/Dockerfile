FROM php:7.4-fpm-alpine
WORKDIR /opt/work/php
WORKDIR /home/www

RUN apk update \
    && apk add --no-cache bash \
    	gmp gmp-dev \
    	zlib-dev libpng libpng-dev libjpeg libjpeg-turbo-dev freetype freetype-dev \
    	--virtual .build-deps $PHPIZE_DEPS \
    && docker-php-ext-configure gd --with-freetype=/usr/include/ --with-jpeg=/usr/include/ \
    && docker-php-ext-install mysqli pdo_mysql opcache gmp gd \
	&& pecl install xdebug && docker-php-ext-enable xdebug \
    && apk del .build-deps

CMD ["php-fpm"]
