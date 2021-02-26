FROM php:8.0-fpm-alpine

RUN apk update \
    && apk add  --no-cache git yarn zip mysql-client libzip-dev curl libmcrypt libmcrypt-dev openssh-client icu-dev \
    libxml2-dev freetype-dev libpng-dev libjpeg-turbo-dev g++ make autoconf postgresql-dev \
    && curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer \
    && docker-php-source extract \
    && pecl install xdebug \
    && docker-php-ext-enable xdebug \
    && docker-php-source delete \
    && docker-php-ext-install opcache pdo_mysql soap intl zip pdo_pgsql

CMD ["php-fpm", "-F"]

RUN apk add --update bash nodejs npm

WORKDIR /var/www/app
