
FROM ubuntu:latest
# Add configuration file
COPY . .

RUN mv limesurvey/* /var/www/html && \ 
    mv limesurvey.conf /etc/apache2/sites-available && \
    chown www-data:www-data -R /var/www/html/limesurvey/ && \
    chmod 755 -R /var/www/html/limesurvey/ && \
    a2ensite limesurvey && \
    a2dissite 000-default.conf && \
    a2enmod rewrite && \
    systemctl reload apache2

EXPOSE 8080

 
