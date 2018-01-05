FROM php:7.1.1-fpm

MAINTAINER Jakub Cegiełka <kuba.ceg@gmail.com>


RUN apt-get update 
RUN apt-get install -y \
        libfreetype6-dev \
        libjpeg62-turbo-dev \
        libmcrypt-dev \
        libpng12-dev \
    libxml2-dev libgmp-dev\
        php-pear wget curl git zlib1g-dev libncurses5-dev openssl libssl-dev libcurl4-openssl-dev libicu-dev libuv-dev cmake g++\
    && docker-php-ext-install iconv mcrypt \
    && docker-php-ext-configure gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/ --with-png-dir=/usr/include/\
    && docker-php-ext-configure intl \
&& docker-php-ext-install gd intl

RUN docker-php-ext-install sysvmsg sysvsem sysvshm && \
    docker-php-ext-install opcache phar posix && \
    docker-php-ext-install mbstring gettext calendar && \
docker-php-ext-install pdo pdo_mysql bcmath json zip curl

RUN pecl install xdebug
RUN docker-php-ext-enable xdebug

RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer
RUN echo "xdebug.remote_enable=on" >> /usr/local/etc/php/conf.d/docker-php-ext-xdebug.ini \
    && echo "xdebug.remote_autostart=on" >> /usr/local/etc/php/conf.d/docker-php-ext-xdebug.ini \
    && echo "xdebug.remote_port=10000" >> /usr/local/etc/php/conf.d/docker-php-ext-xdebug.ini \
    && echo "xdebug.remote_handler=dbgp" >> /usr/local/etc/php/conf.d/docker-php-ext-xdebug.ini \
    && echo "xdebug.remote_connect_back=off" >> /usr/local/etc/php/conf.d/docker-php-ext-xdebug.ini

CMD ["php-fpm", "-F"]

WORKDIR /var/www/symfony

RUN chown -R www-data:www-data /var/www/

EXPOSE 9000