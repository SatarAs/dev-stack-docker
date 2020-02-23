FROM php:7.3-fpm

RUN apt update

RUN apt install -y -qq \
    zip curl wget \
    libxml2-dev \
    libmcrypt-dev \
    libssl-dev \
    libicu-dev \
    libxslt-dev \
    libfreetype6-dev \
    libjpeg62-turbo-dev \
    libpng-dev \
    libzip-dev \
    wkhtmltopdf \
    gnupg

RUN docker-php-ext-install gettext zip xsl pdo pdo_mysql mysqli intl hash

RUN curl --insecure https://getcomposer.org/composer.phar -o /usr/bin/composer && chmod +x /usr/bin/composer

RUN curl -sS https://dl.yarnpkg.com/debian/pubkey.gpg | apt-key add -
RUN echo "deb https://dl.yarnpkg.com/debian/ stable main" | tee /etc/apt/sources.list.d/yarn.list

RUN apt update && apt install -y -qq yarn

RUN rm /etc/localtime
RUN ln -s /usr/share/zoneinfo/Europe/Paris /etc/localtime
RUN "date"

COPY php.ini /usr/local/etc/php/

RUN usermod -u 1000 www-data

WORKDIR /var/www/symfony