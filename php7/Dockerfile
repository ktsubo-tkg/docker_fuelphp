FROM php:7-fpm
LABEL maintainer "tk-gengineer <ktsubo@tk-gengineer.com>"

RUN apt-get update && apt-get install -y libmcrypt-dev mysql-client 
RUN docker-php-ext-install pdo_mysql 
RUN apt-get install -y zip unzip 
RUN apt-get install -y vim curl

# SSL関連
RUN apt-get install libssl-dev \
  openssl \
  ssl-cert \
  && apt-get clean \
  && rm -rf /var/lib/apt/lists/* \
  && a2enmod ssl \
  && a2ensite default-ssl

#composer
RUN curl -sS https://getcomposer.org/installer | php && \
    mv composer.phar /usr/local/bin/composer && \
    chmod 777 /usr/local/bin/composer

RUN cd /var/www && \
    curl https://get.fuelphp.com/oil | sh

WORKDIR /var/www
