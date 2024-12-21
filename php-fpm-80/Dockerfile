# 基本 Image (指定容器的作業系統)
FROM php:8.0.30-fpm

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
            libmemcached-dev \
            libcurl4-openssl-dev \
            libz-dev \
            libpq-dev \
            libjpeg-dev \
            libpng-dev \
            libfreetype6-dev \
            libssl-dev \
            libwebp-dev \
            libmcrypt-dev \
            libicu-dev \
            libzip-dev \
            libonig-dev; \
    rm -rf /var/lib/apt/lists/*

# Composer
RUN curl -sS https://getcomposer.org/installer | php \
    && mv composer.phar /usr/local/bin/composer;

# bcmath
RUN docker-php-ext-install bcmath;

# gd
RUN set -eux; \
    docker-php-ext-configure gd \
            --prefix=/usr \
            --with-jpeg \
            --with-webp \
            --with-freetype; \
    docker-php-ext-install gd;

# intl
RUN apt-get install -y zlib1g-dev g++ && \
    docker-php-ext-configure intl && \
    docker-php-ext-install intl;

# mysqli
RUN docker-php-ext-install mysqli;

# pdo_mysql
RUN docker-php-ext-install pdo_mysql;

# pdo_pgsql
RUN docker-php-ext-install pdo_pgsql;

# redis
RUN pecl install -o -f redis; \
    rm -rf /tmp/pear; \
    docker-php-ext-enable redis;

# swoole
RUN pecl install swoole-5.0.1; \
    docker-php-ext-enable swoole;

# Zend OPcache
RUN docker-php-ext-install opcache;

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
