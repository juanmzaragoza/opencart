FROM php:5.6.30-fpm
RUN apt-get update
RUN apt-get install -y libmcrypt-dev 
RUN apt-get install -y libpq-dev
RUN apt-get install -y git
RUN apt-get install -y zip unzip
RUN apt-get install -y libpng*
RUN apt-get install -y nano
RUN apt-get install -y libssh2-1-dev libssh2-php
RUN apt-get install -y libjpeg-dev
RUN apt-get install -y libfreetype6-dev

RUN docker-php-ext-configure gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/
RUN docker-php-ext-install gd pdo_mysql pdo_pgsql zip
RUN curl -sS https://getcomposer.org/installer | php \
    && mv composer.phar /usr/local/bin/composer.phar



RUN echo  'date.timezone = "America/Argentina/Buenos_Aires"' >> /usr/local/etc/php/php.ini

RUN  apt-get install -y libmemcached-dev zlib1g-dev \
    && pecl install memcached-2.2.0 \
    && docker-php-ext-enable memcached


RUN pecl install mongo
RUN docker-php-ext-enable mongo
RUN pecl install -f  ssh2
RUN docker-php-ext-enable ssh2	



#permisologias y directorio para tarjetas
#RUN mkdir /var/lib/php/
#RUN mkdir /var/lib/php/session
#RUN chmod 777 -R /var/lib/
##fin permisologias para tarjetas

RUN eval $(ssh-agent -s)

#RUN ssh-add /.ssh/id_rsa