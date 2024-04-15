FROM php:7.4-fpm-alpine3.15
WORKDIR /opt/work/php
WORKDIR /home/www

RUN mkdir /usr/lib/php7 && ln -s /usr/local/lib/php/extensions/no-debug-non-zts-20190902 /usr/lib/php7/modules

RUN apk update
RUN apk add bash
RUN apk add php7-mysqli php7-pdo_mysql
RUN apk add php7-gmp
RUN apk add php7-gd
RUN apk add php7-xdebug
RUN docker-php-ext-enable opcache mysqli pdo_mysql gmp gd xdebug

CMD ["php-fpm"]
