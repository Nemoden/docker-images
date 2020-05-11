FROM php:7.4-fpm-alpine

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
    libsodium-dev \
    autoconf \
    && docker-php-ext-configure gd --with-freetype=/usr/include/ --with-jpeg=/usr/include/ \
    && docker-php-ext-install iconv mysqli pdo pdo_mysql gd opcache \
    && echo yes | pecl install igbinary-3.1.2 \
    && echo yes | pecl install memcached-3.1.5 \
    && echo yes | pecl install redis-5.2.1 \
    && echo yes | pecl install imagick-3.4.4 \
    && echo yes | pecl install libsodium-2.0.22 \
    && docker-php-ext-enable memcached redis imagick sodium igbinary

LABEL maintainer="Kirill Kovalchuk <i@nemoden.com>" \
  org.label-schema.docker.dockerfile="/Dockerfile" \
  org.label-schema.license="MIT" \
  org.label-schema.name="php-fpm with mysqli, pdo_mysql, redis, memcached, iconv, imagick, gd, igbinary, iconv and opcache" \
  org.label-schema.vcs-type="Git" \
  org.label-schema.vcs-url="https://github.com/Nemoden/docker-images"
