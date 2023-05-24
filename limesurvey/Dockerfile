# Use PHP 8.0 with Apach as a base image
FROM php:8.1-apache

# Install necessary packages
RUN apt-get update && apt-get upgrade -y \
    && apt-get install -y libzip-dev zip unzip php-imap  php-ldap php-gd \
    phpenmod imap

# Install PHP extensions
RUN docker-php-ext-install mysqli pdo pdo_mysql zip \
    && docker-php-ext-enable mysqli

# Copy LimeSurvey directory and config file
COPY ./limesurvey /var/www/html/limesurvey
COPY ./limesurvey.conf /etc/apache2/sites-available/

# Set proper permissions and enable site
RUN chown -R www-data:www-data /var/www/html/limesurvey && \
    chmod -R 755 /var/www/html/limesurvey && \
    a2ensite limesurvey && \
    a2dissite 000-default.conf && \
    a2enmod rewrite && \
    service apache2 restart

EXPOSE 80
