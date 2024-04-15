FROM php:8.3-fpm
WORKDIR /opt/work/php
WORKDIR /home/www

RUN mkdir /usr/lib/php && ln -s /usr/local/lib/php/extensions/no-debug-non-zts-20230831 /usr/lib/php/20230831

RUN apt update
RUN apt install ca-certificates apt-transport-https software-properties-common lsb-release -y
RUN curl -sSL https://packages.sury.org/php/README.txt | bash -x
#RUN apt update
RUN apt install -y php8.3-common/bookworm php8.3-mysql/bookworm php8.3-gmp/bookworm php8.3-gd/bookworm
RUN pecl install xdebug

CMD ["php-fpm"]
