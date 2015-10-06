FROM php:5.6-apache

RUN a2enmod rewrite
RUN apt-get update
# avoid replace file when installing libapache2-mod-php5
RUN rm /etc/apache2/mods-available/php5.load 
RUN apt-get -qq install \
		libapache2-mod-php5 \
		libjpeg62-turbo-dev \
		libpng12-dev \
		libfreetype6-dev \
		php5-mysql \
		php5-gd \
		php5-dev \
		mysql-client
RUN docker-php-ext-configure gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/ \
    && docker-php-ext-install gd \
    && docker-php-ext-install pdo_mysql \
    && docker-php-ext-install mysqli \
    && docker-php-ext-install zip \
    && docker-php-ext-install pcntl \
    && docker-php-ext-install mbstring
RUN usermod -u 1000 www-data

WORKDIR /usr/local/lib/
RUN curl -sS https://getcomposer.org/installer | php
RUN mv composer.phar /usr/local/bin/composer

RUN apt-get -qq install git
RUN git clone --branch master https://github.com/drush-ops/drush.git
WORKDIR /usr/local/lib/drush
RUN composer install
RUN ln -s /usr/local/lib/drush/drush /usr/local/bin/drush

WORKDIR /var/www/html/

