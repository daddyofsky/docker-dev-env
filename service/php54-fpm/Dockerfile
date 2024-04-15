#FROM yeszao/php:5.4.45-fpm-alpine
FROM greencape/php:5.4-fpm-alpine
WORKDIR /opt/work/php
WORKDIR /home/www

RUN mkdir /usr/lib/php5 && ln -s /usr/local/lib/php/extensions/no-debug-non-zts-20100525 /usr/lib/php5/modules

RUN apk update
RUN apk add bash
RUN apk add gmp-dev mariadb-dev libmcrypt-dev
RUN apk add zlib-dev libpng libpng-dev libjpeg libjpeg-turbo-dev freetype freetype-dev
RUN apk add --virtual .build-deps $PHPIZE_DEPS
RUN docker-php-ext-configure gd --with-freetype-dir=/usr/lib/ --with-jpeg-dir=/usr/lib/
RUN docker-php-ext-install mysql mysqli pdo_mysql gmp mcrypt gd
RUN pecl install ZendOpcache-7.0.5 xdebug-2.4.1
RUN docker-php-ext-enable opcache xdebug gmp mcrypt gd

# fix iconv bug
RUN apk add --repository http://dl-cdn.alpinelinux.org/alpine/v3.13/community/ --allow-untrusted gnu-libiconv
ENV LD_PRELOAD /usr/lib/preloadable_libiconv.so php

CMD ["php-fpm"]
