FROM php:8.0-fpm-alpine
WORKDIR /opt/work/php
WORKDIR /home/www

RUN mkdir /usr/lib/php8 && ln -s /usr/local/lib/php/extensions/no-debug-non-zts-20200930 /usr/lib/php8/modules

RUN apk update
RUN apk add bash
RUN apk add php8-mysqli php8-pdo_mysql
RUN apk add php8-gmp
RUN apk add php8-gd
RUN apk add php8-xdebug
RUN docker-php-ext-enable opcache mysqli pdo_mysql gmp gd xdebug

CMD ["php-fpm"]
