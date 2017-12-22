FROM debian:stretch-slim

MAINTAINER Falk Gebauer <fgebauer@3pc.de>

# supress debconf warnings in build scope
ARG TERM=linux
ARG DEBIAN_FRONTEND=noninteractive

ENV PHP_INI_DIR=/etc/php/7.0
ENV TZ=Europe/Berlin

# Install PHP from deb.sury.org
RUN apt update && apt dist-upgrade -y && \
    apt install -y wget curl apt-transport-https ca-certificates && \
    wget -O /etc/apt/trusted.gpg.d/php.gpg https://packages.sury.org/php/apt.gpg && \
    echo "deb https://packages.sury.org/php/ stretch main" > /etc/apt/sources.list.d/php.list && \
    apt update && apt dist-upgrade -y && \
    apt install -y --no-install-recommends \
        ssmtp \
        graphicsmagick \
        php7.0-fpm \
        php7.0-bcmath \
        php7.0-cli \
        php7.0-common \
        php7.0-curl \
        php7.0-gd \
        php7.0-json \
        php7.0-mbstring \
        php7.0-mysqli \
        php7.0-zip \
        php7.0-soap \
        php7.0-xml \
        php-apcu && \
    ln -s ${PHP_INI_DIR}/mods-available/custom.ini ${PHP_INI_DIR}/cli/conf.d/999-custom.ini && \
    ln -s ${PHP_INI_DIR}/mods-available/custom.ini ${PHP_INI_DIR}/fpm/conf.d/999-custom.ini && \
    rm ${PHP_INI_DIR}/fpm/pool.d/www.conf && \
    apt-get clean -y && \
    apt-get autoclean -y && \
    apt-get remove -y wget && \
    apt-get autoremove -y && \
    rm -rf /var/lib/apt/lists/* /var/lib/log/* /tmp/* /var/tmp/*

ADD conf.d/custom.ini ${PHP_INI_DIR}/mods-available/custom.ini
ADD fpm/php-fpm.conf ${PHP_INI_DIR}/fpm/php-fpm.conf

WORKDIR /var/www
EXPOSE 9000
CMD ["php-fpm7.0"]