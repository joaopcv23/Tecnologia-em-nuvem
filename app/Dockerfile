# usa a imagem oficial do apache
FROM php:8.2-apache

# Porta usada pela render
  ENV PORT=8080

# ativa o mod_rewrite para URLS amigáveis
  RUN a2enmod rewrite

#Copia o código da aplicação
  COPY . /var/www/html/


# Corrige permissôes
  RUN chown -R www-data:www-data /var/www/html && chmod -R 755 /var/www/html

  RUN sed -i "s/listen 80/Listen ${PORT}/" /etec/apache2/ports.conf && \
  sed -i "s/<VirtualHost \*:80>/<VirtualHost \*${PORT}>/" /etc/apache2/sites-available/000-default.conf

  #Permite acesso ao diretório
  RUN echo '<Directory /var/www/html>' >> /etc/apache2/apache2.conf && \
  echo ' Options Indexes FollowSysLinks' >> /etc/apache2/apache2.conf && \
  echo ' Require all granted' >> /etc/apache2/apache2.conf && \
  echo '<Directory>' >> /etc/apache2/apache2.conf

  # Expõe a porta correta 
  EXPOSE ${PORT}

  #Inicia o Apache
  CMD ["apache2-foreground"]
