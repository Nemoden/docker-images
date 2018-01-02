FROM php:7.1-fpm-alpine

RUN apk --update add build-base \
    pcre-dev \
    libjpeg-turbo-dev \
    zlib-dev \
    libpng-dev \
    libmcrypt-dev \
    freetype-dev \
    libmemcached-dev \
    cyrus-sasl-dev \
    imagemagick-dev \
    libtool \
    autoconf \
    && docker-php-ext-configure gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/ \
    && docker-php-ext-install iconv mcrypt pdo pdo_mysql gd opcache \
    && pecl install igbinary-2.0.5 \
    && docker-php-ext-enable igbinary \
    && echo yes | pecl install memcached-3.0.4 \
    && echo yes | pecl install redis-3.1.5 \
    && echo yes | pecl install imagick-3.4.3 \
    && docker-php-ext-enable memcached redis imagick
