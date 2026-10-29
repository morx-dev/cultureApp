FROM php:8.4-fpm

RUN apt-get update && apt-get install -y \
    git unzip libzip-dev libpng-dev libjpeg-dev libwebp-dev \
    libfreetype6-dev libonig-dev libicu-dev \
 && docker-php-ext-configure gd --with-jpeg --with-webp --with-freetype \
 && docker-php-ext-install pdo_mysql mbstring bcmath gd zip intl exif pcntl \
 && rm -rf /var/lib/apt/lists/*

COPY --from=composer:2 /usr/bin/composer /usr/bin/composer
COPY uploads.ini /usr/local/etc/php/conf.d/uploads.ini

WORKDIR /var/www/html
