FROM php:8.2-fpm

# Встановлення залежностей
RUN apt-get update && apt-get install -y \
    libonig-dev \
    libxml2-dev \
    zip unzip git curl libzip-dev \
    && docker-php-ext-install pdo_mysql zip

# Composer
COPY --from=composer:latest /usr/bin/composer /usr/bin/composer

# Копіюємо код
WORKDIR /var/www
COPY . .

RUN composer install

# Права
RUN chown -R www-data:www-data /var/www

EXPOSE 80
CMD ["php-fpm"]
