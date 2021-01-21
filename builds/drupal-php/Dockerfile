FROM php:8.0.1-fpm-alpine
# root -> /var/www/html

COPY ./archives/drupal-9.1.2.zip .

RUN apk add --no-cache unzip && \
    unzip -q drupal-9.1.2.zip && \
    mv drupal-9.1.2/* /var/www/html/ && \
    chown -R www-data:www-data /var/www/html/* && \
    rm -rf drupal-9.1.2.zip drupal-9.1.2

RUN apk update && \
    apk upgrade && \
    apk add --no-cache libpng-dev postgresql-dev && \
    docker-php-ext-configure gd && \
    docker-php-ext-install gd opcache pgsql pdo_pgsql

RUN mkdir /var/www/html/sites/default/files && \
    chown www-data:www-data /var/www/html/sites/default/files && \
    chmod -R 777 /var/www/html/sites/default/files
#    && \
#    cp /var/www/html/sites/default/default.settings.php /var/www/html/sites/default/settings.php && \
#    chmod 777 /var/www/html/sites/default/settings.php && \
#    chown www-data:www-data /var/www/html/sites/default/settings.php

COPY ./files/settings.php /var/www/html/sites/default/settings.php
RUN chmod 644 /var/www/html/sites/default/settings.php && \
    chown www-data:www-data /var/www/html/sites/default/settings.php