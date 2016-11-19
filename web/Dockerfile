FROM php:7-apache

COPY config/php.ini /usr/local/etc/php/
RUN a2enmod rewrite
RUN apt-get update
RUN apt-get -qq install \
		libapache2-mod-php5 \
		libjpeg62-turbo-dev \
		libpng12-dev \
		libfreetype6-dev
RUN docker-php-ext-configure gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/ \
    && docker-php-ext-install gd \
    && docker-php-ext-install pdo_mysql \
    && docker-php-ext-install mysqli \
    && docker-php-ext-install zip \
    && docker-php-ext-install pcntl \
    && docker-php-ext-install opcache \
    && docker-php-ext-install mbstring
RUN usermod -u 1000 www-data

RUN curl -sS https://getcomposer.org/installer | php
RUN mv composer.phar /usr/local/bin/composer

WORKDIR /var/www/html/
RUN composer require drupal/console:1.0.0-alpha2 --prefer-dist --optimize-autoloader --sort-packages
RUN composer install
ENV PATH "$PATH:/var/www/html/vendor/bin"
