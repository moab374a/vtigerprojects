ARG APACHE_VERSION="2.4.32"
FROM httpd:${APACHE_VERSION:+${APACHE_VERSION}-}alpine

RUN apk update; \
    apk upgrade;

# Copy apache vhost file to proxy php requests to php-fpm container
RUN mkdir -p /usr/local/apache2/conf;
ADD vtiger6.apache.conf /usr/local/apache2/conf/vtiger6.apache.conf 
# Copy ssl files to proxy php requests to php-fpm container

RUN echo "Include /usr/local/apache2/conf/vtiger6.apache.conf" \
    >> /usr/local/apache2/conf/httpd.conf;


# ADD https://github.com/glpi-project/glpi/releases/download/9.5.5/glpi-9.5.5.tgz /var/www/html/glpi-9.5.5.tgz
# RUN mkdir -p /var/www/html/glpi;
# RUN cd /var/www/html && tar xvfz glpi-9.5.5.tgz;
# RUN chown -R www-data /var/www/html/glpi && \
#     chgrp -R www-data /var/www/html/glpi && \
#     chmod -R 0755 /var/www/html/glpi;

VOLUME /var/www/html

    
# RUN cd /var/www/html && \
#    wget --no-check-certificate https://github.com/glpi-project/glpi/releases/download/9.5.5/glpi-9.5.5.tgz && \
#    tar xvfz glpi-9.5.5.tgz && \
#    mkdir /etc/glpi && \
#    cp -R glpi/config /etc/glpi/ && \
#    cp  -R glpi/files /var/lib/glpi/ && \
#    chown -R www-data /var/www/html/glpi && \
#    chgrp -R www-data /var/www/html/glpi && \
#    chmod -R 0755 /var/www/html/glpi;
