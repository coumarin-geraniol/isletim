# Use PHP 8.0 with Apache as a base image
FROM php:8.0-apache

# Install necessary packages
RUN apt-get update && apt-get upgrade -y \
    && apt-get install -y libzip-dev zip unzip

# Install PHP extensions
RUN docker-php-ext-install mysqli pdo pdo_mysql zip \
    && docker-php-ext-enable mysqli

# Enable Apache mod_rewrite
RUN a2enmod rewrite

# Copy limesurvey into the docker container
COPY limesurvey /var/www/html/limesurvey

# Set the correct permissions
RUN chown -R www-data:www-data /var/www/html/limesurvey \
    && chmod -R 755 /var/www/html/limesurvey

# Expose port 80
EXPOSE 80