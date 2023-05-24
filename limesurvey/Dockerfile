# Use PHP 8.0 with Apache as a base image
FROM php:8.0-apache

# Install necessary packages
RUN apt-get update && apt-get upgrade -y \
    && apt-get install -y libzip-dev zip unzip

# Install PHP extensions
RUN docker-php-ext-install mysqli pdo pdo_mysql zip \
    && docker-php-ext-enable mysqli

COPY ./limesurvey.conf /etc/apache2/sites-available/

RUN mkdir -p /var/www/html/limesurvey && \
    chown -R www-data:www-data /var/www/html/limesurvey && \
    chmod -R 755 /var/www/html/limesurvey && \
    a2ensite limesurvey && \
    a2dissite 000-default.conf && \
    a2enmod rewrite && \
    service apache2 restart

EXPOSE 80
