FROM php:5.6-fpm-alpine
WORKDIR /opt/work/php
WORKDIR /home/www

RUN mkdir /usr/lib/php5 && ln -s /usr/local/lib/php/extensions/no-debug-non-zts-20131226 /usr/lib/php5/modules

RUN apk update \
    && apk add --no-cache bash \
    	php5-mysql php5-mysqli php5-pdo_mysql php5-gmp php5-mcrypt php5-gd php5-iconv \
    	--virtual .build-deps $PHPIZE_DEPS \
	&& pecl install xdebug-2.5.5 \
    && docker-php-ext-enable opcache mysql mysqli pdo_mysql gmp mcrypt gd xdebug

# fix iconv bug
RUN apk add --no-cache --repository http://dl-cdn.alpinelinux.org/alpine/v3.13/community/ --allow-untrusted gnu-libiconv
ENV LD_PRELOAD /usr/lib/preloadable_libiconv.so php

CMD ["php-fpm"]
