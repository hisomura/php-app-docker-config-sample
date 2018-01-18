FROM php:5.6-apache
RUN docker-php-ext-install pdo_mysql
RUN yes | pecl install xdebug \
        && echo "zend_extension=$(find /usr/local/lib/php/extensions/ -name xdebug.so)" > /usr/local/etc/php/conf.d/xdebug.ini \
        && echo "xdebug.remote_enable=on" >> /usr/local/etc/php/conf.d/xdebug.ini \
        && echo "xdebug.remote_autostart=off" >> /usr/local/etc/php/conf.d/xdebug.ini \
        && echo "xdebug.remote_host=docker.for.win.localhost" >> /usr/local/etc/php/conf.d/xdebug.ini \
        && echo "xdebug.connect_back=off" >> /usr/local/etc/php/conf.d/xdebug.ini \
        && echo "xdebug.idekey=IDEA" >> /usr/local/etc/php/conf.d/xdebug.ini
RUN sed -ri -e 's!/var/www/html!${APACHE_DOCUMENT_ROOT}!g' /etc/apache2/sites-available/*.conf
RUN a2enmod rewrite
