FROM php:8.1-fpm-alpine
WORKDIR /home/www

# basic
RUN apk update \
    && apk add --no-cache bash gmp gmp-dev \
	&& docker-php-ext-install mysqli pdo_mysql opcache gmp \
    && apk del gmp-dev

# gd
RUN apk add --no-cache zlib-dev libpng libpng-dev libjpeg libjpeg-turbo-dev freetype freetype-dev \
    && docker-php-ext-configure gd --with-freetype=/usr/include/ --with-jpeg=/usr/include/ \
    && docker-php-ext-install gd \
    && apk del zlib-dev libpng-dev libjpeg-turbo-dev freetype-dev

# xdebug
RUN apk add --no-cache --virtual .build-deps $PHPIZE_DEPS \
	&& pecl install xdebug && docker-php-ext-enable xdebug \
	&& apk del -f .build-deps

CMD ["php-fpm"]
