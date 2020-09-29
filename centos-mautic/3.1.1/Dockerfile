FROM perlur/centos-nginx-php-fpm

LABEL maintainer="Mark Stopka <mark.stopka@perlur.cloud>"

ENV SERVICE_NAME "mautic"

ENV MAUTIC_VERSION "3.1.1"

RUN yum update -y
RUN yum install -y unzip \
    cronie-noanacron \
    php-json \
    php-pdo \
    php-intl \
    php-mysqlnd \
    php-xml \
    php-zip \
    php-process
RUN yum clean all && \
    dnf clean all && \
    rm -rf /var/cache/yum && \
    rm -rf /var/cache/dnf

WORKDIR /var/www/default/html

RUN curl -L --proto '=https' --tlsv1.2 -sSf -O https://github.com/mautic/mautic/releases/download/${MAUTIC_VERSION}/${MAUTIC_VERSION}.zip
RUN unzip -q ${MAUTIC_VERSION}.zip && rm ${MAUTIC_VERSION}.zip
RUN chown -R nginx.nginx /var/www/default/html
