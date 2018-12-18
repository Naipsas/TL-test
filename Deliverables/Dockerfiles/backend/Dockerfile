# Backend Image - https://hub.docker.com/_/php/
FROM php:7.2-apache

# Imagick + Xdebug
# PECL - https://github.com/docker-library/docs/tree/master/php#pecl-extensions
# Imagick version - https://pecl.php.net/package/imagick
# Xdebug - https://xdebug.org/docs/install
RUN apt-get update && apt-get install -y libmagickwand-dev
RUN pecl install imagick-3.4.3 \
	&& pecl install xdebug \
	&& docker-php-ext-enable imagick \
  && rm -r /var/lib/apt/lists/*

# Addid to php.ini config file
RUN mv "$PHP_INI_DIR/php.ini-production" "$PHP_INI_DIR/php.ini"
RUN echo "extension=php_imagick.dll" >> "$PHP_INI_DIR/php.ini"
RUN echo 'zend_extension="/usr/local/lib/php/extensions/no-debug-non-zts-20170718/xdebug.so"' >> "$PHP_INI_DIR/php.ini"

# Restart apache to use Xdebug
RUN apachectl -k graceful