FROM php:8.0-fpm-alpine
WORKDIR /opt/work/php
WORKDIR /home/www

RUN mkdir /usr/lib/php8 && ln -s /usr/local/lib/php/extensions/no-debug-non-zts-20200930 /usr/lib/php8/modules

RUN apk update \
    && apk add --no-cache bash \
    	php8-mysqli php8-pdo_mysql php8-gmp php8-gd php8-xdebug \
    && docker-php-ext-enable opcache mysqli pdo_mysql gmp gd xdebug

CMD ["php-fpm"]
