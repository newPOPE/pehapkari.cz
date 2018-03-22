FROM php:7.2
MAINTAINER adam.stipak@gmail.com

# system deps
RUN apt-get update && \
  apt-get install -y \
    git \
    gnupg \
    zlib1g-dev

# install nodejs
RUN curl -sL https://deb.nodesource.com/setup_8.x | bash - &&\
  apt-get install -y nodejs

RUN # php extensions
RUN docker-php-ext-install zip

# binaries
RUN curl https://getcomposer.org/composer.phar -o "/usr/local/bin/composer" && \
  chmod +x /usr/local/bin/composer

# gulp dependencies
RUN npm install -g \
  gulp \
  gulp-watch

WORKDIR /src
CMD composer install && \
  npm install && \
  gulp
