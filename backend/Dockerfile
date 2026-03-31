FROM php:8.4-fpm-alpine

# Extensions système nécessaires
RUN apk add --no-cache \
    git \
    curl \
    libpng-dev \
    libxml2-dev \
    zip \
    unzip \
    sqlite-dev

# Extensions PHP
RUN docker-php-ext-install \
    pdo \
    pdo_sqlite \
    opcache

# Installer pdo_pgsql (PostgreSQL)
RUN apk add --no-cache postgresql-dev \
    && docker-php-ext-install pdo_pgsql

# Installer Composer
COPY --from=composer:2 /usr/bin/composer /usr/bin/composer

WORKDIR /var/www/backend

# Copier et installer les dépendances
COPY composer.json composer.lock ./
RUN composer install --no-scripts --no-autoloader --prefer-dist

# Copier le reste du projet
COPY . .

RUN composer dump-autoload --optimize \
    && mkdir -p var/cache var/log \
    && chmod -R 777 var/

EXPOSE 8000

CMD ["php", "-S", "0.0.0.0:8000", "-t", "public"]
