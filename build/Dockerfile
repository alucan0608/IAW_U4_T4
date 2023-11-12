FROM php:7.4-apache
RUN apt-get update && apt-get install -y mariadb-client
RUN docker-php-ext-install mysqli && docker-php-ext-enable mysqli
COPY bookmedik/. /var/www/bookmedik
RUN chmod -R 755 /var/www/bookmedik &&  chown -R www-data:www-data /var/www/bookmedik
ENV APACHE_DOCUMENT_ROOT /var/www/bookmedik
RUN sed -ri -e "s!/var/www/html!${APACHE_DOCUMENT_ROOT}!" /etc/apache2/sites-available/000-default.conf
CMD service apache2 restart && /usr/local/bin/script.sh
EXPOSE 80
ENV DB_USER a
ENV DB_PASS a
ENV DB_NAME a
ENV DB_HOST a
ADD script.sh /usr/local/bin/script.sh
ADD bookmedik/schema.sql /opt
RUN chmod +x /usr/local/bin/script.sh
CMD ["/usr/local/bin/script.sh"]