FROM php:8.2-fpm-alpine
WORKDIR /opt/work/php
WORKDIR /home/www

RUN mkdir /usr/lib/php82 && ln -s /usr/local/lib/php/extensions/no-debug-non-zts-20220829 /usr/lib/php82/modules

RUN apk update
RUN apk add bash
RUN apk add php82-mysqli php82-pdo_mysql
RUN apk add php82-gmp
RUN apk add php82-gd
RUN apk add php82-xdebug
RUN docker-php-ext-enable opcache mysqli pdo_mysql gmp gd xdebug

CMD ["php-fpm"]
