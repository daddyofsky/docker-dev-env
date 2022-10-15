FROM iwatth/php:5.3-fpm-alpine
WORKDIR /opt/work/php
WORKDIR /home/www

RUN mkdir /usr/lib/php5 && ln -s /usr/local/lib/php/extensions/no-debug-non-zts-20090626 /usr/lib/php5/modules

RUN apk update \
    && apk add --no-cache bash \
    	gmp-dev mariadb-dev libmcrypt-dev \
    	zlib-dev libpng libpng-dev libjpeg libjpeg-turbo-dev freetype freetype-dev \
    	--virtual .build-deps $PHPIZE_DEPS \
    && docker-php-ext-configure gd --with-freetype-dir=/usr/lib/ --with-jpeg-dir=/usr/lib/ \
	&& docker-php-ext-install mysql mysqli pdo_mysql gmp mcrypt gd \
	&& pecl install ZendOpcache-7.0.5 xdebug-2.2.7 && docker-php-ext-enable opcache xdebug gmp mcrypt gd

# fix iconv bug
RUN apk add --no-cache --repository http://dl-cdn.alpinelinux.org/alpine/v3.13/community/ --allow-untrusted gnu-libiconv
ENV LD_PRELOAD /usr/lib/preloadable_libiconv.so php

CMD ["php-fpm"]
