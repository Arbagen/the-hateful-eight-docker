FROM php:5.6-fpm
RUN apt-get update && apt-get install -y git mc gnupg
RUN docker-php-ext-install opcache
RUN docker-php-ext-install pdo_mysql
COPY ./config/php.ini /usr/local/etc/php/php.ini
# Install Composer and make it available in the PATH
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/bin/ --filename=composer
#xdebug
ARG INSTALL_XDEBUG=false
RUN if [ ${INSTALL_XDEBUG} = true ]; then \
    pecl install xdebug-2.5.5 && docker-php-ext-enable xdebug && \
    echo "\n xdebug.remote_host=dockerhost \n xdebug.remote_enable = 1 \n xdebug.remote_port = 9000 \n xdebug.max_nesting_level = 500 \n xdebug.remote_autostart=1 \n xdebug.remote_connect_back=1" >> /usr/local/etc/php/php.ini \
;fi
