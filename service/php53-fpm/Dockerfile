FROM iwatth/php:5.3-fpm-alpine
WORKDIR /opt/work/php
WORKDIR /home/www

RUN apk update \
    && apk add --no-cache bash \
    	gmp-dev mariadb-dev \
    	zlib-dev libpng libpng-dev libjpeg libjpeg-turbo-dev freetype freetype-dev \
    	--virtual .build-deps $PHPIZE_DEPS \
    && docker-php-ext-configure gd --with-freetype=/usr/include/ --with-jpeg=/usr/include/ \
	&& docker-php-ext-install mysql mysqli pdo_mysql gmp gd \
	&& pecl install ZendOpcache-7.0.5 xdebug-2.2.7 && docker-php-ext-enable opcache xdebug gmp gd

CMD ["php-fpm"]
