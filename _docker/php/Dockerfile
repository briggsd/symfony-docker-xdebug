FROM php:7.2-apache

ADD ./php.ini /usr/local/etc/php/conf.d

RUN apt-get update \
  && apt-get upgrade -y openssl \
  && apt-get install -y libcurl4-gnutls-dev libmcrypt-dev libxml2-dev \
  && docker-php-ext-install pdo_mysql \
  && docker-php-ext-install mysqli \
  && docker-php-ext-install sockets \
  && docker-php-ext-install soap \
  && a2enmod rewrite \
  && a2enmod headers \
  && pecl install xdebug-2.6.1

# -------------------------------
ENV XDEBUGINI_PATH=/usr/local/etc/php/conf.d/xdebug.ini

COPY xdebug.ini /tmp/xdebug.ini

RUN echo "zend_extension="`find /usr/local/lib/php/extensions/ -iname 'xdebug.so'` > $XDEBUGINI_PATH \
    && cat /tmp/xdebug.ini >> $XDEBUGINI_PATH \
    && echo "xdebug.remote_host=docker.for.win.host.internal" >> $XDEBUGINI_PATH

RUN php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');" \
    && php composer-setup.php --install-dir=/usr/local/bin --filename=composer \
    && rm composer-setup.php
