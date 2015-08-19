FROM php:5.6-apache

RUN a2enmod rewrite
RUN apt-get update
RUN rm /etc/apache2/mods-available/php5.load # avoid replace file when installing libapache2-mod-php5
RUN apt-get -qq install libapache2-mod-php5 -y
RUN apt-get -qq install drush
RUN apt-get -qq install php5-mysql
RUN apt-get -qq install php5-gd -y
RUN usermod -u 1000 www-data