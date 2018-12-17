# Backend Image - https://hub.docker.com/_/php/
FROM php:7.2-apache

# Imagick
# PECL - https://github.com/docker-library/docs/tree/master/php#pecl-extensions
# Imagick version - https://pecl.php.net/package/imagick
RUN apt-get update && apt-get install -y libmagickwand-dev
RUN pecl install imagick-3.4.3 \
	&& docker-php-ext-enable imagick \
  && rm -r /var/lib/apt/lists/*

# Addid to php.ini config file
RUN mv "$PHP_INI_DIR/php.ini-production" "$PHP_INI_DIR/php.ini"
RUN echo "extension=php_imagick.dll" >> "$PHP_INI_DIR/php.ini"
RUN cat "$PHP_INI_DIR/php.ini" | grep imagick