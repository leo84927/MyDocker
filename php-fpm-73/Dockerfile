# php-7.3.33 (Debian)

# 基本 Image (指定容器的作業系統)
FROM php:7.3.33-fpm

# 維護者
MAINTAINER Leo

# 安裝所需的工具
RUN set -eux; \
    apt-get update; \
    apt-get -y upgrade; \
    apt-get -y --no-install-recommends install \
            git \
            curl \
            lsof \
            vim \
            g++ \
            gettext \
            imagemagick \
            libcurl4-openssl-dev \
            libmcrypt-dev \
            libmagickwand-dev \
            libmemcached-dev \
            libz-dev \
            libpq-dev \
            libjpeg-dev \
            libpng-dev \
            libfreetype6-dev \
            libssh2-1-dev \
            libssl-dev \
            libwebp-dev \
            libmcrypt-dev \
            libicu-dev \
            libzip-dev \
            libbz2-dev \
            zlib1g-dev \
            libxslt-dev \
            libonig-dev; \
    rm -rf /var/lib/apt/lists/*

# Composer
RUN curl -sS https://getcomposer.org/installer | php \
    && mv composer.phar /usr/local/bin/composer;

# bcmath
RUN docker-php-ext-install bcmath;

# bz2
RUN docker-php-ext-install bz2;

# calendar
RUN docker-php-ext-configure calendar && \
    docker-php-ext-install calendar;

# Exif
RUN docker-php-ext-install exif;

# gd
RUN set -eux; \
    docker-php-ext-configure gd \
            --with-jpeg-dir=/usr \
            --with-webp-dir=/usr \
            --with-freetype-dir=/usr; \
    docker-php-ext-install gd;

# gettext
RUN docker-php-ext-install gettext;

# igbinary
RUN pecl install igbinary \
    && rm -rf /tmp/pear \
    && docker-php-ext-enable igbinary;

# imagick
RUN pecl install imagick \
    && docker-php-ext-enable imagick;

# mcrypt
RUN pecl install mcrypt \
    && docker-php-ext-enable mcrypt;

# msgpack
RUN pecl install msgpack \
    && docker-php-ext-enable msgpack;

# mysqli
RUN docker-php-ext-install mysqli;

# pcntl
RUN docker-php-ext-install pcntl;

# pdo_mysql
RUN docker-php-ext-install pdo_mysql;

# redis
RUN pecl install -o -f redis; \
    rm -rf /tmp/pear; \
    docker-php-ext-enable redis;

# shmop
RUN docker-php-ext-install shmop;

# sockets
RUN docker-php-ext-install sockets;

# ssh2
RUN pecl install -a ssh2 \
    docker-php-ext-enable ssh2;

# swoole
RUN pecl install \
    --configureoptions 'enable-sockets="yes" enable-openssl="yes" enable-http2="yes" enable-swoole-json="yes" enable-swoole-curl="yes" enable-mysqlnd="yes"' \
    swoole-4.8.6; \
    docker-php-ext-enable swoole;

# sysvmsg
RUN docker-php-ext-install sysvmsg;

# sysvsem
RUN docker-php-ext-install sysvsem;

# sysvshm
RUN docker-php-ext-install sysvshm;

# wddx
RUN docker-php-ext-install wddx;

# xsl
RUN docker-php-ext-install xsl;

# zip
RUN docker-php-ext-install zip;

#
#--------------------------------------------------------------------------
# Final Touch
#--------------------------------------------------------------------------
#

# Clean up
RUN apt-get clean && \
    rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/* && \
    rm /var/log/lastlog /var/log/faillog

CMD ["php-fpm"]
