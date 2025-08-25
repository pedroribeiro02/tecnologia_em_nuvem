# Usa a imagem oficial do PHP com Apache
FROM php:8.2-apache

# Porta usada pela Render
ENV PORT=8080

# Ativa o mod_rewrite para URLs amigáveis
RUN a2enmod rewrite

# Copia o código da aplicação
COPY . /var/www/html/

# Corrige permissões
RUN chown -R www-data:www-data /var/wwww/html && chmod -R 755 /var/wwww/html
