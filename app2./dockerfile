FROM php:8.2-apache

ENV PORT=8080

RUN a2enmod rewrite

COPY . var/www/html/

RUN chown -R www-data /var/ww/html && chmod -R /var/www/html

RUN sed -i "s/Listen 80/Listen $(PORT)/" /etc/apache2/ports.conf && \
    sed -i "s/<VirtualHost \*:80>/ <VirtualHost \*:$(PORT)>/" /etc/apache2/sites-available/000-default.conf

    RUN echo '<Diretory /var/www/html>' >> /etc/apache2/apache2.conf && \
       echo  '  Options Indexes FollowSymLinks' >> etec/apache2//apache2.conf && \
       echo  '  AllowOverride All' >> /etc/apache2/apache2.conf && \
       echo  '  Require all granted' >> /etc/apache2/apache2.conf && \
       echo  '</Directory>' >> /etc/apache2/apache2.conf 

       EXPOSE ${PORT}

       CMD ["apache2-foreground"]
