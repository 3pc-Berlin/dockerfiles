FROM debian:stretch-slim

MAINTAINER Falk Gebauer <fgebauer@3pc.de>

# supress debconf warnings in build scope
ARG TERM=linux
ARG DEBIAN_FRONTEND=noninteractive

ENV PHP_INI_DIR=/etc/php/5.6
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
        php5.6-fpm \
        php5.6-bcmath \
        php5.6-cli \
        php5.6-common \
        php5.6-curl \
        php5.6-gd \
        php5.6-json \
        php5.6-mbstring \
        php5.6-mysqli \
        php5.6-zip \
        php5.6-soap \
        php5.6-xml \
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
CMD ["php-fpm5.6"]