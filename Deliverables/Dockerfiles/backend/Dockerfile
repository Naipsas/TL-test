# Backend Image - https://hub.docker.com/_/php/
FROM php:7.2-apache

# Extension installation
# PECL - https://github.com/docker-library/docs/tree/master/php#pecl-extensions
# Imagick version - https://pecl.php.net/package/imagick
RUN pecl install imagick-3.4.3 \
	&& docker-php-ext-enable imagick