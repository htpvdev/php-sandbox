FROM php:8.0-fpm-buster
SHELL ["/bin/bash", "-oeux", "pipefail", "-c"]

ENV COMPOSER_ALLOW_SUPERUSER=1 \
  COMPOSER_HOME=/composer

# composerのバージョン2系をインストール
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/bin --filename=composer --version=2.1.6

# composerをコピー
COPY --from=composer /usr/bin/composer /usr/bin/composer

RUN \
  apt-get update && \
  apt-get -y install git unzip libzip-dev libicu-dev libonig-dev libfreetype6-dev libjpeg62-turbo-dev libpng-dev && \
  apt-get clean && \
  rm -rf /var/lib/apt/lists/* && \
  docker-php-ext-install intl zip bcmath opcache && \
  pecl install xdebug-3.1.0 \
  && docker-php-ext-enable xdebug \
  && docker-php-ext-configure gd --with-freetype --with-jpeg \
  && docker-php-ext-install -j$(nproc) gd exif

COPY ./php.ini /usr/local/etc/php/php.ini

WORKDIR /work

#RUN chmod 777 -R storage
