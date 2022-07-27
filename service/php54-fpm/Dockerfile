FROM yeszao/php:5.4.45-fpm-alpine
WORKDIR /opt/work/php
WORKDIR /home/www

RUN mkdir /usr/lib/php5 && ln -s /usr/local/lib/php/extensions/no-debug-non-zts-20100525 /usr/lib/php5/modules

RUN apk update \
    && apk add --no-cache bash \
    	gmp-dev mariadb-dev \
    	zlib-dev libpng libpng-dev libjpeg libjpeg-turbo-dev freetype freetype-dev \
    	--virtual .build-deps $PHPIZE_DEPS \
    && docker-php-ext-configure gd --with-freetype=/usr/include/ --with-jpeg=/usr/include/ \
	&& docker-php-ext-install mysql mysqli pdo_mysql gmp gd \
	&& pecl install ZendOpcache-7.0.5 xdebug-2.4.1 && docker-php-ext-enable opcache xdebug gmp gd

# fix iconv bug
RUN apk add --no-cache --repository http://dl-cdn.alpinelinux.org/alpine/v3.13/community/ --allow-untrusted gnu-libiconv
ENV LD_PRELOAD /usr/lib/preloadable_libiconv.so php

CMD ["php-fpm"]
