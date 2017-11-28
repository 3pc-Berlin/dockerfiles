FROM dreipc/php:7.1-fpm-typo3

MAINTAINER Falk Gebauer <fgebauer@3pc.de>

ENV XDEBUG_IDE_KEY=PHPSTORM \
    XDEBUG_REMOTE_PORT=9001 \
    XDEBUG_REMOTE_HANDLER=dbgp \
    XDEBUG_MAX_NESTING_LEVEL=400

# supress debconf warnings in build scope
ARG TERM=linux
ARG DEBIAN_FRONTEND=noninteractive

# Install PHP from deb.sury.org
RUN apt update && apt dist-upgrade -y && \
    apt install -y --no-install-recommends \
    php-xdebug && \
    apt-get clean -y && \
    apt-get autoclean -y && \
    apt-get remove -y wget curl && \
    apt-get autoremove -y && \
    rm -rf /var/lib/apt/lists/* /var/lib/log/* /tmp/* /var/tmp/*

CMD ["php-fpm7.1", "-d", "xdebug.remote_enable=1", "-d", "xdebug.remote_connect_back=1", "-d", "xdebug.remote_port=${XDEBUG_REMOTE_PORT}", "-d", "xdebug.remote_handler=${XDEBUG_REMOTE_HANDLER}", "-d", "xdebug.max_nesting_level=${XDEBUG_MAX_NESTING_LEVEL}"]