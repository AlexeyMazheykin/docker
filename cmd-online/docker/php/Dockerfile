FROM php:8.4-apache
RUN apt-get update && apt-get install -y msmtp && rm -rf /var/lib/apt/lists/*
RUN echo 'sendmail_path = "/usr/bin/msmtp -t --read-envelope-from --host=host.docker.internal --port=1025"' > /usr/local/etc/php/conf.d/mail.ini
RUN apt-get update \
    && apt-get install -y --no-install-recommends \
        libfreetype6-dev libicu-dev libjpeg62-turbo-dev \
        libonig-dev libpng-dev libwebp-dev libzip-dev unzip \
        libmagickwand-dev \
    && docker-php-ext-configure gd --with-freetype --with-jpeg --with-webp \
    && docker-php-ext-install -j"$(nproc)" bcmath gd intl mbstring mysqli opcache pdo_mysql zip \
    && a2enmod expires headers rewrite \
    && pecl install xdebug imagick \
    && docker-php-ext-enable xdebug imagick \
    && rm -rf /var/lib/apt/lists/*
COPY docker/php/php.ini /usr/local/etc/php/conf.d/99-local.ini
COPY docker/php/xdebug.ini /usr/local/etc/php/conf.d/zz-xdebug.ini