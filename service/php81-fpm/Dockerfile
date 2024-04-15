FROM php:8.1-fpm-alpine
WORKDIR /opt/work/php
WORKDIR /home/www

RUN mkdir /usr/lib/php81 && ln -s /usr/local/lib/php/extensions/no-debug-non-zts-20210902 /usr/lib/php81/modules

RUN apk update
RUN apk add bash
RUN apk add php81-mysqli php81-pdo_mysql
RUN apk add php81-gmp
RUN apk add php81-gd
RUN apk add php81-xdebug
RUN docker-php-ext-enable opcache mysqli pdo_mysql gmp gd xdebug

CMD ["php-fpm"]
