FROM php:7.3-fpm
COPY php.ini /usr/local/etc/php/
COPY docker.conf /usr/local/etc/php-fpm.d/docker.conf

RUN apt-get update \
  && apt-get install -y zlib1g-dev default-mysql-client curl gnupg procps wget tzdata \
    libzip-dev \
    unzip \
    git \
    ssh \
    libssh2-1 \
    libssh2-1-dev \
    libssl-dev \
    sqlite3 \
    tree \
  && docker-php-ext-install zip pdo_mysql

RUN cp /usr/share/zoneinfo/Asia/Tokyo /etc/localtime

RUN curl -sL https://deb.nodesource.com/setup_12.x | bash -
RUN apt-get install -y nodejs
RUN npm install npm@latest -g

#Composer install
RUN php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');"
RUN php composer-setup.php
RUN php -r "unlink('composer-setup.php');"
RUN mv composer.phar /usr/local/bin/composer

ENV COMPOSER_ALLOW_SUPERUSER 1

ENV COMPOSER_HOME /composer

ENV PATH $PATH:/composer/vendor/bin


WORKDIR /var/www

RUN composer global require "laravel/installer"
