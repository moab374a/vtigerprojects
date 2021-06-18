ARG PHP_VERSION="7.4"
FROM php:${PHP_VERSION:+${PHP_VERSION}-}fpm-alpine

RUN apk update; \
    apk upgrade;

# Add support for PHP7.4.
# RUN apk add --no-cache --repository http://dl-cdn.alpinelinux.org/alpine/edge/community 
    

#RUN apk add --no-cache --repository http://dl-cdn.alpinelinux.org/alpine/edge/community libxml2-dev \
# bzip2-dev curl-dev enchant2-dev enchant2 libexif-dev libpng-dev libgmpxx gmp-dev \
# libevent-dev libpthread-stubs boost-thread fftw-long-double-libs musl-utils gnu-libiconv-dev xxhash-dev \
# rhash-dev rhash-libs gettext-dev libpq libzip-dev libedit-dev libsodium-dev php7-cli php7-intl php7-pecl-apcu php7-fpm icu-dev icu-libs icu-data openldap-dev \
# oniguruma-dev freetds-dev argon2-dev argon2-libs php-pear readline-dev sqlite-dev sqlite-libs php7-soap php7-sockets \
# php7-simplexml php7-session php7-xml php7-xsl php7-xmlrpc php7-posix php7-phar php7-sysvshm php7-sysvmsg \
# php7-sysvsem php7-shmop php7-tidy php7-zip php7-pdo php7-pdo_dblib php7-pdo_mysql php7-pdo_pgsql \
# php7-pdo_sqlite php7-pgsql php7-pspell php7-pecl-apcu php7-sqlite3 php7-pecl-uuid php7-pecl-redis php7-pecl-amqp \
# php7-pecl-yaml php7-pecl-memcache php7-pecl-psr php7-pecl-mongodb php7-iconv php7-imap php7-pecl-igbinary \
# php7-pecl-memcached php7-brotli php7-pecl-xhprof unit-php7 php7-common

#RUN docker-php-ext-install bcmath bz2 calendar curl dom exif fileinfo gd \
#    intl json ldap mbstring mysqli opcache pcntl xmlrpc zip\
#    readline sodium tokenizer



WORKDIR /var/www/html

ADD https://sourceforge.net/projects/vtigercrm/files/vtiger%20CRM%207.2.0/Core%20Product/vtigercrm7.2.0.tar.gz/download /var/www/html/vtigercrm7.2.0.tar.gz
#ADD https://sourceforge.net/projects/vtigercrm/files/vtiger%20CRM%206.5.0/Core%20Product/vtigercrm6.5.0.tar.gz/download /var/www/html/vtigercrm6.5.0.tar.gz
CMD cd /var/www/html
RUN tar xvfz vtigercrm7.2.0.tar.gz
#CMD cp -R /var/www/glpi/config/ /etc/glpi/ && \
#    cp -R /var/www/glpi/files/ /var/lib/glpi/

#COPY --chown=www-data:www-data /var/www/glpi/config/.htaccess /etc/glpi/.htaccess

CMD /bin/sh

#CMD mkdir -p /var/lib/glpi;
#COPY --chown=www-data:www-data /var/www/glpi/files/ /var/lib/glpi/

#CMD chown -R www-data /var/www/glpi
#CMD chgrp -R www-data /var/www/glpi
#CMD chmod -R 0755 /var/www/glpi

#CMD cp index.php /var/www/html
#RUN ln -sf /var/www/html/glpi/index.php /var/www/html/index.php;

# VOLUME /var/www/glpi