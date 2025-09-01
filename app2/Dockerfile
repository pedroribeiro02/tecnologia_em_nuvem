# Usa a imagem oficial do PHP com Apache
FROM php:8.2-apache

# Porta usada pela Render
ENV PORT=8080

# Ativa o mod_rewrite para URLs AMIGÁVEIS
RUN a2enmod rewrite

# Copia o código da aplicação para o diretório do Apache
COPY . /var/www/html/

# Corrige permissões
RUN chown -R www-data:www-data /var/www/html && chmod -R 755 /var/www/html

# Corrige a configuração da porta
RUN sed -i "s/Listen 80/Listen ${PORT}/" /etc/apache2/ports.conf && \
    sed -i "s/<VirtualHost \*:80>/<VirtualHost \*:${PORT}>/" /etc/apache2/sites-available/000-default.conf

# Permite o acesso ao diretório /var/www/html e ativa o mod_rewrite
RUN echo '<Directory /var/www/html>' >> /etc/apache2/apache2.conf && \
    echo '    Options Indexes FollowSymLinks' >> /etc/apache2/apache2.conf && \
    echo '    AllowOverride All' >> /etc/apache2/apache2.conf && \
    echo '    Require all granted' >> /etc/apache2/apache2.conf && \
    echo '</Directory>' >> /etc/apache2/apache2.conf

# Expõe a porta corretamente
EXPOSE ${PORT}

# Inicia o Apache em primeiro plano
CMD ["apache2-foreground"]
