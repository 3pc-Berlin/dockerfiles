FROM debian:stretch-slim

MAINTAINER Falk Gebauer <fgebauer@3pc.de>

# supress debconf warnings in build scope
ARG TERM=linux
ARG DEBIAN_FRONTEND=noninteractive

ENV PHP_INI_DIR=/etc/php/7.0
ENV TZ=Europe/Berlin

# Install PHP from deb.sury.org
RUN apt update && apt dist-upgrade -y && \
    apt install -y wget cron apt-transport-https ca-certificates curl gnupg2 software-properties-common && \
    curl -fsSL https://download.docker.com/linux/$(. /etc/os-release; echo "$ID")/gpg | apt-key add - && \
    add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/$(. /etc/os-release; echo "$ID") $(lsb_release -cs)  stable"  && \
    apt update && \
    apt install -y docker-ce && \
    apt clean -y && \
    apt autoclean -y && \
    apt remove -y wget && \
    apt autoremove -y && \
    rm -rf /var/lib/apt/lists/* /var/lib/log/* /tmp/* /var/tmp/*

COPY entrypoint.sh /entrypoint.sh
RUN chmod +x /entrypoint.sh
ENTRYPOINT ["/entrypoint.sh"]